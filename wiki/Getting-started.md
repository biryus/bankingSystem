BankSystem consists of two base components - the bank web application and the _CentralApi_, which securely connects banks running on separate machines together to process [[transfers between different banks|Money transfers#Global--worldwide-transfers]], [[card payments|Cards#Purchases]] and [[direct payments|Direct payments]].

***

## BankSystem.Web
The BankSystem.Web web application can be found in the Web directory in the solution.

>Note: If a connection to the _CentralApi_ cannot be established, a lot of functionality **will not work**. For example, [[global transfers|Money transfers#Global--worldwide-transfers]], [[card payments|Cards#Purchases]] and [[direct payments|Direct payments]] **require a connection**.

### Bank details
The bank details such as name, unique identifier, card prefix, and country can be found in the _Web/BankSystem.Web/appsettings.json_ file.

Example:
```
"BankConfiguration": {
  "BankName": "Bank system",
  "CentralApiAddress": "https://localhost:5001/",
  "Key": "<RSAKeyValue><Modulus>uBJG...",
  "UniqueIdentifier": "ABC",
  "First3CardDigits": "101",
  "Country": "Bulgaria", 
  "CentralApiPublicKey": "<RSAKeyValue><Modulus>v76m9..."
}
```

The CentralApiAddress, Key and CentralApiPublicKey options can be configured later after setting up the CentralApi.

### How to generate RSA key
Simply run the project in _RSAKeyGenerator/RSAGenerator_ directory.
 
### Automatically generated user

If there are no users in the database, the app will automatically create one for testing purposes. An account containing €10000 will also be generated. Its login details are listed below:

| Email                 | Password 
|-----------------	|----------
| test@test.com         | Test123$


### Administrator account
To be able to use the administrative functions of BankSystem, you have to create an administrator account by following these steps:

1. Make an account in the application (or use the default account above).
2. Connect to the SQL database using a tool such as SSMS or DataGrip.
3. From the *AspNetRoles* table, note the ID of the Administrator role.
4. From the *AspNetUsers* table, note the ID of your newly created user account.
5. Create a new row in the *AspNetUserRoles* table and insert the user and role ID.

***

## CentralApi
The CentralApi app can be found in the Web/Api/ solution directory. Its purpose is to route transactions and confirm the identity of the banks by verifying their keys and signatures. **It is necessary** for much of the functionality of the BankSystem.

### Configuration
To configure the CentralApi, please follow the steps below:
1. Run the CentralApi so that the database gets created.
2. Connect to the database and open the _Banks_ table.
3. Delete or modify the first row so that the details match the ones you have chosen when configuring the _BankSystem.Web_ app. The corresponding table columns and JSON keys are listed below:

|CentralApi database column      |BankSystem.Web appsettings.json key
|--------------------------------|--------------------------------------
|Name                            |BankName
|SwiftCode                       |UniqueIdentifier
|Location                        |Country
|BankIdentificationCardNumbers   |First3CardDigits

4. Change the URLs so that the banks can connect to the _CentralApi_ and vice versa
 * Change the domain and port of the ApiAddress, PaymentUrl and CardPaymentUrl in the _CentralApi_ database
 * Change the CentralApiAddress in the _appsettings.json_ of the _BankSystem.Web_ app _(it has to end with a slash - / )
5. Repeat steps 3 and 4 for every bank you want to add
6. Generate new keypairs for every bank _(the provided keys match and work, but should be replaced)_
 * Insert the **public key of the CentralApi** in the _appsettings.json_ of every bank
 * Insert the **private key of the CentralApi** in the _appsettings.json_ of the _CentralApi_ _(CentralApiConfiguration -> Key)_
 * Insert the **private key of every bank** in the _appsettings.json_ of that bank _(BankConfiguration -> Key)_
 * Insert the **public key of every bank** in the _ApiKey_ column of the corresponding row in the _CentralApi_ database
***

## External services

In order to register an account on the BankSystem.Web application, the following services must be configured. This is not necessary if you wish to use the automatically generated user.

#### ReCaptcha
The app uses ReCaptcha to protect the registration form against bots.

Please follow the steps below to configure ReCaptcha:
1. Register a [reCAPTCHA v2 Checkbox site](https://www.google.com/recaptcha/admin).
>Alternatively, you can use the testing ReCaptcha keys from [this page](https://developers.google.com/recaptcha/docs/faq), which do not, however, offer any protection.
2. Insert the Site key and Secret key in the following file:
    * *src/Web/BankSystem.Web/appsettings.json*

Example:
```
"ReCaptcha": {
  "SiteKey": "6L************************************FG",
  "SiteSecret": "6L************************************D1"
}
```

#### SendGrid
The app uses SendGrid to send emails containing registration confirmation links, as well as to notify users when money has been transferred to or from their accounts.

Please follow the steps below to configure SendGrid:
1. Register a [SendGrid](https://sendgrid.com/) account.
2. [Create an API key](https://sendgrid.com/docs/ui/account-and-settings/api-keys/#creating-an-api-key).
3. Insert the API key in the following file:
    * *src/Web/BankSystem.Web/appsettings.json*

Example:
```
"SendGrid": {
  "ApiKey": "SA.10*****************************************************DO-zfxp"
}
```
Alternatively, you can delete [this line](../blob/56d67987ce918959202894f5adef251bf61e3d8c/src/Web/BankSystem.Web/Startup.cs#L52) from the _Web/BankSystem.Web/Startup.cs_ file to disable account confirmation.
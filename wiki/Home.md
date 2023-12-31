**BankSystem** is an open-source web project where users can create bank accounts, transfer money, create payment cards, pay with them or directly through their account, etc.
It supports connecting multiple banks together through the _CentralApi_. This allows money to be securely transferred between **separate instances of BankSystem** running on different machines.

## Project links

We have set up a network of two BankSystem instances and one [[DemoShop]], connected through a _CentralApi_. This network supports all BankSystem functionality, including [[Global transfers|Money transfers#Global--worldwide-transfers]], [[Direct payments]] and [[Card payments|Cards#Purchases]].

|Project |Address
|-|-
|**DemoShop** |https://banksystem-demoshop.herokuapp.com/
|**Test Bank 1** <br><br> **Transfer details:** <br> * Bank name - _Bank system_ <br> * Bank country - _Germany_ <br> * Bank code - _ABC_ |https://banksystem-1.herokuapp.com/
|**Test Bank 2** <br><br> **Transfer details:** <br> * Bank name - _Bank system 2_ <br> * Bank country - _Netherlands_ <br> * Bank code - _CBA_ |https://banksystem-2.herokuapp.com/

All of these projects have a demo account already registered:

| Email                 | Password 
|-----------------	|----------
| test@test.com         | Test123$

Additionally, all bank accounts created have an initial balance of €500 for demonstration purposes.

### P.S We kindly ask you not to enable Two Factor Auth in the demo accounts so that all users can log in and see the different sections and functionalities.

## Wiki pages

### [[Getting started]]
>**This page contains important information on how to properly configure BankSystem and CentralApi.**

BankSystem consists of two base components - the bank web application and the _CentralApi_, which securely connects banks running on separate machines together to process [[transfers between different banks|Money transfers#Global--worldwide-transfers]], [[card payments|Cards#Purchases]] and [[direct payments|Direct payments]].

### [[Bank accounts]]
Bank accounts hold information about their owner, balance, transactions, date of creation, etc.

### [[Money transfers]]
BankSystem supports two types of money transfers - internal and global / worldwide.

### [[Cards]]
Cards are used for making purchases on other websites using the _CentralApi_.

### [[Direct payments]]
Direct payments are a way to securely pay on websites directly through a bank account without the need to provide card details.

### [[DemoShop]]
DemoShop is an example web application implementing direct and card payments.

### [[User settings]]

### [[Bank administration]]

***
### Project information

**Used technologies:**
* C#
* ASP.NET Core
* ASP.NET Core MVC
* ASP.NET Core Web API
* Entity Framework Core
* Asymmetric & hybrid encryption
* jQuery
* AJAX
* HTML
* CSS
* Bootstrap

***
## Development Timeline Visualization
### [Video:](https://youtu.be/3Vm7BcysBVc)
[![](https://img.youtube.com/vi/3Vm7BcysBVc/hqdefault.jpg)](https://youtu.be/3Vm7BcysBVc)

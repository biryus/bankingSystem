Cards are used for making purchases on merchant websites. They are connected to a bank account and can be created and deleted at any time.

#### Card listing page
![Card listing page](https://i.imgur.com/8FmLN47.png)

***
### Creation
Cards are created by clicking on the _Create card_ button on the right hand side of the card listing page, or by selecting the _Create new card_ option in the _Cards_ menu on the navigation bar, and then selecting an account for the card to be attached to.

***
### Deletion
Cards can be deleted by clicking the _Delete_ button on the card listing page. A prompt will appear to confirm or cancel the deletion.

Deletions are permanent and a deleted card is invalidated immediately.

![Card deletion prompt](https://i.imgur.com/77NSkiO.png)

***
### Purchases

> Note: Card purchases require the _CentralApi_ to be [[set up and running|Getting started#configuration]].

To make a purchase, a user must provide the card number, cardholder name, expiration date, and security code to the merchant website.

The first three digits of every card number correspond to a specific bank. They are used by the _CentralApi_ to route the payment request to the correct BankSystem instance, which then, after verification, initiates a transfer to the destination account specified in the request.

This functionality is implemented in the included _DemoShop_ project. After choosing to pay by card, the user is asked to fill in their card details.

![Card payment page](https://i.imgur.com/F2CQjBf.png)

A payment request is then generated using the card details and sent to the issuing bank through the _CentralApi_. After it is processed, the order is marked as completed on the My Orders page.

![Completed order](https://i.imgur.com/XalqLyv.png)
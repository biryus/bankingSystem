BankSystem supports two types of money transfers - internal and global / worldwide. Both can be accessed by selecting the _New Transfer_ option on the _Money Transfers_ menu on the navigation bar and choosing a transfer type.

![Money Transfers menu](https://i.imgur.com/bwahU6I.png)

![Transfer type selection page](https://i.imgur.com/yFTVkvd.png)

***
### Internal transfers
Internal transfers are used to transfer money between two accounts within the same bank. On the Internal Transfer page, the user must choose a source account and enter a destination account number or select one of their own accounts from the drop-down menu, which automatically fills in the number of the selected account.

![Internal transfers](https://i.imgur.com/8u28BTg.png)

***
### Global / worldwide transfers

> Note: Global transfers require the _CentralApi_ to be [[set up and running|Getting started#configuration]]

Global / worldwide transfers are used when transferring money between accounts in different BankSystem instances by relaying the transfers through the CentralApi. All communication is securely encrypted and signed to prevent tampering.

To make a global transfer, users must enter the exact details of the recipient and their bank.

![Global transfers](https://i.imgur.com/iN08e9A.png)
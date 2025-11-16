---
title: Operations Done in ACI Issuer Web
---
---
## Creating a New Users for Issuer UI
#### steps
1. ```Login``` to ```Issuer web``` using the ```security module```.
![step 1](/img/Picture11.png "step 1")
2. Click on ```Users```
![step 2](/img/Picture12.png "step 2")
3. Click on the ```Add button```
![step 3](/img/Picture13.png "step 3")
4. Fill in the ```user information```, set a ```password``` and click ```OK```
![step 4](/img/Picture14.png "step 4")
5. Select the ```user``` from the ```user list``` and click the ```“Add User To Groups”``` button from the ```left sidebar```
![step 5](/img/Picture15.png "step 5")
6. Select ```appropriate group``` from the ```Available groups column``` and add it to ```Assigned Group column user``` using the ```">"``` button at the ```bottom``` and click ```OK``` to complete the process.
![step 6](/img/Picture16.png "step 6")
---
## Adding a New Product Type
#### Log in to the ```ACI Issuer Web``` and follow the steps below:
1. Navigate to:
```Product Definition``` → ```Products```
2. Copy an existing product that is most similar to the new one and edit it accordingly:
- Increment the ```Product ID``` or use the ```given ID```.
- Update the Description.
- Input the ```BIN/ICA```.
- Check the following options:
    - Settle Transactions On External System
    - Generate ```Posting Extract```
    - Include ```Single Message Transactions``` On ```Posting Extract```
    - Card File Required
    ---
## Adding a New Card Type
#### Follow the steps below to add a new card type
### PAN Generation
```Log in``` to the ```ACI Issuer Web``` and complete the following steps:
1. Navigate to:
```Payment Device Processing``` → ```PAN Generation```
2. Copy the most similar ```PAN Generation rule``` and modify it as needed:
- Increment the ```ID```.
- Update the ```Description```.
- Assign the ```appropriate Number Generation Template```.
### Payment Device Definition
```Log in``` to the ```ACI Issuer Web``` and follow the steps below:
1. Navigate to:
```Payment Device Processing```→ ```Payment Devices```
2. Copy the most similar ```Payment Device``` and modify it as needed:
- Increment the ```ID```.
- Update the ```Description```.
- Enable the following options:
     - ```EMV Chip Card```
     - Include ```Contactless Application```
     - ```Prevent Reissue```
- Select the ```Primary PAN Generation Rule```
### Account Type Definition
```Log in``` to the ```ACI Issuer Web``` and follow the steps below:
1. Navigate to:
```Product Definition``` → ```Account Types```
2. Copy the most similar ```Account Type``` and modify it as needed:
- Increment the ```ID```.
- Update the ```Description```.
### Linking the New Account Type with a Payment Device
```Log in``` to the ```ACI Issuer Web``` and follow these steps:
1. Select the ```newly created Account Type```.
2. Navigate to: ```Payment Devices``` (on the left panel).
3. Click on ```"Add"```.
4. Choose the following:
- ```Product```
- ```Account Type```
- ```Default Payment Device```
### Linking the New Account Type with a Product
```Log in``` to the ```ACI Issuer Web``` and follow these steps:
1. Click on ```"Add"```.
2. Select the following options:
- ```Product```
- Check ```E-Commerce Allowed```
- Check ```Do Not Re-issue Payment Devices```
- Choose ```Limit Profile```

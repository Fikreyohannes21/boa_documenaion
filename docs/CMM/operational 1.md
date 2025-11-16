---
title: Operational Requests from Card
---
---
## Request for changing the card's status to "Destroyed"
#### Steps
1. Enter the ISSUER region.
2. Navigate to the following directory:
``` cd/home/CMM/psycripts/card_close/ ```
3. Populate the list of PANs nto the file named ```card_file```.
4. Run the following command to change the status of the cards to "Destroyed":
```sh card_close.sh```
5. Check for any PANs in the file named ```failed``` and send it back to the tean if there are any.
---

## Card Production Steps for Test
#### Steps
1. Log in to the production server.
2. Select the ISS region.
3. Navigate to the ```$DATA``` directory:
```cd $DATA```
4. Upload the onboarding file.
5. Take a backup of the ```Migration_File.txt``` file.
6. Copy the onboarding file to ```Migration_File.txt```.
7. Submit the job ```G26S001B```:
(This job creates a PAN and saves the user's data in database tables 10 and 16).
8. Check that there are no rejections in the file ```g26b001b_reject_*_*```.
9. Submit the following 4 jobs sequentially:
• ```submit G00SK09B```
• ```submit G00S047S```
• ```submit G00SA46B```
• ```submit G0AS179B```
10. Copy the newly created perso file:
```cp em01.g179emao_* PersoFiles_ACI/em```
11. Navigate to the PersoFiles_ACI directory:
```cd PersoFiles_ACI/```
12. Run the process script:
```sh process.sh```
13. Go to the Perso directory:
```cd Perso```
14. Download and send the last folder (e.g.,``` VISA_*```) to card printing.
---
## Perso Generation for instant Cards Issuance
#### steps
1. Make the ```flag``` in the following files is set to ```'0'```.
```/boacmm/CMM_BASE_INSTALL1/ISS/DEV1/files/parms/stnd2```
![step 1](/img/image.png "step 1")
2. Log in to the production server.
3. Select the ISS region.
4. Navigate to the ```$DATA``` directory:
```cd $DATA```
5. Upload the onboarding file.
6. Take a backup of the ```Migration_File.txt``` file.
7. Copy the onboarding file to ```Migration_File.txt```.
8. Submit the job ```G26S001B```:
(This job creates a PAN and saves the user's data in database tables 10 and 16).
9. Check that there are no rejections in the file ```g26b001b_reject_*_*```.
10. Submit the following 4 jobs sequentially:
• ```submit G00SK09B```
• ```submit G00S047S```
• ```submit G00SA46B```
• ```submit G0AS179B```
11. Copy the newly created perso file:
```cp em01.g179emao_* PersoFiles_ACI/em```
12. Navigate to the PersoFiles_ACI directory:
```cd PersoFiles_ACI/```
13. Run the process script:
```sh process.sh```
14. Go to the Perso directory:
```cd Perso```
15. Download and send the last folder (e.g.,``` VISA_*```) to card printing.

---
## PIN and CVV2 Request
### Finding PIN – on the test env’t
#### steps
1. Open the ```HSM folder```.
2. Check the ```pin.hsm``` file to ensure that the NG command is not commented, while all
other commands are commented.
![step 2](/img/Picture1.png "step 2")
3. Refer to the table below for the command’s description. For more detailed information on HSM commands, refer to the book ```“Host Command Reference”```.
![step 3](/img/Picture2.png "step 3")
4. Use the following ```SQL query``` to find the ```PIN``` encrypted under the LMK from the database:

```sql
select P.pan_tkn_sky, utl_raw.cast_to_varchar2(P.pan_txt), E.pin_nbr
from issdev1.tgen818 P, issdev1.tgen016 E
where P.pan_tkn_sky || '2020202020202020202020202020202020202020' = E.pan_txt
and trim(utl_raw.cast_to_varchar2(P.pan_txt)) in ('4006780025551253');
```
5. Once you retrieve all the necessary information, run the application named ```HsmScript``` to find the ```PIN```.
### Finding CVV2
#### steps
1. Open the file ```pin.hsm```, located in the ```“HSM” folder```.
2. Comment out all lines of commands, except the one containing the field
```HEADCWA39ABBB482C0396A55B5E0310FCBB0E6```.
3. Replace the ```PAN``` and ```expiry date``` with the card's details for which you are requesting the ```CVV2```.
4. Run the application named ```HsmScript``` to retrieve the ```CVV2```.
---
## Adding Branches in to the Issuer Web
#### steps
1. ```Access the Issuer Web```:
Login to the ```Issuer Web``` using your credentials.
![step 1](/img/Picture3.png "step 1")
2. ```Select the Institution```:
On the first page, choose the ```institution``` for which you want to add a branch.
![step 2](/img/Picture4.png "step 2")
3. ```Navigate to Institution Reference```:
Click on ```Institution Reference``` in the top navigation bar.
![step 3](/img/Picture5.png "step 3")
4. ```Scroll to Bank Branches```:
Scroll down to find ```Bank Branches``` and select it.
![step 4](/img/Picture6.png "step 4")
5. ```Add a New Branch```:
• Click on ```Add``` in the top left.
• Enter the ```ID``` and ```Description for the new branch```.
![step 5](/img/Picture7.png "step 5")
6. ```Verify the Addition```:
After adding the ```branch```, click on the relevant option to check if your ```branch``` has been successfully added.
![step 6](/img/Picture8.png "step 6")
---
## Card Production Stopped (Return Code 24)
#### steps
1. Enter in the ```production Issuer region``` and display the jobs. 
2. Display the jobs until you find a job with a ```return code of 24```. 
3. And then view it to see the ```error type```.
![step 3.1](/img/Picture9.png "step 3.1")
![step 3.2](/img/Picture10.png "step 3.2")
4. Since ```error code 24``` is related to the expiry of the region’s password to the database.
5. Change its database password in ```oracle sqldeveloper```. Find the ```query``` in the internet.
6. Then, run the following 3 ```commands``` respectively.
```sql
mkstore -wrl /boacmm/CMM_BASE_INSTALL1/wallet/ -listCredential
mkstore -wrl /boacmm/CMM_BASE_INSTALL1/wallet/ -deleteCredential ISSPROD1
mkstore -wrl /boacmm/CMM_BASE_INSTALL1/wallet/ -createCredential ISSPROD1
ISSPROD1 newPassWord
```
---

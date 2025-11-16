---
title: Operational Requests from Reconciliation
---
---
## Request for Processing Rejected Cardholder Posting (Locked O-G) Transactions
#### steps to process the locked transactions file
1. Upload the ```Excel file``` to ```WinSCP```:
Upload to: ```/upload/CMM_Files/locked```
2. Enter the Issuer Region:
 ```cd pyscripts/```
3. Upload the file to the specified path:
```sh $DATA/get_sftp.sh```
```/upload/CMM_Files/locked/Locked_Transaction_*.xlsx```
Here replace ```‘Locked_Transaction_*.xlsx’``` with the name of the ```excel file```
4. Rename the uploaded file:
```cp Locked_Transaction_*.xlsx Acct_locked.xlsx```
5. Generate the ```TE file``` using ```Python script```:
```python3.8 gen_TE_server.py Acct_locked.xlsx```
6. Verify file generation:
```ll -ltr```
If no file named ```notfound``` is generated:
Copy the generated files ```(eths, onus, and/or visa)``` to the ```TE file```:
```cat onus eths visa > TE.00006.*_*```
Else, if a ```notfound``` file is generated:
 Take a backup of any generated file ```(eths, onus, or visa)```.
 Run the following ```command``` to regenerate the ```TE file``` for the transaction(s) which is(are) not found using their approval code ```(gen_TE_server.py)```:
```python3.8 gen_TE_server_terminal.py Acct_locked.csv```
 Copy the newly generated files ```(eths, onus, visa)``` along with the backup file to the ```TE file```.
7. Check if the following directory is empty:
```ll /boacmm/Clearing/daily_TE/```
 If it is not empty:
 Wait for the ```Core team``` to process the files.
 If it is empty:
 Copy the ```TE file``` to the directory:
```cp TE.00006.*_* /boacmm/Clearing/daily_TE/```
 Sanitize it using the following command:
```python3.8 /home/CMM/sanitize.py```
8. Notify the Core team via ```Outlook``` to process the file.
---
## Refund and Rejected (Outgoing) Transactions
Here Is How You Can Handle Rejected Transactions
### Rejected Mastercard Transaction
#### steps
1. Identify the reason for rejection from the ```T140 report```.
This can be either:
-    ```File-level error``` (at the ```header```).
-   ```Single transaction``` (field-level) error (e.g., ```Processing Code (F3) error – IRD```).
 2. Fix the issue and generate a new ```outgoing file``` in the ```test environment```.
 ---
 ### Rejected Cardholder Posting
 #### steps
1. Identify the issue and fix it.
 - If the issue is from the ```switch side```, send the ```new cardholder posting file``` to the ```Core team``` for processing.
 - If the issue is from ```T24```, resend the ```original cardholder posting file```.
 ---
 ### Rejected Payment Order Posting
 #### steps
1. Identify the issue and fix it.
- If the issue is from the ```switch side```, send the ```new payment order posting file``` to the ```Core team``` for processing.
- If the issue is from ```T24```, resend the ```original payment order posting file```.
---
### Refund Transaction
#### steps
1. Locate the ```PX file```.
2. Change the transaction type indicator to ```refund```.
3. Process the ```PX file```.
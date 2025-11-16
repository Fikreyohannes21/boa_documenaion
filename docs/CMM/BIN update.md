---
title: BIN Update for Schemes (Visa, MC, and Union Pay)
---
---
## Get BIN file from VISA
#### steps
1. ```Log in``` to ```10.3.15.81```.
2. Open ```Edit Package```.
3. Navigate to the ```Utilities``` tab.
4. Select ```Table Extract Utilities```.
![step 4](/img/Picture17.png "step 4")
5. Select the ```table name``` - ```ARDEF table```.
6. Click ```"Execute"``` to run the command.
![step 6](/img/Picture18.png "step 6")
7. Copy the file from ```C:\EP40\workspace``` to the ```SFTP server```.
8. Copy the file from the ```SFTP server``` to the path ```$DATA``` in the ICG region of the CMM server.
---
## Get BIN file from CUP
#### steps
1. ```Log in``` to ```10.3.15.40```.
2. Navigate to: ```F:\CMM Shared Folder\Incoming\CUP\```.
3. Select the folder with the latest date.
4. Select the file with the largest size.
5. Copy the file from the ```SFTP server``` to the path ```$DATA``` in the ICG region of the CMM server.
---
## Downloading BIN file from MasterCard File Express
#### steps
1. ```Log in``` to ```MasterCard File Express```.
2. Select the file named ```t067``` to download from the screen.
3. Click on ```"Transfer"``` in the toolbar and then select ```"Transfer Selected File"``` from the dropdown menu.
4. The downloaded file will be saved in the ```C:\MCONLINE\MFE\DOWNLOAD``` directory.
![step 4](/img/Picture19.png "step 4")
### Processing t067 Files on Mulugeta’s Server
1. Copy the ```t067``` files to any directory of your choice on Mulugeta’s server.
2. Run the ```bin_rename.py script```, located at**
```C:\Users\user\Desktop\daily_script**```.
3. Enter the path where the ```t067``` files are located.
4. Copy the renamed files to ```C:\ClearingOptimizer_AutoEdit2022.4\Data\MPE Update Files```.
5. ```Deblock``` the files using ```Auto Edit```.
6. Run the ```update command``` on ```Auto Edit```.
![step 6](/img/Picture20.png "step 6")
  - Run this command on CMD 

```
java -cp C:\ClearingOptimizer_AutoEdit2022.4\BatchFiles\JavaFiles\lib\*
com.cloudframe.app.utility.MainframeToMicroFocusConvertor -source
"C:\ClearingOptimizer_AutoEdit2022.4\InputFiles\ParameterMaster\parmmast.var" -target
"C:\ClearingOptimizer_AutoEdit2022.4\Data\IPM Output Files\parmmast_microfocus.var"
```
## Completing the BIN Update on CMM Server

1. Log in to the ```CMM server```.
2. Copy the file to the ```ICG $DATA directory```.
3. Rename ```EpArdefExt.txt``` to ```ardef```.
4. Rename ```parmmast_microfocus.var``` to ```mpe```.
5. Rename the ```CUP BIN``` file to ```ixubn```.
6. Run the ```jobdisp command```.
7. Navigate to ```$COS_UTL_INPUT_DIR``` by running:
```cd $COS_UTL_INPUT_DIR```
8. Execute the batch script:
```batch_run.ksh BOA_ICG_BIN_LOAD_1_STREAM.csv 1```
---
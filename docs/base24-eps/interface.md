---
title: Creating a New Interface
---

---

## Create a new interface “T24_Advice” In UI
#### steps
-	In ```UI``` go to >>```configure``` >>```interface``` >>```host```>> ```ISO 8583(93) Host Interface```      
-	Use the original ```T24 interface``` as a template to create the new ```T24_Advice interface```
-	```Cd $CONFIG``` ….. ```vi config.csv```
-	In ```store and forward menu set``` 
      - ```Assign name``` >> ```SAF_T24_C``` and 
      -  ```SAF Manager name``` >> ```BOA1.SAF1```
-	Under ```station``` menu add  
           -  ```Input/Receive``` >> ```BOA1_A_ADV_01```
           - ```Output/send``` >>  ```BOA1_A_ADV_01```
           - ```Node name``` >> ```unknown```
           - ```Logon type```  >> ```combined Acq/issuer```
           - ```outstanding requests limit``` >> ```100```
           ---
## Create a new action code profile “T24_ADV_ACT_PRFL” 
#### steps
-	In ```UI``` go to >>```configure``` >> ```Action code profile```
-	Use ```T24_ACT_PRFL``` as a template and create ```T24_ADV_ACT_PRFL```
-	Then go to >>```configure``` >>```interface``` >>```host```>>```ISO 8583(93) Host Interface``` , select ```Interface name``` ```T24_ADVICE``` and change the ```Action code profile``` to ```T24_ADV_ACT_PRFL```
---
## Create a new context profile “T24_ADV_CTX_PRFL”
#### steps
-	In ```UI``` go to >>```configure``` >> ```interface```>> ```context profile```
-	```Context profile``` - ```T24_ADV_CTX_PRFL```  & ```Assign name``` - ```CXD_T24```
-	Then go to >>```configure``` >>```interface``` >>```host```>> ```ISO 8583(93) Host Interface``` , select ```Interface name``` ```T24_ADVICE``` and change the ```context profile``` (processing) to ```T24_ADV_CTX_PRFL```  
---
## Create nof file for the new interface “boa1_t24_advice.nof”
#### steps
-	```Cd $ICECFG```
-	```Cp boa1_t24.nof boa1_t24_advice.nof```
-	```Vi boa1_t24_advice.nof```
-	```:%s/T24/ADV```
---
## Create queue 
#### steps
-	```runmqsc $QMNGR```
-	```define qlocal(BOA1.HI93.ADV) like(BOA1.HI93)```
-	```end```
---
## Add the new interface in ADMF
#### steps
-	```cd $CONFIG```
-	```vi admf```
-  add >> ```BOA1_A_ADV_01   BOA1.HI93.ADV      H 01```
---
## Start the new nof “boa1_t24_advice.nof”
#### steps
-	```cd $ICECFG```
-	```r boa1_t24_advice.nof cold```
---
## Restart IS Process  
#### steps
-	in the ```UI```, ```System operations``` => ```Application managment``` => ```Application management summary``` => ```Process summary```
-	 Stop ```IS1```
-	Start ```IS1```
-	Stop ```IS2```
-	Start ```IS2```
---
## Change the routing destination of the advice to the new interface “T24_ADVICE”
#### steps
-	In ```UI``` go to >>```configure``` >>```routing``` >> ```Destinations```
-	Change the ```primary destination``` of ```Advice 1``` information to ```T24_ADVICE```

Use the below table to change the ```primary destination``` of ```Advice 1``` information

---
## Change the routing destination of the advice to the new interface “T24_ADVICE”
#### steps

Use the table below to change the primary destination of Advice 1 information:

| Destination Routing Profile | Route Code | Existing Primary Destination of Advice 1 Information | New Primary Destination of Advice 1 Information |
|-----------------------------|------------|----------------------------------------------------|-------------------------------------------------|
| ACI_ISSUER                 | WDL        | T24                                                | T24_ADVICE                                      |
| CUP_ISSUER                 | WDL        | T24                                                | T24_ADVICE                                      |
| ETH_SWITCH                 | OTHER_TXN  | T24                                                | T24_ADVICE                                      |
| MDS-ISSUER                 | WDL        | T24                                                | T24_ADVICE                                      |
| VSMS_ISSUER                | WDL        | T24                                                | T24_ADVICE                                      |
---
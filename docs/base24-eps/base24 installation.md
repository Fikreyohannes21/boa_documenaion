---
title: Base24-eps Installation Guide
---

---
## Base24-eps installation
#### steps
1)	Refer ```“Implementation Checklist Base24-eps v0.2”``` before starting installation 
2)	Request Infrastructure team to install ```Oracle``` and ```MQ``` on the server
3)	Make sure installing linux user can create a ```queue manager```. Eg. ```Crtmqm test```
4)	Install ```Java```
-	Put the ```jdk-8u261-linux-x64.tar.gz``` file in ```/opt/java```
-	```tar zxvf``` ```jdk-8u261-linux-x64.tar.gz```
-	```update-alternatives``` ```--install /usr/bin/java``` ```java /opt/java/jdk1.8.0_261/bin/java 1```
-	```update-alternatives --config java```
5)	Follow and fill the ```Linux-UNIX Pre-Install Checklist and Worksheet``` 
e.g ```BASE24-eps 3.0.6 - Linux-UNIX Pre-Install Checklist and Worksheet.docx```
6)	Install the necessary ```Packages```
-	```yum install pax-3.4-19.el7.x86_64.rpm```
-	```yum install perl*```
-	```yum install dos2unix```
-	```yum install vsftpd```
-	```yum install pax-3.4-19.el7.x86_64.rpm```
-	```yum install spax-1.5.2-13.el7.x86_64.rpm```
-	```yum install tcpdump```
7)	Download Base24 installation file from support
[ACI Worldwide Support](https://www.aciworldwide.com/support)
(Go to ```Product Central``` > ```ACI Product Downloads```)
8)	Make sure that ```firewall``` is disabled and ```ftp``` is enabled from ```ssh```
```service firewalld status```
```service vsftpd status```
9)	Extract

 ![Extract](/img/Picture24.png "Extract")


10)	Add the ```hardened apache-tomcat-7.0.85.tar.gz``` to the extracted directory.
11)	Install ```ICE-XS application```
	- Refer ```Install ICE-XS.docx```
12)	Run ```ES_Install.exe```
13)	```Introduction``` >```next```
14)	```License Agreement``` > ```accept```
15)	Choose ```install set``` > ```UNIX```
16)	Choose ```install folder```
17)	```System Prefix``` e.g ```BOA1```

18)	Host Information
-	```DNS name``` or IP of the Host e.g dc-base24-app
-	```Host Install Location``` e.g /ACI/b24eps
-	```Location of ICEXS Directory``` e.g /ACI/icexs
-	```Java Home Location``` e.g /opt/java/jdk1.8.0_261
-	```Desktop Title``` e.g ACI Desktop – PROD
-	```Tenants Type``` > Single tenancy

19)	```Credentials for host``` >Do not validate
20)	Oracle Database information
-   ```Oracle home location```
-	```Oracle tnsname.ora location``` 
-	```Oracle DB SID ```
-	```Oracle DB Schema```
-	```Oracle DB App ID```
21)	Oracle Database Information
```db_ora_ts_journal```=```EPS_EPSPROD_JOURNAL```
```db_ora_ts_journal_idx```=```EPS_EPSPROD_JOURNAL_INDEX```
```db_ora_ts_context```=```EPS_EPSPROD_CONTEXT```
```db_ora_ts_context_idx```=```EPS_EPSPROD_CONTEXT_INDEX```
```db_ora_ts_acct```=```EPS_EPSPROD_CARD```
```db_ora_ts_acct_idx```=```EPS_EPSPROD_CARD_INDEX```
```db_ora_ts_dynamic```=```EPS_EPSPROD_DYNAMIC```
```db_ora_ts_dynamic_idx```=```EPS_EPSPROD_DYNAMIC_INDEX```
```db_ora_ts_other```=```EPS_EPSPROD_OTHER```
```db_ora_ts_other_idx```=```EPS_EPSPROD_OTHER_INDEX```
22)	Linux MQ information
-	```Manager name``` e.g BOA1.MANAGER
-	```QUEUE prefix``` e.g BOA1
23)	```System Time Offset```  > ```GMT-3```
24)	HSM Devices
e.g
```sec_hsm1```=HSM1
```sec_hsm1_ip```=10.70.0.128
```sec_hsm1_port```=1500
```hsm1_typ```=R
```sec_hsm2```=HSM2
```sec_hsm2_ip```=10.70.0.128
```sec_hsm2_port```=1500
```hsm2_typ```=R
25)	```UI Component``` > ```UNIX```
-	```DNS``` or ```IP Address``` Where ```UI component``` will be installed e.g 10.1.13.122
-	Install Location of ```UI component``` e.g /home/eps/eps_ui
-	```Java Home Location``` e.g /opt/java/jdk1.8.0_261
-	Server Type > Tomcat
26)	```ESWEB Third Party``` Location
-   ```3rd Party Jar Location``` 
-	```JDK Location``` 
27)	```Input Base Port``` e.g 8000
28)	```Installation Summary``` – ```UNIX```
- ```Check Summary```>```next```
29)	Installation will start 
30)	```Name``` and ```Password``` to ```FTP```
   -  ```Name```: - username eg. eps
   -  ```Password```:-Password 
- ```FTP Results```
- ```Check the Result``` > ```next```
31)	```FTP Summary``` >```done``` 
32)	```Check log on``` eg. C:\_BASE24-EPS --PROD\FTP\Upload_Installation_Results.txt
33)	```Check the ftp file``` on $ES_HOME/install 
34)	Do ```dos2unix``` if needed
35)	```chmod u+x essetup```
36)	```./essetup```
37)	On another window > ```tail –f essetup.log```
38)	```Do you want to continue to update your system? (y/n)``` choose ```y```
39)	```Check log``` and ```status```.
40)	Start the processes
-	```start_manager.sh```
-	```Start tdal```
-	```start acijmx```
-	```start esweb````
-	```start Versionchecker```
---
---
### In ```UI``` start the processes
-	```run evtadapter```
-	```run timrp```
-	```run SVCLOC```
-	```run CNFG```
-	```run is 1```
-	```run is 2```
-	```run is 3```
-	```run xml```
-	```run jqbtch```
-	```run safm```
-	```run rfsh```
-	```run ttlm 1```
-	```run tbp```
-	```run cmcp```
-	```run atbm```
-	```run eopp```
---
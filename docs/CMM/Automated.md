---
title: Automated Region Installation
---
# Automated Region Installation
Installation utilities are supplied that provide an automated process for the installation of ```ACI Issuer```, ```ACI Acquirer``` and ```ACI Interchange``` on ```AIX``` and ```Linux``` platforms. The installation tool requires that an installation configuration file is created as described in this guide.
# Usage guide
To start a CMM server application installation, enter the following command:
```ESS_UTL_REGION_CREATE.ksh  -ci  <full path of install configuration file>  <PRODUCT NAME>  <REGION NAME>```
The product name parameter should use one of the following three options:
```ACQ``` For an ```ACI Acquirer```, ```ICG``` For ```ACI Interchange```, ```ISS``` For ```ACI Issuer```
The region name could be any name with max of 4 characters. For example, DEV1 or PROD
# Install configuration file
An install configuration file contains a set of optional, mandatory, or conditional configuration properties, each in the following format with no trailing spaces:
```PropertyName```:```PropertyValue```
Head over to the installation directory ```(/boacmm/install_ini)``` and create ```.ini file``` for a specific region ```(Apr2024_updateISS_DEV1.ini)```. The following table contains a list of configuration properties that the automated installation process recognizes:
![table 1](/img/CMM1.png "table 1")
![table 1](/img/CMM2.png "table 2")
![table 3](/img/CMM3.png "table 3")
![table 4](/img/CMM4.png "table 4")
![table 5](/img/CMM5.png "table 5")
![table 6](/img/CMM6.png "table 6")
![table 7](/img/CMM7.png "table 7")
![table 8](/img/CMM8.png "table 8")
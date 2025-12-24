---
title: Base24 upgrade action plan
---
---
## Base24-eps UI (3.0.26+) - ES_Desktop Installation
#### steps
1. Please download the JDK 21 installer for Windows and install it on your workstation 
2. ES_Desktop Installation
    -  Double click on the file shared from ACI/switch team (ES_Desktop.exe) 
    - Allow the app to make changes to your device? – click yes 
    - Click next on the next window 
    ![step 3](/img/upgrade1.png "step 3")
    - Check the Accept the terms checkbox and click next 
    ![step 4](/img/upgrade2.png "step 4")
    -  Choose installation directory starting from c:\ (e.g:- c:\ACI\Base24eps) from your windows pc or click choose and give the directory you want.  

      Note: - the application won’t start if it is installed on C:\Program Files or C:\Program Files (x86) so please do as suggested above and click Next 
      ![step 5](/img/upgrade3.png "step 5")
      - Tick where you want the startup icon to be or just click next 
      ![step 6](/img/upgrade4.png "step 6")
      - Give a reasonable desktop title (e.g Base24-eps production) and click next
      ![step 7](/img/upgrade5.png "step 7")
      - Enter UI installation server IP(10.1.13.122 for production) , tick TLS 1.2 Desktop Connection option and click next 
      ![step 8](/img/upgrade6.png "step 8")
      - Enter version checker IP(10.1.13.122 for production) and click next 
      ![step 9](/img/upgrade7.png "step 9")
      - Please enter java jdk installation location for your widows’ pc and click next 
      ![step 10](/img/upgrade8.png "step 10")
      - Please enter the 3rd party jar files’ location on your workstation and click next (these files are shared by switch team along with the installer file. give the path where jar files are stored e.g. C:\3rd party jar)
       ![step 11](/img/upgrade9.png "step 11")
      - Enter base port (8000 for now) and click next 
      ![step 12](/img/upgrade10.png "step 12")
      - Click Install 
      ![step 13](/img/upgrade11.png "step 13")
      - Click Done 
       ![step 14](/img/upgrade12.png "step 14")
      - Go to your installation directory (e.g. C:\ACI\Base24eps) on your workstation and double click on the RunDesktop.bat file inside the desktop directory 
       ![step 15](/img/upgrade13.png "step 15") 
      - On Version checker update prompt click update
        ![step 16](/img/upgrade14.png "step 16") 
      - Login to ES_desktop using your credentials 
      - To ES_Desktop next time the RunDektop.bat file or the DesktopLauncher.exe can be used  
# 4d-topic-odbc-driver-for-mac

as of v19, the preferred way to access 4D Server datastore from an external application is to use the [REST API](https://developer.4d.com/docs/REST/REST_requests). the API is a prorietary protocol that runs on top of the integrated HTTP server to access [dataclasses, attributes and functions](https://developer.4d.com/docs/REST/manData) as well as [singleton classes](https://developer.4d.com/docs/Concepts/classes#singleton-classes) . [user authentication and session management](https://developer.4d.com/docs/REST/authUsers) is also built in. the feature is exclusive to [project mode](https://doc.4d.com/4Dv20/4D/20.2/Converting-databases-to-projects.300-6750126.en.html) and unlocked by the 4D Client Expansion license, not the Web Application Expansion or Web Sercvices Expansion licenses.

> [!NOTE]
 you can search for more information in the blog with the [REST](https://blog.4d.com/tag/rest/) tag

in earlier versions (4D v11 SQL and above), ODBC the primary technology to access 4D Server database from 3rd party software. in this setup, a client application would send SQL requests to 4D Server having configured [4D ODBC Driver](https://doc.4d.com/4Dv20/4D/20/4D-ODBC-Driver.100-6341902.en.html) as a data source name. native drivers were available for Mac OS X (PowerPC and Intel), Windows (32-bit and 64-bit), macOS (Intel 32-bit and 64-bit). obsolete platforms/architectures were retired. in 2021 4D announced that [Apple Silicon will not be supported](https://discuss.4d.com/t/macos-end-of-support-for-4d-odbc-driver-4d-for-oci-s2-2021/17013/19). as of v20, **the only supported platform for 4D ODBC Driver is Windows x64**.

the final release of 4D ODBC Driver for Mac x64 was v18.6. 

this article is an unofficial tutorial of how to setup ODBC for 4D Server on modern macOS hardware.

* download [4D ODBC Driver 18.6 for Mac](https://github.com/miyako/4d-topic-odbc-driver-for-mac/releases/tag/odbc-driver-macos-x64-18.6)

* copy `4D ODBC Driver x64.bundle` to /Library/ODBC/

<img src="https://github.com/user-attachments/assets/5348c5d3-7cfb-4da1-90f3-ddb9abc69de9" width=600 height=auto />

you may need to create the folder manually.

* create a file named `odbcinst.ini` in the same location with the following content

```
[ODBC Drivers]
4D ODBC Driver 64-bit = Installed

[4D ODBC Driver 64-bit]
Driver = /Library/ODBC/4D ODBC x64.bundle/Contents/MacOS/4D ODBC x64
Setup  = /Library/ODBC/4D ODBC x64.bundle/Contents/MacOS/4D ODBC x64
APILevel = 2
ConnectFunctions = YYN
DriverODBCVer = 3.52
FileUsage = 0
SQLLevel = 3
```

this file is used by ODBC administration software to discover ODBC drivers installed on the system.

* Download and install [ODBC Manager](https://odbcmanager.net/index.php) by [Actual Technologies](http://www.actualtech.com/)

> [!WARNING]
[iODBC](https://www.iodbc.org/dataspace/doc/iodbc/wiki/iodbcWiki/WelcomeVisitors) by OpenLink Software can't be used to add or remove 4D ODBC Driver
> 
> <img src="https://github.com/user-attachments/assets/50b16e34-0215-4e6c-be27-ab881221bcd7" width=400 height=auto />
>    
> <img src="https://github.com/user-attachments/assets/5a811159-8695-42aa-a3ac-285c67207790" width=300 height=auto />

* launch ODBC Manager (installed in /Application/Utilities/)

* add 4D ODBC Driver 64-bit

<img src="https://github.com/user-attachments/assets/14d21ac7-4416-4042-8a1c-b164f9e61fe3" width=400 height=auto />

* double-click on the entry and add the following key-value pairs:

> [!NOTE]
the information is stored in a file named `obbc.ini`
 
```
Driver: /Library/ODBC/4D ODBC x64.bundle/Contents/MacOS/4D ODBC x64
Server: the server address
UID: username
PWD: password
```

> [!NOTE]
you do not need to add the TCP port number (e.g. `:19812`) to the server address

<img src="https://github.com/user-attachments/assets/f26bd293-905f-4bde-a69c-ab95c3341dc2" width=400 height=auto />

* launch 4D Developer or 4D Server and start the SQL server.
 
* launch a Intel/Rosetta client application other than 4D

> [!WARNING]
 ODBC connection between 4D applications is not supported and may result in problems 

To Be Continued.

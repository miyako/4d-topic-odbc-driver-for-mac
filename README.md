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

this file is used by ODBC managers to discover ODBC drivers installed on the system.

* Download [ODBC Manager](https://odbcmanager.net/index.php) by [Actual Technologies](http://www.actualtech.com/)

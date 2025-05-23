# 4d-topic-odbc-driver-for-mac

as of v19, the preferred way to access 4D Server datastore from an external application is to use the [REST API](https://developer.4d.com/docs/REST/REST_requests). the API is a prorietary protocol that runs on top of the integrated HTTP server to access [dataclasses, attributes and functions](https://developer.4d.com/docs/REST/manData) as well as [singleton classes](https://developer.4d.com/docs/Concepts/classes#singleton-classes) . [user authentication and session management](https://developer.4d.com/docs/REST/authUsers) is also built in. the feature is exclusive to [project mode](https://doc.4d.com/4Dv20/4D/20.2/Converting-databases-to-projects.300-6750126.en.html) and unlocked by the 4D Client Expansion license, not the Web Application Expansion or Web Sercvices Expansion licenses.

> [!NOTE]
 you can search for more information in the blog with the [REST](https://blog.4d.com/tag/rest/) tag

in earlier versions (4D v11 SQL and above), ODBC the primary technology to access 4D Server database from 3rd party software. in this setup, a client application would send SQL requests to 4D Server having configured [4D ODBC Driver](https://doc.4d.com/4Dv20/4D/20/4D-ODBC-Driver.100-6341902.en.html) as a data source name. native drivers were available for Mac OS X (PowerPC and Intel), Windows (32-bit and 64-bit), macOS (Intel 32-bit and 64-bit). obsolete platforms/architectures were retired. in 2021 4D announced that [Apple Silicon will not be supported](https://discuss.4d.com/t/macos-end-of-support-for-4d-odbc-driver-4d-for-oci-s2-2021/17013/19). as of v20, **the only supported platform for 4D ODBC Driver is Windows x64**.

the final release of ODBC Driver for Mac x64 was 18.6. 

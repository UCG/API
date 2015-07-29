# API
Documentation for UCG API

##Current Version
By default, all requests receive the v1.0 version of the API.
To access on the web, go to the following URL: 
```
http://www.ucg.org/api/v1.0/
```
Here you will see the additional calls you can make from your user account.

##Schema
Blank fields are typically returned as ```null``` or empty

All timestamps are returned in ISO 8601 format:
```
YYYY-MM-DDTHH:MM:SSZ
```

##Parameters
Many API methods take optional parameters. For GET requests, any parameters not specified as a segment in the path can be passed as an HTTP query string parameter:
```bash
$ curl -i "http://www.ucg.org/api/v1.0/media?production=209"
```
This example pulls a list of media filtered by the production type 209, which is "Beyond Today Television Program"
##Root Endpoint

##Authentication
@todo


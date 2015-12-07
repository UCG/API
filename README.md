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
$ curl -i "http://www.ucg.org/api/v1.0/media?filter[production]=209"
```
This example pulls a list of media filtered by the production type 209, which is "Beyond Today Television Program"
##Root Endpoint

##Consuming the API
The following examples use the *media* section of the API.

###Calling a list of media items
```bash
$ curl http://www.ucg.org/api/v1.0/media
```
###View multiple items at once
```bash
$ curl http://www.ucg.org/api/v1.0/media/1,2
```
###Exploring the API
Using a HTTP ```GET``` request on a resource's root URL will return info about that resource, and the data itself.
The data results are stored in the ```data``` property of the JSON response, while the ```self``` and ```next``` objects contain additional information about the resource being called.
```json
"self":{
"title":"Self",
"href":"http://www.ucg.org/api/v1.0/media"
},
"next":{
"title":"Next",
"href":"http://www.ucg.org/api/v1.0/media?page=2"
}
```
### Returning specific fields
Using ```?fields``` query string, you can declare which fields should be returned. You can return most fields, but specific may not be returned without the rest of the item.
```bash
$ curl http://www.ucg.org/api/v1.0/media/225856?fields=created
```
Returns the following: 
```json
"data":[
{
"created":"1438013820"
}
],
```
##Filtering

##Authentication
Access to the API is restricted to 100 GET calls a day to unauthenticated users. Authenticated connections can call on the API an @todo (unlimited?) times per day.

In order to gain authenticated access you must first have an account at ucg.org. Then request authenticated access to the API by @todo.

After recieving API access permission you can gain less restricted access to the API. Connect the api and request a "Token" using the method below. Then Append the URL GET variable access_token with your Token to all of your requests.
```
# (Change username and password)
curl -u "username:password" https://ucg.org/api/login

# Response has access token.
{"access_token":"YOUR_TOKEN"}

# Call a "protected" with token resource
curl https://ucg.org/api/v1.1/media/1?access_token=YOUR_TOKEN
```

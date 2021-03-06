# auto-mock-server
A simple mock server that reads and exposes resources with minimal config

## How to setup the project :
* configure config.json located at the project root.

Type the following command :
* bower install
* node install

## How to launch the server :
Type the following command :
* node auto_mock_server.js
* shorthand npm start (in project directory)

## How to expose a mocked resource :
A mock is currently composed of two files :
* config.json --> a resource config file, currently only containing the http method to expose the resource on
* mock.json --> the content to be served
* schema.json -> the json schema related to mock.json

## How to configure the port :
By default, the server runs on port 8000, you may pass an argument to the app to change the used port :
* node auto_mock_server.js 8001

## Mock files :
* config.json : informations about the mock (mandatory)
* mock.json : mock content
* schema-mock.json : mock content JSON schema
* schema-payload.json : payload content JSON schema
* http-codes.json : forecast http codes
* README.md : description of the mock of whatever in md format
* images

## How to organize your mocks :
```
/mocks/{version}/{methodName1}/{methodName2}/.../{methodNameX}/{methodType}
/mocks/{version}/{methodName1}/{methodName2}/.../{methodNameX}/{methodType}/config.json
/mocks/{version}/{methodName1}/{methodName2}/.../{methodNameX}/{methodType}/mock.json
/mocks/{version}/{methodName1}/{methodName2}/.../{methodNameX}/{methodType}/schema-mock.json
/mocks/{version}/{methodName1}/{methodName2}/.../{methodNameX}/{methodType}/schema-payload.json
/mocks/{version}/{methodName1}/{methodName2}/.../{methodNameX}/{methodType}/http-codes.json
/mocks/{version}/{methodName1}/{methodName2}/.../{methodNameX}/{methodType}/README.md
/mocks/{version}/{methodName1}/{methodName2}/.../{methodNameX}/{methodType}/{image}.["png", "jpeg", "jpeg", "gif"]
```
## How to send a POST request with a payload
* Using curl or a tool like Postman, you can send POST requests to a WS in the mock server.
* Specify a payload in the body and it will be checked against the associated schema-payload.json
* Check your Node.js console to see if the request is valid or not


*Note :
You may use a directory tree structure to express a RESTFULL API. For example, if you create the folder "user" under the "mocks/1.0/" folder,
any resource inside the "user" folder will be exposed at localhost:8000/1.0/user
This works recursively, so you can expose resources like this :
localhost:8000/1.0/user/login/admin/...*

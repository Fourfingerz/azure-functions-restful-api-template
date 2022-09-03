# Azure Functions NodeJS Templater

You can use this sample "Vacations" RESTful API as a template and  kickstart autonomous code deployments on code push to deploy your code to Azure Functions.
___

### Folder Structure 

This is a typical Azure Functions project directory structure:
```
FunctionsProject
 | - MyFirstFunction
 | | - index.js
 | | - function.json
 | - MySecondFunction
 | | - index.js
 | | - function.json
 | - services (shared code)
 | | - myFirstHelperFunction.js
 | | - mySecondHelperFunction.js
 | - node_modules
 | - host.json
 | - package.json
 | - extensions.csproj
 ```

In our example, 

`/services/data.ts` 

contains the "data" that is right now just a JavaScript object that can be replaced by an actual database (ie MySQL/Postgres/Mongo) and contains the data transformation functions to fetch and manipulate said data for the API.

`/services/vacation.service.ts`

is the stand-in for our ExpressJS server. Notice I have commented out the ExpressJS lines that are now replaced by the equivalent Azure Function API calls.

`/services/index.ts`

is what ties the API all together and exports our API as a package.

`vacations-get`, `vacations-post`, `vacations-put`, `vacations-delete` directories imports the `services` directory and is each of our API calls now mapped to an Azure function call with an Azure built in `httpTrigger` from it's standard library. 

___

### Local Development

Install Azure function tools to develop locally:

`npm install -i g azure-functions-core-tools --unsafe-perm true`

Install npm dependencies:

`npm install`

Boot up Azure Functions local webserver:

`npm start`

You should see the following output if Azure Functions local is up and running:
```
Azure Functions Core Tools
Core Tools Version:       4.0.4736 Commit hash: N/A  (64-bit)
Function Runtime Version: 4.8.1.18957


Functions:

        vacations-delete: [DELETE] http://localhost:7071/api/vacations/{id}

        vacations-get: [GET] http://localhost:7071/api/vacations

        vacations-post: [POST] http://localhost:7071/api/vacations

        vacations-put: [PUT] http://localhost:7071/api/vacations/{id}

```

___


### Deploy to public Azure Functions
Push to `master` branch, there's a Github Actions Workflow that will take care of deployment to Azure
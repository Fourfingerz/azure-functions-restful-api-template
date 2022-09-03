# Azure Functions NodeJS Templater

You can use this sample "Vacations" RESTful API as a template and  kickstart autonomous code deployments on code push to deploy your code to Azure Functions.
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
# CICD-pipeline

- Download
  - [CICD.postman_collection.json]()
  - [workspace.postman_globals.json]()
  - [Test.postman_environment.json]()
- Import all in Postman


## Set up the environments

Go to Environtments --> Globals and fill the variables:
- Mendix-Username: This is your emailadres at Mendix
- Mendix-ApiKey:
  - Go to https://sprintr.home.mendix.com/link/personalapikeys
  - Create and API-key and use this one
- Mendix-PAT:
  - Go to https://user-settings.mendix.com/link/developersettings
  - Create a PAT-Token, with scopes:
    - mx:modelrepository:repo:read
    - mx:deployment:write
    - mx:deployment:read
- TeamsWebhook, if you'd want to send a message to a Teams-channel for failed unit tests
- RegressionTestURL, if you want to also start your external regression tests, put an URL here. You may have to adjust this step

Go to Environtments --> Test and fill the variables:
- appid: with the Name of the app, usually found in the default URL of your app
- appguid: guid in general settings in Sprintr
- branch: trunk (svn) or main (git)
- deployVersion: 1.2.3 (or whatever you'd want as the versionnumber). Needs to be in x.x.x format
- runUnittests: true or false. In case of true, also fill these:
  - UnitTestPassword: constant UnitTesting.RemoteApiPassword
  - appURL (don't add the / after .com)
- runRegressiontests: true or false. In case of true, also fill the RegressionTestURL in the "Globals" environment
- Any other variables will be created automatically during the run

## Run the script
- Select the Test environtment (right-top corner)
- Go to the collection CICD and press the ... and then "Run collection"
- Press the orange "Run CICD" button and see what happens

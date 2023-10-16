# _PSI_

## Table Of Contents 
  * [Overview](#overview)
  * [Prerequisites](#prerequisites)
  * [Build and Run on local](#build-and-run-on-local)
  * [Cucumber Html Report](#cucumber-html-report)

## Overview
Cypress automation test suite

## Prerequisites
* Cypress   
* Visual studio code
* MacOs
* Linux
* Local workflow

 ##### Cypress :
* For installing and setup cypress click on the below link and follow the instructions.
[Installing Cypress](https://docs.cypress.io/guides/getting-started/installing-cypress).
* Cypress version : 12.17.4

##### MacOs
* Install the dependencies by running `brew bundle`.
* Install the git pre commit hooks by running `pre-commit -install`
* The first time you run `bin/cucumber-json-formatter` it will ask you allow the exutable in the System Settings. (more details here)

##### Linux
* Run to install envsubst
```
apt-get update && apt-get install gettext-base
```

##### Local workflow
1. Copy the template environment to create a local copy:
```
Use file environment/local.env
```
2. Edit the file and set the password

3. To execute test:
```
npm run test:local
```

## Build and Run on Local
* Run EsLint
**_npm run check_**

* Clean reports, screenshots, videos and dependencies
**_npm run clean_**

* Clean only reports, screenshots, videos
**_npm run delete:all_**

* Install Cypress
**_npm install cypress_**

* Install all packges
**_npm install_**

* Run all test cases headless
**_npm run test_**

* Run all test cases headed
**_npm run test:headed_**

* Run all test cases in chrome
**_npm run test:chrome_**

* Run all test cases in firefox
**_npm run test:firefox_**

* Run test with Tags
**_npm run test -- -e TAGS='tag'_**  
            OR 
**_npx cypress run -e TAGS='tag'_**

* Run test with Tags headed
**_npm run test -- -e TAGS='tag' --headed_**

* Run test with disabled recording
**_npm run disableVideoTest_**

### Report
* Cucumber Html Report
**_node cucumber-html-report_**

* Report Folder Path
**_./testReport_**

## Note:
* Run all commands in GIT Bash Terminal
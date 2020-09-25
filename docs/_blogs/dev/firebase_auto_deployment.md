---
title: Steps to auto Firebase deployment using GITHUB Actions (CI/CD)
description: Firebase deployment
---

Step #1
Create a GITHUB repository

Step #2
Create a Firebase Project on the Firebase console

Step #3
$ firebase init
And choose your project and select Hosting from the CLI tool

Step #4
Create package.json using
$ npm init
Once the package.json created add the following component on the JSON under scripts
"build:production": "node --version",
"build:prod": "node --version",
The final package.json will look like this

package.json
{
  "name": "cicd",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "build:production": "node --version",
    "build:prod": "node --version",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/muthugit/cicd.git"
  },
  "author": "",
  "license": "ISC",
  "bugs": {
    "url": "https://github.com/muthugit/cicd/issues"
  },
  "homepage": "https://github.com/muthugit/cicd#readme"
}
Step #5
Create the workflow file (main.yml) on the following directory
$ <root directory>/.github/workflows
main.yml
name: FIREBASE-DEPLOY

on:
  push:
    branches:
    - master
    - release/*


jobs:
  firebase-deploy:


    runs-on: ubuntu-latest


    steps:
    - uses: actions/checkout@master
    - uses: actions/setup-node@master
      with:
        node-version: '10.x'
    - run: npm install
    - run: npm run build:prod
    - uses: w9jds/firebase-action@master
      with:
        args: deploy --only hosting
      env:

        FIREBASE_TOKEN: ${{ secrets.FIREBASE_TOKEN }}
Step #6
Get the Firebase token by running this
$ firebase login:ci
Step #7
Goto GITHUB.com and navigate to your repository
Goto Settings -> Secrets
Create new secret
Copy the secret generated on the previous step and name the secret as FIREBASE_TOKEN
Step #8
Thats it! Just push your code. This will deploy the PUBLIC folder to firebase hosting
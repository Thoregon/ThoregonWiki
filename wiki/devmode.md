# Testdata

## Dev Mode

1) when from localhost
2) url param &isDev=true|false

3) prod: thoregon.html, dev: thoregondev.html

Settings:

export in File: universe.dev.mjs (not in git, deveploper private)

````javascript
 export const DEV = {
     ssi: TESTIDENTITY,
     apps: {
         'example-application' : { 
            instance: 'MYDEV', 
            testdata: ['/module-testdata/testdataA.mjs', '/module-testdata/testdataB.mjs', '/module-testdata/testdataC.mjs'],
            autoreload: true 
         },
     },
     thoregon: 'prod'    // 'prod' uses or loads thoregon system into browser cache from repo ; 'dev' loads also thoregon system via the dev server
 }
````

## Usage
1) Dev Identity for each developer

2) Testidentity for all
    - use different app instances
    - -> config (non git) to select the instance

3) Fork with non persistent data in app tree

Fn -> API on the app home

- home defines sub roots for objects

- backup
- purge
- restore

API for test data in dev environment only

[Test Data](testdata.md)

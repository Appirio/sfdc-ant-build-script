# sfdc-ant-build-script
Build script for Salesforce projects

### Prerequisites
1. Ant version greater than 1.6, tested with 1.10.1 (latest version).
2. Install [Java, ant, and the Force.com Migration Tool (ant-salesforce.jar)]( https://resources.docs.salesforce.com/sfdc/pdf/salesforce_migration_guide.pdf)

3. Copy ```./build-sample.properties``` to ```../../build.properties``` (two directories up)

4. Update ```../../build.properties``` with your own usernames and passwords

### Commands

See the build.xml for the definitive list of commands.  Typical syntax is:

 ```
 ant dev2qa -Dversion=1.0
 ```

This will command will:
- retrieve the Salesforce metadata from the dev environment based upon ```package-1.0.xml```
- store this metadata in a local folder called  ```dev sprint 1.0```
- copy ```destructiveChanges-1.0.xml``` (if it exists) to ```dev sprint 1.0/destructiveChanges.xml```
- deploy this metadata to the qa environment

Our environment flow looks like:

![Environment Flow](http://drive.google.com/uc?export=view&id=0Bz-xKipcMk3xZ2xjMXE3Ykh6Q2M)

Often used commands are:

 ```

ant local2dev -Dversion=1.0 -Dsource=dev
ant local2itdev -Dversion=1.0 -Dsource=dev
ant dev2full -Dversion=1.0
ant qa2full -Dversion=1.0
ant itdev2full -Dversion=1.0
ant itdev2full-specified-tests -Dversion=1.0 -DspecifiedTests=TestClassName
ant full2prod -Dversion=1.0
ant full2prod-specified-tests -Dversion=1.0 -DspecifiedTests=TestClassName
 ```

Optional parameters exist for checkOnly and/or runAllTests (which default to false).  For example:

 ```
 ant dev2qa -Dversion=3.6 -DcheckOnly=true -DrunAllTests=true
 ```

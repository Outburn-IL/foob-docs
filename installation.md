# Installing Intersystems FUME Plugin

The FUME Plugin installation is possible using ZPM (IPM) package manager.

The installer supports different platforms and workflow scenarios and can be adapted to new or existing IRIS implementations. Supported scenarios are:
 -  Existing IRIS or HealthShare Health Connect with FHIR Repository
 -  Existing IRIS or HealthShare Health Connect  without FHIR Repository when FHIR Repository is intended to be deployed as a part of the IRIS platform. 
 -  Existing IRIS or HealthShare Health Connect with 3rd party FHIR Server
 -  New IRIS or HealthShare Health Connect installation

If ZPM is not installed on your server yet, install it according to the instructions on the official [IRIS ZPM (IPM) package manager page](https://github.com/intersystems/ipm).

> Prerequisites:
1. Outburn FUME (Community or Enterprise edition) is installed on the server accessible by IRIS, and the FUME Rest API is exposed. 
   **!Important note!**  In case the FUME instance is supposed to use the new IRIS FHIR repository (which hasn't been created yet) as a Conformance Resource repository, our recommendation is to complete FUME configuration after the 3rd step of FUME Plugin installation. 
2. Install FUME   
3. ZPM is installed on the target IRIS server.
4. Target namespace and database were created (if required)
   
> Installation / Upgrade procedure:
1.	Open InterSystems IRIS for Health terminal
2.	Authenticate yourself using your credentials
3. Switch the namespace to the target one where FUME Plugin will be installed
```shell
%SYS> zn "FUME"
FUME>
```
4. Launch ZPM:
```shell
FUME> zpm
```
5. On the next step, you have to switch ZPM to use the package registry. In the following example, Outburn private registry is used. Yours will vary. To get credentials for the Outburn private registry, please send the request to **info@outburn.co.il**:
   
```shell
zpm:FUME> repo -r -n registry -url http://ec2-3-124-79-139.eu-central-1.compute.amazonaws.com:52773/registry/ -user <user> -pass <password>
```

6.	Start installation/upgrade

```shell
zpm:FUME> install -dev iris-fume-plugin
```
*Please refer to: https://github.com/intersystems/ipm/issues/434#issuecomment-1864512242 in case of the error: "Object open failed because 'Name' key value of 'iris-fume-plugin' was not found"*

> Installer Options
1. Confirm or change the active namespace used for a Plugin installation.
2. If a running Production found, the installer will ask your confirmation to add new components to existing Production. Otherwise a new Production will be created.
3. The installer will propose the new FHIR repository creation and configuration. Please confirm if required.
4. The installer will propose a default endpoint. Please confirm or change. 
5. Proivde FUME REST endpoint URL.
6. Proivde FUME Designer URL.

Installation Completed! 

> Post-installation steps

1. Check if IRIS FUME plugin components were added to your active production. You should see the following:

![Alt text](img/production.png)
 
2. Check if a CSP application (Web UI) at URL `http://<iris_host>:<iris_port>/csp/healthshare/<namespace>/fume/index.html` is available
3.	Finally, don’t forget to switch ZPM back to the community repository:

```shell
zpm:FUME> repo -r -n registry -reset-defaults
```
> Uninstallation

```shell
zpm:FUME: uninstall iris-fume-plugin
```

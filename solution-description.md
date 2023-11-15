## General solution description

The **InterSystems FUME plugin** is a specialized IRIS production whose primary goal is to effectively convert incoming messages in HL7 V2, CSV, and JSON formats to FHIR using a seamlessly integrated Outburn FUME Conversion engine. 

The **FUME** is available in two versions: **Community and Enterprise**. The IRIS plugin supports both of them. The table below represents the main differences between them:





The FUME conversion and transformation engine Community Edition can be downloaded from the Outburn GitHub repository: [https://github.com/Outburn-IL/fume-community]
The FUME 

The general data workflow is represented in the diagram below:

![Alt text](img/Fume-plugin-dataflow.png)

The  IRIS production accepts a message over the exposed REST endpoint (default method)  and passes the message to the Intersystems FUME  plugin Business Service. Intersystems FUME plugin forwards a message to the FUME engine REST API along with the conversion map. The conversion map selection depends on the deployed workflow on site and supports various configurations, starting from static FUME conversion map configuration for each incoming message up to complex Routing Rules configuration supported by FUME Plugin HL7 V2 Web UI. The FUME service transforms the data and returns an FHIR resource (or a collection of separate FHIR resources packed into an FHIR Bundle, depending on the conversion map) to IRIS production. Finally, IRIS production submits FHIR data to the FHIR Server (internal IRIS FHIR repository or external FHIR Server) according to the pre-defined rules based on the FHIR resource type.

> The InterSystems FUME plugin comprised the following main features and default modules:

1. ZPM package installer supporting various platforms, implementation scenarios, and configuration options.
2. IRIS FUME Plugin Rest Service supporting source messages accepting in the following formats: JSON,CSV,HL7 V2.
3. IRIS FUME Plugin HTTP Business Service supporting source messages accepting  in the following formats: JSON,CSV,HL7 V2
4. FUMETransformOperation Business Operation class allowing "One click" based  FUME integration and conversion map configuration from the Production           Configuration page. 
5. FUMEStoreOperation Business Operation class allows the interaction with the FHIR Server (internal IRIS FHIR  repository or external FHIR Server) and provides automatic REST call construction depending on the FHIR resource type/structure received from FUME. 
6. FUMEBusinessProcess allows entire solution workflow management according to the business requirements. The BP is capable of managing FUME conversion map calls in addition or instead of FUMETransformOperation, registration of additional components, and coordination of the data flow.
7. FUME plugin Web-based UI, allowing HL7 V2 to FHIR conversion management by configuring specially designed, FUME-based routing rules






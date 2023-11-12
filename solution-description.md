## General solution description

The **Intersystems FUME plugin** is a specialized IRIS production whose primary goal is to effectively convert incoming messages in HL7 V2, CSV, and JSON formats to FHIR using a seamlessly integrated FUME Conversion engine. 
The general data workflow is represented in the diagram below:

![Alt text](img/Fume-plugin-dataflow.png)

The  IRIS production accepts a message over the exposed REST endpoint (default method)  and passes the message to the Intersystems FUME  plugin Business Service. Intersystems FUME plugin forwards a message to the exposed FUME engine REST API along with the conversion map (for more information about the Outburn FUME conversion engine, please review FUME documentation). The conversion map selection depends on the deployed workflow on site and supports various configurations, starting from static FUME conversion map configuration for each incoming message up to complex Routing Rules configuration supported by FUME Plugin HL7 V2 Web UI. The FUME service transforms the data and returns an FHIR resource (or a collection of separate FHIR resources packed into an FHIR Bundle, depending on the conversion map) to IRIS production. Finally, IRIS production submits FHIR data to the FHIR Server (internal IRIS FHIR repository or external FHIR Server) according to the pre-defined rules based on the FHIR resource type.

The 

			1. Wizard-based ZPM package installer supports various platforms, implementation scenarios, and configuration options.
			2. FUME call  global settings configurable from IRIS production configuration
			3. IRIS FUME Plugin Rest Service supporting source messages accepting  in the following formats: JSON,CSV,HL7 V2
			4. IRIS FUME Plugin HTTP Business Service supporting source messages accepting  in the following formats: JSON,CSV,HL7 V2
			5. FUMETransformOperation Business Operation class allowing "One click" based  FUME integration and conversion map configuration from Production           Configuration page.
			6. FUMEStoreOperation Business Operation class allows the interaction with the FHIR Server (internal IRIS FHIR  repository or external FHIR Server) and provides automatic REST call construction depending on the FHIR resource type/structure received from FUME. 
			7. FUMEBusinessProcess allowing entire solution workflow management according to the business requirements. The BP is capable to manage FUME conversion maps calls in addition or instead of FUMETransformOperation, registration of additional components and coordination of the data flow. 
			8. Wen Interface allowing HL7 V2 conversion management (improved functionality from the first plugin version)






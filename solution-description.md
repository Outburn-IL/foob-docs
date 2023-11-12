## General solution description

The **Intersystems FUME plugin** is a specialized IRIS production whose primary goal is to effectively convert incoming messages in HL7 V2, CSV, and JSON formats to FHIR using a seamlessly integrated FUME Conversion engine. 
The general data workflow is represented in the diagram below:

![Alt text](img/Fume-plugin-dataflow.png)

The  IRIS production accepts a message over the exposed REST endpoint and passes the message to the Intersystems FUME  plugin Business Service. Intersystems FUME plugin forwards a message to the exposed FUME engine REST API along with the conversion map (for more information about the Outburn FUME conversion engine, please review FUME documentation). The conversion map selection depends on the deployed workflow on site and supports various configurations, starting from static FUME conversion map configuration for each incoming message up to complex Routing Rules configuration supported by FUME Plugin HL7 V2 Web UI. The FUME service transforms the data and returns an FHIR resource (or a collection of separate FHIR resources packed into an FHIR Bundle, depending on the conversion map) to IRIS production. Finally, IRIS production submits FHIR data to the FHIR Server (internal IRIS FHIR repository or external FHIR Server) according to the pre-defined rules based on the FHIR resource type.

The high-level architecture is shown in the diagram below:





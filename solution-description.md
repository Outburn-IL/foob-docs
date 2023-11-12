## General solution description

The **Intersystems FUME plugin** is a specialized IRIS production whose primary goal is to effectively convert incoming messages in HL7 V2, CSV, and JSON formats to FHIR using a seamlessly integrated FUME Conversion engine. 
The general workflow diagram is represented in the diagram below:

![Alt text](img/Fume-plugin-dataflow.png)

The  IRIS production accepts a message over the exposed REST endpoint and passes the message to the Intersystems FUME  plugin Business Service. Intersystems FUME plugin forwards a message to an instance of FUME service along with the conversion map (for further information, please review FUME documentation). The  FUME service transforms data and returns an FHIR resource (or a collection of separate FHIR resources packed in an FHIR Bundle, depending on the conversion map) to IRIS production. Finally, IRIS production submits FHIR data to its internal storage.



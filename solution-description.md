## General solution description

The **Intersystems FUME plugin** is a specialized IRIS production whose primary goal is to effectively convert incoming messages in HL7 V2, CSV, and JSON formats to FHIR using a seamlessly integrated FUME Conversion engine. 
The general workflow is the following IRIS production accepts a message and passes the message to the IRIS FUME plugin. IRIS FUME plugin forwards a message to an instance of FUME service. FUME service transforms data and returns an FHIR resource (or a collection of separate FHIR resources packed in an FHIR Bundle) to IRIS production. Finally, IRIS production submits FHIR data to its internal storage.

**InterSystems IRIS** exposes the following core components: 

* FHIR repository
* FHIR endpoint
* IRIS production 

**IRIS FHIR storage** is a high-performance database designed for effective FHIR data querying and processing. 

**IRIS FHIR endpoint** is a secured web service that implements FHIR REST API and acts as a service layer between FHIR storage for external clients. 

Finally, **IRIS production** is a business-process engine that manages medical application business logic. It is an integration framework for easily connecting systems and developing interoperability applications. The production provides built-in connections to various message formats and communications protocols. You can easily add other formats and protocols – and define business logic and message transformations by coding or using graphic wizards. Productions provide persistent storage of messages, allowing you to trace a message's path and audit whether a message is successfully delivered. A production consists of business services, processes, and operations.

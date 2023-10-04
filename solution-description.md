## General solution description

**InterSystems IRIS** exposes the following core components: 

* FHIR storage
* FHIR endpoint
* IRIS production. 

**IRIS FHIR storage** is a high-performance database designed for effective FHIR data querying and processing. 

**IRIS FHIR endpoint** is a secured web service which implements FHIR REST API and acts as a service layer between FHIR storage for external clients. 

Finally, **IRIS production** is a business-process engine which manages medical application business logic. It is an integration framework for easily connecting systems and for developing applications for interoperability. Production provides built-in connections to a wide variety of message formats and communications protocols. You can easily add other formats and protocols – and define business logic and message transformations either by coding or using graphic wizards. Productions provide persistent storage of messages, which allow you to trace the path of a message and audit whether a message is successfully delivered. A production consists of business services, processes, and operations.

Generally, **IRIS FUME plugin** is just a highly specialized IRIS production, which primary goal is to effectively convert incoming messages in HL7 v2, CSV and JSON formats to FHIR. IRIS production accepts a message and passes the message to IRIS FUME plugin. IRIS FUME plugin forwards message to an instance of FUME service. FUME service performs data transformation and returns a FHIR resource (or a collection of separate FHIR resources packed in a FHIR Bundle) as a result to IRIS production. Finally, IRIS production submits FHIR data to its own internal storage.

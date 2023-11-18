## IRIS FUME HL7v2 plugin


IRIS FUME HL7v2 plugin is a web application that runs on the InterSystems IRIS web server. The application allows users to design and test HL7v2 to FHIR conversion using IRIS FUME Plugin integrated with FUME.

The application is available at the following URL:
* /csp/healthshare/{namespace}/fume/index.html

Here, the {namespace} variable should match your namespace (e.g. /csp/healthshare/clinic1/fume/index.html)

The plugin comprised the following modules:

### FUME Designer
Link to the FUME designer (applicable for FUME Enterprise versions only).

### HL7v2 Routing Rules Editor
This module aimed to configure the **routing rules** between source HL7v2 messages and the FUME conversion map.
The routing rules call the appropriate map based on the logical expressions identifying each source message. The expression syntax is based on the FLASH - FUME map language and provides broad flexibility for setting any logical condition. The target is to build expression which will uniquely identify the incoming message.

As an example, the following expression: 
'MSH.SendingApplication.NamespaceID='VitalSignsDevice''

will identify the following HL7v2 message:


The rule set is created once for each incoming source message type and can be reused as often as needed.

Before using the editor, you must develop and register a few FUME maps using the FUME designer. 

**To design a new HL7v2 routing rule**

![IRIS FUME plugin routing rules editor](img/routing-rules-editor.png)

* In the `Source data` text box, type or paste the source HL7 v2 message from the clipboard or load the message from your hard drive using the Load button. 
* Click the `Convert to JSON button` to transform your HL7 message to its JSON representation
* In the `Rule name` text box, specify the name of the mapping rule
* In the `Rule priority` text box, set a numeric value that specifies the rule priority for an algorithm that sorts rules. If a message matches several rules, the rule with the lowest priority value will be applied to transform the message
* Using the `FUME map` dropdown list, select the FUME mapping which should be used to convert data
* In the `Rule expression` text box, enter a FLASH expression that takes your HL7v2 message represented in JSON format as input and returns a boolean value. If the expression returns true, the message will be converted to FHIR format using the FUME map specified in the previous field. Otherwise, if the message does not match the expression, it will be rejected. 
* To test your FLASH expression, click the `Validate rule` button
* To save the rule to the IRIS database, click the `Save` button
 
**To edit an existing HL7v2 routing rule:**

* Navigate to a list of routing rules in the bottom part of the page
* Select a rule you want to edit
•	Click the `Edit` button
•	Modify rule settings (rule name, rule priority, rule expression, and others)
•	Click the `Save` button to apply changes

[Applying FUME mappings to incoming data streams](/configuration.md#applying-fume-mappings-to-incoming-data-streams)

### IRIS FUME Plugin HL7 conversion tester

This page allows a user to perform online testing of FUME HL7v2 mappings and IRIS FUME plugin HL7v2 routing rules.

![Alt text](img/conversion-tester.png)
 
To perform testing, follow these steps:
* Click the `HL7 Conversion tester` main menu item
* Paste the source HL7v2 message from the clipboard into the upper text box. Alternatively, click the `Load...` button to load the message from your hard disk
* Click the `Convert` button to upload your test data to the IRIS server
* The transformation results will be displayed in the bottom pane of the page.

## IRIS FUME plugin HL7 v2 routing rules editor

IRIS FUME Plugin routing rules editor is a web application that runs on the InterSystems IRIS web server. The application allows users to design and test their own medical data conversion and routing rules for the FUME service on the InterSystems IRIS platform.

![IRIS FUME plugin routing rules editor](img/routing-rules-editor.png)
 
Before using the editor, you must develop and register some mappings using the FUME designer. 

In current release, the editor supports HL7 v2 and JSON formats.

**To design a new HL7v2 routing rule:**

* In the `Source data` text box, type or paste source message from the clipboard, or load a file using the Load button
* If you are working with an HL7 v2 message, click the `Convert to JSON button` to transform your HL7 message to its JSON representation
* In the `Rule name` text box, specify the name of the rule
* In the `Rule priority` text box, set a numeric value which defines the order for an algorithm, which sorts rules according to priority.
* Using the `FUME map` dropdown list, select the FUME mapping which should be used to convert data
* In the `Rule expression` text box, enter a Jsonata expression that takes your JSON message as input and returns a boolean value. If the expression returns true, the message will be converted to FHIR format using the FUME map specified in the previous field. Otherwise, if the message does not match the expression, it will be rejected. 
* To test your Jsonata expression, click the `Validate rule` button
* To save the rule to the IRIS database, click the `Save` button
 
**To edit an existing HL7v2 routing rule:**

* Navigate to a list of routing rules in the bottom part of the page
* Select a rule you want to edit
•	Click the `Edit` button
•	Modify rule settings (rule name, rule priority, rule expression and others)
•	Click the `Save` button to apply changes

## IRIS FUME Plugin conversion tester

This is another web application which allows a user to perform online testing of FUME mappings and IRIS routing rules.

![Alt text](img/conversion-tester.png)
 
In order to perform testing, follow these steps:
* Open the main page of the IRIS FUME Plugin client application
* Click the `Conversion tester` main menu item
* Choose which data conversion you want to test (HL7 v2, JSON or CSV)
* Paste the source data from the clipboard into the upper text box. Alternatively, click the `Load...` button to load a file from your hard disk
* Click the `Convert` button to upload your test data to the IRIS server
* The results of the transformation will be displayed in the bottom pane of the page.

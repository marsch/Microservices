# Communication Router

An execution of an integration flow is always started by the 1st step of the flow, the so called `trigger`. A trigger
component used to monitor changes in the source system and start the flow upon detecting any changes. The detection of
changes may occur in active or passive way, depending on the trigger type:

* polling trigger: actively monitoring the source service in predefined intervals
* webhook trigger: waiting for the source system to send notification about changes

In order to receive webhook requests, an integration flow with a webhook trigger need to be accessible from internet
over HTTPS.
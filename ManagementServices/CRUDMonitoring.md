# CRUD Monitoring

# Introduction

This document describes the evaluation of the Microservice "CRUD Monitoring".
This microservice is part of the integration services of the Open Integration Hub.

# Description

## Purpose of the Microservice CRUD Monitoring

This microservice is part of the "Smart Data Framework Services". With the "CRUD Monitoring" the baseline operations create, read, update and delete will be supervised.

## Requirements for the Integration Content Repository

Within the Open Integration Hub we have to consider how we are fulfilling the following tasks:

- In the case of a CRUD-event decide, how the Open Integration Hub has to work with the data,
- and which components have to be informed by the event
- and how to deal with upcoming conflicts.

The microservice CRUD Monitoring works inside the "Smart Data Framework" as a kind of supervisor. The smart data framework supports data synchronization by providing multiple domain models and by capturing relations between data objects within all kinds of integration flows. Therefore the CRUD Monitoring has to get in contact with every data operation inside the SDF.

# Technology Used

For monitoring the crud operations we consider to use "Logstash". Logstash is a tool to collect, parse and store logs and events. It reads the logs via so called inputs, parses, aggregates and filters with the help of filters and stores by outputs.

# Concept of the Integration Content Repository

The microservice is functioning as a log relay. The system must transport these logs and save them reliably and effectively to ensure that no data is lost. The storage system should allow the possibility of scaling out when there is a need for storing large volumes of data.

Logstash extracts the monitored data with event processing. This process consists of three stages: Input, then filtering and at last the output.

In the input stage Logstash gets the data from the source. Upon receiving events from an input, Logstash performs an action based on the conditional filter, which means it will transformed from unstructured to structured data. In the output stage, the structured data is sent to multiple outputs.

With the conditional filtering within Logstash we will be able to inform other endpoints. Therefore we have do define the rules for filtering.

The structured data can be sent to message processing services.

In summary we will have an incoming queue with all the input from a message broker, this will transferred to Logstash and we will get an output to the messaging services.

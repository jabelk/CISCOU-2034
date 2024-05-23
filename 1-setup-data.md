https://docs.splunk.com/Documentation/Splunk/9.2.1/Installation/StartSplunkforthefirsttime

$SPLUNK_HOME/bin/splunk start --accept-license

set up login if you haven't already

https://docs.splunk.com/Documentation/Splunk/9.2.1/Installation/ReadytostartusingSplunk

### Getting Data in First cloud then enterprise

https://docs.splunk.com/Documentation/Splunk/9.2.1/Data/WhatSplunkcanmonitor
What data can I index?
The Splunk platform can index any kind of data. In particular, the Splunk platform can index any and all IT streaming, machine, and historical data, such as Microsoft Windows event logs, web server logs, live application logs, network feeds, metrics, change monitoring, message queues, archive files, and so on.

#### Types of data sources in Splunk Cloud Platform

Splunk Cloud Platform provides tools to configure many kinds of data inputs, including those that are specific to particular application needs. Splunk Cloud Platform also provides the tools to configure any arbitrary data input types. In general, you can categorize Splunk Cloud Platform inputs as follows:

- Files and directories
- Network events
- Windows sources
- HTTP Event Collector (HEC)
- Metrics
- Files and directories

### Types of data sources in Splunk Enterprise

Because Splunk Enterprise is on-premises, you can either get data into the instance directly or use universal or heavy forwarders to get data in. In general, you can categorize Splunk Enterprise inputs as follows:

- Files and directories
- Network events
- Windows data
- Other sources
- Files and directories

### Understand your needs

https://docs.splunk.com/Documentation/Splunk/9.2.1/Data/Getstartedwithgettingdatain

### Use forwarders to get data in ENT

Splunk forwarders consume data and send it to an indexer. Forwarders require minimal resources and have little impact on performance, so they can usually reside on the machines where the data originates.

For example, if you have a number of Apache Web servers that generate data that you want to search centrally, you can set up forwarders on the Apache hosts. The forwarders take the Apache data and send it to your Splunk Enterprise deployment for indexing, which consolidates, stores, and makes the data available for searching. Because of their reduced resource footprint, forwarders have a minimal performance impact on the Apache servers.

Similarly, you can install forwarders on your employees' Windows desktops. These forwarders can send logs and other data to your Splunk Enterprise deployment, where you can view the data as a whole to track malware or other issues.

What forwarders do
Forwarders get data from remote machines. Unlike raw network feeds, forwarders have the following capabilities:

Tag metadata (source, sourcetype, and host)
Buffer data
Compress data
Use SSL security
Use any available network ports
Run scripted inputs locally
Forwarders usually do not index the data, but instead, forward the data to a Splunk Enterprise deployment that does the indexing and searching. A Splunk Enterprise deployment can process data that comes from many forwarders. For detailed information on forwarders, see the Forwarding Data or Universal Forwarder manuals.

In most Splunk Enterprise deployments, forwarders serve as the primary consumers of data. In a large Splunk Enterprise deployment, you might have hundreds or even thousands of forwarders that consume data and forward for consolidation.

https://docs.splunk.com/Documentation/Splunk/9.2.1/Data/Usingforwardingagents
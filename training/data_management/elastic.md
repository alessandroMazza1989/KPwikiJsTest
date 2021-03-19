---
title: Elastic
description: 
published: true
date: 2021-03-19T11:00:30.284Z
tags: 
editor: markdown
dateCreated: 2021-03-17T13:24:58.693Z
---

# Elastic Stack
## **Goals**
1. Install and configure the Elastic Stack (Elasticsearch, Kibana, Logstash, Beats) components
2. Implement an ETL flow using the Elastic Stack
	 a) Beats => Elasticsearch ( Using Elasticsearch Ingest Pipelines )
   b) Beats => Logstash => Elasticsearch ( Using Logstash Pipelines )
3. Gather data from different data sources outside the Elastic Stack
4. Use basic Ruby programming language to implement advanced data enrichment 
5. Advanced configuration in Elastic Stack:
	 a) Configure Security and Data Encryption
   b) Configure Kibana Multi Tenancy
   c) Configure Hot-Warm-Cold Architecture
   d) Configure the data lifecycle policy using ILM (Index Lifecycle Management)
   e) Configure data types and index settings using mappings and index templates
6. Use Kibana to visualize data

- *Useful Links*
  [**Elastic Free Training**](https://www.elastic.co/training/)
  [**Elastic Official Youtube Channel**](https://www.youtube.com/channel/UCIy5GtVvLEiLik0T2bZwm7g)
  [**Elastic Documentation**](https://www.elastic.co/guide/index.html)
  [**Elastic Discuss Forum**](https://discuss.elastic.co/)
  [**Elastic Videos&Webinar**](https://www.elastic.co/videos/)
  
  

## Training Path ( 20 work days )

1. Elastic Stack Overview:
   Install and run [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/targz.html)    and [Kibana](https://www.elastic.co/guide/en/kibana/current/targz.html) from tar.gz archive in single node    mode using the default configuration and navigate Kibana exploring the sample data. ( 1 day )
2. Regex and Grok patterns:
   Understanding what the [Regular Expressions](https://blog.chalda.it/guida-alla-sintassi-delle-espressioni-regolari-217.html#gruppi ) (RegEx) are and understand their implementaion in [Grok](https://grokdebug.herokuapp.com/patterns#) patterns used both in Logstash and Elasticsearch ( 1.5 day )
3. Basic ETL using Beats and Logstash:
   Understanding of what a [ETL](https://www.youtube.com/watch?v=a5C-Bw8y9gM) (Extract Transform Load) flow is. Understanding of what a [Logstash](https://www.elastic.co/guide/en/logstash/current/getting-started-with-logstash.html) pipeline is and basic tests with Grok filter plugin. Overview of [Elastic Beats](https://www.elastic.co/guide/en/beats/libbeat/current/beats-reference.html) and [Elastic Agent](https://www.elastic.co/guide/en/fleet/current/index.html). Use of [Filebeat](https://www.elastic.co/guide/en/beats/filebeat/current/index.html) to ingest data from log files and using Logstash to parse data and send them to Elasticsearch.
   ( 2 day )
4. Basic Kibana usage:
Overview of [Kibana](https://www.elastic.co/guide/en/kibana/current/introduction.html). Creation of an [index pattern](https://www.elastic.co/guide/en/kibana/current/index-patterns.html) to search data. Overview of the basic visualization and basic [Dashboard building](https://www.elastic.co/guide/en/kibana/current/dashboard.html). ( 1 day )
- Video Resources [Getting started with Kibana](https://www.elastic.co/webinars/getting-started-kibana)
   
5. Test (ETL + Visualization):
Implement an ETL flow Filebeat->Logstash->Elasticsearch and visualize data on Kibana dashboard; using new filter plugins. This tests the previously studied concepts and the ability to search in the docs for new features. ( 3 day )
6. Logstash Level Up ( Server configuration, Advanced plugins):
   ( 1.5 day )
7. Kibana Level Up ( Server configuration, Kibana features ):
   ( 1 day )
8. Elasticsearch Server Configuration:
   ( 1 day )
9. Elastic Advanced Features:
   ( 3 day )
10. Configuring Security in Elastic:
   ( 2 day )
11. Configure Alerts in Elastic:
    ( 1 day )
11. Observability with Elastic:
   ( 0.5 day )
12. Opensource Plugins Overview:
   ( 1 day )
13. Elastic Alternatives Overview:
   ( 0.5 day )
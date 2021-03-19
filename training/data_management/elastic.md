---
title: Elastic
description: 
published: true
date: 2021-03-19T12:06:35.236Z
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
Deepen knowledge of Logstash server [configuration files](https://www.elastic.co/guide/en/logstash/current/config-setting-files.html) expecially [logstash.yml](https://www.elastic.co/guide/en/logstash/current/logstash-settings-file.html) file for advanced configuration. Run logstash in background. Run logstash using the pipelines.yml file.
Overview of all logstash plugins ([input](https://www.elastic.co/guide/en/logstash/current/input-plugins.html), [filter](https://www.elastic.co/guide/en/logstash/current/filter-plugins.html), [output](https://www.elastic.co/guide/en/logstash/current/output-plugins.html)) deepen on the ones used previously in the training for advanced use. (1.5 day)
7. Kibana Level Up ( Server configuration, Kibana features ):
Overview of Kibana Server configuration file ([kibana.yml](https://www.elastic.co/guide/en/kibana/current/settings.html)). Understanding of the most important Kibana features ([Spaces](https://www.elastic.co/guide/en/kibana/current/xpack-spaces.html),[Field Management](https://www.elastic.co/guide/en/kibana/current/managing-fields.html),[Saved Objects](https://www.elastic.co/guide/en/kibana/current/managing-saved-objects.html)). Run Kibana in background. Advanced visualizations tools. (2 day)
- Video resources [Kibana Dashboards Level-up](https://www.elastic.co/webinars/kibana-dashboards-level-up) | [Introduction to Kibana Spaces](https://www.elastic.co/webinars/kibana-security-access-management-spaces-and-feature-controls)
8. Elasticsearch Server Configuration:
Deepen Elasticsearch server configuration ([elasticsearch.yml](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup.html)) to start Elasticsearch in not-trivial mode (e.g. change the binding host and port, change the data and logs location, change the JVM heap).
Start Elasticsearch in cluster mode using 3 AWS EC2 instances ([here](https://drive.google.com/file/d/1EyC2Br9khxiKPMtYSPxTXRPuc7V_kqJh/view?usp=sharing) the guide to set up the environment). (3 day)
9. Elastic Advanced Features:
Understanding of [Index settings](https://www.elastic.co/guide/en/elasticsearch/reference/current/index-modules.html) configuration to control the resource usage and the [Mappings](https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping.html) to handle data types. Understanding of what an [Ingest Pipeline](https://www.elastic.co/guide/en/elasticsearch/reference/current/ingest.html) is and the difference with a Logstash pipeline. Understanding of [ILM](https://www.elastic.co/guide/en/elasticsearch/reference/current/index-lifecycle-management.html)(Index Lifecycle Policy) to handle time based retetion of data. Usage of [Index templates](https://www.elastic.co/guide/en/elasticsearch/reference/current/index-templates.html) to automatically configure the previous feature for an index. (3 day)
10. Querying data in Elasticsearch:
Basic CRUD operations in Elasticsearch([Create](https://www.elastic.co/guide/en/elasticsearch/reference/current/docs-index_.html),[Read](https://www.elastic.co/guide/en/elasticsearch/reference/current/docs-get.html),[Update](https://www.elastic.co/guide/en/elasticsearch/reference/current/docs-update.html),[Delete](https://www.elastic.co/guide/en/elasticsearch/reference/current/docs-delete.html)).
[Query DSL](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl.html)(Domain Specific Language) for Elasticsearch data, focusing on: [Full Text queries](https://www.elastic.co/guide/en/elasticsearch/reference/current/full-text-queries.html), [Term-level queries](https://www.elastic.co/guide/en/elasticsearch/reference/current/term-level-queries.html) and [Bool compound queries](https://www.elastic.co/guide/en/elasticsearch/reference/current/query-dsl-bool-query.html) usage.
Understand [Aggregations](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations.html) and [nested](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations.html#run-sub-aggs) aggregations; understanding the difference between Bucket, Metrics and Pipeline aggregation. Overview of the available aggregations for each type focusing on: [Terms](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-bucket-terms-aggregation.html), [Date Histogram](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-bucket-datehistogram-aggregation.html), [Histogram](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-bucket-histogram-aggregation.html), [Range](https://www.elastic.co/guide/en/elasticsearch/reference/current/search-aggregations-bucket-range-aggregation.html). (2 day)
11. Configuring Security in Elastic:
(2 day)
12. Configure Alerts in Elastic:
(1 day)
13. Opensource Plugins Overview:
(1 day)
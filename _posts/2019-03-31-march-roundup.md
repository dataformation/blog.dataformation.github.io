---
layout:     post
title:      "March Roundup"
subtitle:   "Curated summary of interesting articles from the world of mobile and data"
date:       2019-03-31 12:00:00
author:     "DataFormation"
header-img: "img/post-bg-01.jpg"
tags: []
---

<h2 class="section-heading">BigQuery Storage API Promoted to Beta</h2>

*Google Cloud, BigQuery, Apache Beam*{: style="color: gray"}


The <a href="https://beam.apache.org/documentation/io/built-in/google-bigquery/#storage-api">BigQuery Storage API</a> unifies 
the data warehouse and storage by providing a fast export of data using 
multiple streams that may be consumed by a multithreaded or distributed recipient. It is 
much faster than the existing alternatives of bulk export to file or paginated access using the BigQuery client APIs.

The key features are:
 * Multiple streams for fast read access.
 * A subset of columns may be selected to be read, further increasing performance.
 * Simple filtering of data to be read before sending to the client.
 * Snapshot consistency---data is read from a specific point in time.

In addition, the Apache Beam BigQueryIO connector (starting with version 2.11) supports <a href="https://beam.apache.org/documentation/io/built-in/google-bigquery/#storage-api">reading using the BigQuery Storage API</a>. 
This is a good example of how the BigQuery Storage API can work in combination with a distributed processing framework.

This video from <a href="https://youtu.be/8UuiJjTW12Y?t=1527">Google Next</a> provides more information about the storage API and demonstrates the performance benefits.

<h2 class="section-heading">Apache Beam SQL</h2>

*Apache Beam, Beam SQL*{: style="color: gray"}

A review of the new Apache <a href="https://medium.com/weareservian/exploring-beam-sql-on-google-cloud-platform-b6c77f9b4af4
">Beam SQL</a> feature that allows SQL to be injected in 
the pipeline.




<!--<a href="#">-->
<!-- <img src="{{ site.baseurl }}/img/post-sample-image.jpg" alt="Post Sample Image"> -->
<!--</a>-->
<!--<span class="caption text-muted">To go places and do things that have never been done before – that’s what living is all about.</span>-->


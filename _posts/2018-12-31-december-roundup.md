---
layout:     post
title:      "December Roundup"
subtitle:   "Curated summary of interesting articles from the world of mobile and data"
date:       2018-12-31 12:00:00
author:     "DataFormation"
header-img: "img/post-bg-01.jpg"
tags: [BigQuery, Apache Beam, Dataflow, Google Cloud]
---

<h2 class="section-heading">Google Cloud 2018</h2>

*Google Cloud*{: style="color: gray"}

A completely uncurated list of every <a href="https://cloud.google.com/blog/products/gcp/every-gcp-blog-post-2018">Google Cloud</a> blog post from 2018.



<h2 class="section-heading">Beam BigQuery annotation</h2>

*Dataflow, Apache Beam, BigQuery*{: style="color: gray"}

Interacting with BigQuery from Apache Beam/Dataflow requires use of the <code><a href="https://developers.google.com/resources/api-libraries/documentation/bigquery/v2/java/latest/com/google/api/services/bigquery/model/TableRow.html?is-external=true" target="_blank">TableRow</a></code> class from the Google
API client libraries to read/write data field by field, as well managing table schemas when writing data. The
<a href="https://medium.com/windfalldata/bigquery-utilities-for-apache-beam-1b6153fd1a9d">BigQuery Utilities</a> library
from Windfall Data provides a workflow to streamline this process. Perhaps the most valuable benefit of this library is that
 it reduces the risk of annoying and potentially time consuming mistakes when managing BigQuery schema definitions.

The <code>@BigQueryColumn</code> annotation is used to define the table schema. Schema modifications introduced when the annotation
usage is changed are handled by the library. The library also provides a transform to read or write data, avoiding the boilerplate
associated with <code>TableRow</code>. Collections are handled and mapped to repeated columns.

See the <a href="https://github.com/WindfallData/beam-bigquery-utils">github repo</a> for more.

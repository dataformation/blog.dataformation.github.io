---
layout:     post
title:      "November Roundup"
subtitle:   "Curated summary of interesting articles from the world of mobile and data"
date:       2018-11-25 12:00:00
author:     "DataFormation"
header-img: "img/post-bg-01.jpg"
tags: [BigQuery, GIS, Android, Robolectric, AndroidX, unit testing, automated testing]
---

<h2 class="section-heading">Geospatial Functions for BigQuery</h2>

*BigQuery, GIS*{: style="color: gray"}

<a href="https://cloud.google.com/blog/products/data-analytics/whats-happening-bigquery-new-ingest-format-data-type-updates-ml-and-query-scheduling">Geospatial functions for BigQuery</a>
has been placed in beta release, along with a web query result visualisation tool called
<a href="https://cloud.google.com/bigquery/docs/gis-visualize">BigQuery Geo Viz</a>.

Some new <a href="https://cloud.google.com/blog/products/data-analytics/expanding-our-public-datasets-geospatial-and-ml-based-analytics">public data sets</a>
have also been announced to help users with their geospatial analysis. The current
data sets are focused on the United States, but the free storage
tiers for public data sets provide an incentive for other organizations to share public
datasets using BigQuery.

This product video by Google demonstrates an example of using BigQuery GIS to
<a href="https://www.youtube.com/watch?v=V6D_qE00qEE">identify suitable retail locations using zip code data</a>.

<h2 class="section-heading">BigQuery Scheduled Queries</h2>

*BigQuery*{: style="color: gray"}

Until now it was necessary to write your own query and output code using a client library of the BigQuery CLI and then
schedule this to run using <a href="https://cloud.google.com/blog/products/gcp/scheduling-dataflow-pipelines-using-app-engine-cron-service-or-cloud-functions">Google Cloud cron jobs (AppEngine)</a>,
<a href="https://cloud.google.com/composer/">Cloud Composer</a> (Apache Airflow), or local cron
jobs jobs that initiate queries using the BigQuery command line.

<a href="https://cloud.google.com/bigquery/docs/scheduling-queries">BigQuery Scheduled Queries</a> now offers a simple way to execute a scheduled
query without the complexity of the other solutions.

Notifications of query completions may be posted to <a href="https://cloud.google.com/pubsub/">Google Cloud PubSub</a>,
allowing subsequent processing to be performed by any service that can process PubSub data. For example, the query completion
notification might be a trigger for a Cloud Function.

At present the scheduled query must be created using the web interface. Hopefully this
is extended to allow programmatic creation for a solid operational solution that allows automated creation of environments.

<h2 class="section-heading">Serverless Data Aggregation with Firebase</h2>

*Firestore, Dataflow, Apache Beam, Cloud PubSub, Cloud Functions*{: style="color: gray"}

Here is a nice <a href="https://medium.com/evenbit/aggregate-thousands-of-inputs-per-second-with-firebase-76111212b850">serverless architecture for aggregating a high rate of inputs and publishing the results quickly</a>.
It makes use of Cloud Firestore, Cloud Functions, Cloud Pub/Sub, and Cloud Dataflow (Apache Beam). It is well suited for use in mobile applications. The
example used is a game where thousands of players are producing inputs to the game state simultaneously. As it uses Cloud Firestore, it is
straightforward to send input data from iOS or Android apps, websites, or applications written in a variety of languages.

The data pipeline is structured as follows:
 1. The data sources (e.g. Android and iOS apps) write to a new Firestore document for each data entry. This avoids contention over
 updating a single document and updates can be written at a rate that is essentially unlimited.
 1. Firestore provides the ability to trigger a Cloud Functions for each document write. The cloud function will send a message to
 a Cloud Pub/Sub topic.
 1. A streaming Cloud Dataflow job then reads each Pub/Sub message, performs the desired aggregation across a time window and then
 publishes the result to another Pub/Sub topic. The results could also be saved to BigQuery or file on Cloud Storage at this stage.
 1. A second cloud function is triggered of the Pub/Sub results messages and writes the results to Firestore. The Firestore change
 listening client functions can then be used to display the changes in the client applications asynchronously as each new aggregation update is published.


<h2 class="section-heading">Robolectric 4</h2>

*Android, Robolectric, AndroidX, unit testing, automated testing*{: style="color: gray"}


<a href="http://robolectric.org/">Robolectric</a> is an excellent open source tool that simplifies Android
automated testing. <a href="http://robolectric.org/blog/2018/10/25/robolectric-4-0/">Robolectric 4</a> takes
that a step further and brings tighter integration with the new repackaged AndroidX test framework. This includes
the ability to use the AndroidX test runner to launch a test that uses the Robolectric as well as adopting the Android binary
resource processing chain, instead of Robolectric’s own method.

Recent Google Android testing presentations have also discussed Robolectric, assuring its position as a key tool for Android unit testing.


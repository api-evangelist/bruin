---
title: "What Is Impact Analysis for a Schema Change? Finding What Breaks Before You Rename a Column"
url: "https://getbruin.com/blog/what-is-impact-analysis-for-a-schema-change/"
date: "2026-09-25"
author: "Kateryna Kozachenko"
feed_url: "https://getbruin.com/rss.xml"
---
Impact analysis is the step before a schema change where you find every model, check, dashboard, and consumer that depends on the column or table you are about to alter. This explainer covers why it needs column-level lineage rather than table-level, how to run it from the command line with Bruin, and what dbt, Airflow, and catalog tools give you instead.

---
title: "What Is Pipelines as Code? Managing Data Pipelines Like Software"
url: "https://getbruin.com/blog/what-is-pipelines-as-code/"
date: "2026-09-01"
author: "Kateryna Kozachenko"
feed_url: "https://getbruin.com/rss.xml"
---
Pipelines as code means every part of a data pipeline, the loads, the SQL and Python transformations, the quality checks, the schedule, lives as files in a git repository, is validated on every pull request, and is deployed on merge. This explainer covers what belongs in the repository, the two CI jobs that make it work, and how Bruin, dbt, and Dagster implement it.

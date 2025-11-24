---
title: Add to Uninterception List (GET)
excerpt: >-
  Add email address or receiving domain to the uninterception list. apiUserName
  defaults to "all" if empty; domainName and email cannot be empty at the same
  time. Duplicate data (judged by apiUserName+domainName or apiUserName+email)
  will not be added repeatedly; filling both domainName and email splits into
  two records.
api:
  file: unintercepyion.yaml
  operationId: add-uninterception-get
hidden: false
---
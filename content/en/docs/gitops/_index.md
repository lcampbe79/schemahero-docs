---
date: 2019-09-16
linktitle: "GitOps"
title: GitOps
weight: 60000
---

SchemaHero is designed to enable [GitOps](https://www.weave.works/technologies/gitops/) for database schema migrations. While it works great when deploying into an existing GitOps workflow (such as a cluster with [Weave Flux](https://www.weave.works/oss/flux/) or [ArgoCD](https://argoproj.github.io/argo-cd/getting_started/)), not every cluster has this setup.

SchemaHero is a GitOps operator and can be configured to monitor a Git repo for updated schemas.


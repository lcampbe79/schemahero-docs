---
date: 2019-09-16
linktitle: "Plans"
title: Publishing Pre-Deployment Plans
weight: 60020
---

In addition to gitops deployments, SchemaHero can write plans to a pull request, when using GitHub. This feature requires GitHub Actions to be available on the GitOps repo.

To enable planning, add a `isPlanEnabled` attribute to the `gitops` key:

```yaml
apiVersion: databases.schemahero.io/v1alpha2
kind: Database
metadata:
  name: my-database
gitops:
  url: git@github.com:my-org-name/my-gitops-repo.git
  isPlanEnabled: true
connection:
  postgres:
    uri:
      valueFrom:
        secretKeyRef:
          name: postgresql-secret
          key: uri
```
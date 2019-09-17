---
date: 2019-09-16
linktitle: "Configuring"
title: Configuring Built-In GitOps
weight: 60010
---

To use the built-in GitOps pipeline, add the configuration to the [Datanase](/docs/connecting-databases/creating-db-resource/) object. 

Add the `gitops` key to a database object, as in:

```yaml
apiVersion: databases.schemahero.io/v1alpha2
kind: Database
metadata:
  name: my-database
gitops:
  url: git@github.com:my-org-name/my-gitops-repo.git
connection:
  postgres:
    uri:
      valueFrom:
        secretKeyRef:
          name: postgresql-secret
          key: uri
```

When this is deployed, SchemaHero will create a deploy key and write the public key to it's own log. This deploy key should be added to the repo, and it should have read/write access.

SchemaHero will wait for the deploy key to be added. No steps are necessary to restart or reload the configuration once the key is created.

If you already have a key, you can also use that. Create a secret with the name of the database, and two fields:

```yaml

```
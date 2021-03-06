---
date: 2019-05-25
linktitle: "Image Tags"
title: Image Tags
weight: 20020
---

SchemaHero builds and uses 2 different container images:

`schemahero/schemahero` and `schemahero/schemahero-manager`.

The `schemahero-manager` image is the Kubernetes CRD controller and manager. It runs in the cluster and handles the reconciliation of any deployed custom resources. When a database or table custom resource is deployed, the code to connect to and monitor the connection is in the schemahero container. Both of these container images are built from this repo.

There are several reasons for this separation:

1. It's possible to run schemahero as a binary, outside of Kubernetes. As covered later in these docs, this is useful in testing and dev environments when creating fixtures.
2. This separation enables SchemaHero to work in tightly controlled environments where it might not be possible to connect to the database from any pod on any node in the cluster. SchemaHero supports Kubernetes `nodeSelector` attribute at the database connection level, allowing the `schemahero-manager` to manage multiple databases.

The two images are tagged and released at the same time, using the same versioning system

## Alpha

There is an `:alpha` tag of these iamges. This is the latest commit to master. This has the latest code, but also may have some issues. It's not recommended to use the `:alpha` tag in production.

## Latest

There is no `:latest` tag. Docker defaults to the `latest` tag, and this is clear what the expectation of pulling this tag is. SchemaHero chooses to not publish an image on this tag.

## major.minor.patch

The `:x.y.z` tag points to a specific, immutable revision. These are created when a tag is pushed. These are the most stable versions of SchemaHero and recommended to use in production.


---
layout: post
date: 2020-10-18
tags:
- OpenShift
- Registry
- Red Hat
---

## Pulling images from Red Hat Registry

>
> Tested in OpenShift 3.11 Version
> 

[Red Hat Registry](https://catalog.redhat.com/software/containers/explore) is an authenticated images registry
to provide the latest official and supported images of the Red Hat products. These images are available
with a valid subscription, as enterprise customer or as Developer, and it is needed to provided the
right credentials to pull images from there.

First at all you need a valid token to pull images. You could create a new one from the
[Registry Service Accounts](https://access.redhat.com/terms-based-registry/) as an OpenShift Secret
to install in your platform.

To install it:

```bash
❯ oc create -f cdk-3-secret.yaml 
secret/cdk-3-pull-secret created
```

Finally you need to link that secret to the ```default``` and ```builder``` service
accounts to pull images:

```bash
❯ oc secrets link default cdk-3-pull-secret --for=pull
❯ oc secrets link builder cdk-3-pull-secret
```

Now you can import an image as:

```bash
❯ oc import-image dotnet-31-jenkins-agent-rhel7 --from=registry.redhat.io/dotnet/dotnet-31-jenkins-agent-rhel7 --confirm
```

### References

* [Red Hat Container Registry Authentication](https://access.redhat.com/RegistryAuthentication)

* * *

[OpenShift Knowledge Base](./)
[Knowledge Base](../)

---
layout: default
---

## Activate Round Robin OCP Routes

>
> Tested in OpenShift 3.11 Version
> 

Disabling cookies:

```bash
❯ oc annotate routes <ROUTE_NAME> haproxy.router.openshift.io/disable_cookies='true'
```

Defining *Round Robin* balance strategy:

```bash
❯ oc annotate routes <ROUTE_NAME> haproxy.router.openshift.io/balance='roundrobin'
```

### References

* [How to disable sticky session for a specific route in Red Hat OpenShift Container Platform 3](https://access.redhat.com/solutions/4820731)
* [OpenShift 3.11 - Sticky Sessions](https://docs.openshift.com/container-platform/3.11/architecture/networking/routes.html#routes-sticky-sessions)
* [OpenShift 3.11 - Load Balancing Strategy](https://docs.openshift.com/container-platform/3.11/architecture/networking/routes.html#load-balancing)

* * *

[OpenShift Knowledge Base](/openshift)

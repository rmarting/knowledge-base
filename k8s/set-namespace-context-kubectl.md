---
layout: post
date: 2020-10-18
tags:
- Kubernetes
- kubectl
- how-to
---

## Set namespace context in kubectl

You could permanently save the namespace for all subsequent ```kubectl``` commands in that context:

```bash
❯ kubectl config set-context --current --namespace=my-namespace
```

* * *

[Kubernetes Knowledge Base](./)
[Knowledge Base](../)

# Kayla Soraya Djakaria - 2306256381

## Reflection on Hello Minikube
1. Comparing the application logs before and after exposing it as a Service

Before I hit the app through the Service (or proxy), the only log lines in my Pod were the two startup messages:

![](img/image1a.png)

Once I exposed the Deployment as a Service, each time I opened or refreshed the app in my browser I saw exactly one new “GET /” entry in the logs. For example, after two page-loads I saw:

![](img/image1b.png)

If I refresh a third time, there’s a third “GET /” line, and so on. In other words, every HTTP request forwarded through the Service produces one log entry, and the total number of “GET /” lines grows in step with the number of times I open the app.


2. Purpose of the `-n` option

![](img/image2.png)
The `-n` (or `--namespace`) flag tells kubectl which Kubernetes namespace to operate in. By default, if you don’t supply `-n`, kubectl acts on the “default” namespace. When you run:

```bash
kubectl get pods,services
```

you see the Pods and Services you created (e.g. your `hello-node` Deployment) because they live in the “default” namespace.

When you run:

```bash
kubectl get pods,services -n kube-system
```

you switch context into the `kube-system` namespace, which is where Kubernetes itself runs its core components.
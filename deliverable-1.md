# Deliverable 1.5

```bash
>kubectl get po -n online-boutique
NAME                                     READY   STATUS    RESTARTS   AGE
adservice-b8c99885b-nl898                2/2     Running   0          73s
cartservice-65c987d449-4ghfb             2/2     Running   2          73s
checkoutservice-8bddb89db-rqt6s          2/2     Running   0          74s
currencyservice-7978fb77d8-t5f9j         2/2     Running   0          73s
emailservice-8848674-q2fc7               2/2     Running   0          74s
frontend-58594bf684-s6c46                2/2     Running   0          74s
paymentservice-77979f5c66-js4gs          2/2     Running   0          74s
productcatalogservice-7d5f94d858-dkmsl   2/2     Running   0          74s
recommendationservice-764dc66688-mwsdj   2/2     Running   0          74s
redis-cart-74594bd569-vdbgc              2/2     Running   0          73s
shippingservice-589dc45c5d-9h868         2/2     Running   0          73s
```

```bash
>istioctl verify-install
1 Istio control planes detected, checking --revision "default" only
✔ Deployment: istio-ingressgateway.istio-system checked successfully
✔ PodDisruptionBudget: istio-ingressgateway.istio-system checked successfully
✔ Role: istio-ingressgateway-sds.istio-system checked successfully
✔ RoleBinding: istio-ingressgateway-sds.istio-system checked successfully
✔ Service: istio-ingressgateway.istio-system checked successfully
✔ ServiceAccount: istio-ingressgateway-service-account.istio-system checked successfully
✔ Deployment: istio-egressgateway.istio-system checked successfully
✔ PodDisruptionBudget: istio-egressgateway.istio-system checked successfully
✔ Role: istio-egressgateway-sds.istio-system checked successfully
✔ RoleBinding: istio-egressgateway-sds.istio-system checked successfully
✔ Service: istio-egressgateway.istio-system checked successfully
✔ ServiceAccount: istio-egressgateway-service-account.istio-system checked successfully
✔ ClusterRole: istiod-istio-system.istio-system checked successfully
✔ ClusterRole: istio-reader-istio-system.istio-system checked successfully
✔ ClusterRoleBinding: istio-reader-istio-system.istio-system checked successfully
✔ ClusterRoleBinding: istiod-istio-system.istio-system checked successfully
✔ Role: istiod-istio-system.istio-system checked successfully
✔ RoleBinding: istiod-istio-system.istio-system checked successfully
✔ ServiceAccount: istio-reader-service-account.istio-system checked successfully
✔ ServiceAccount: istiod-service-account.istio-system checked successfully
✔ ValidatingWebhookConfiguration: istiod-istio-system.istio-system checked successfully
✔ CustomResourceDefinition: destinationrules.networking.istio.io.istio-system checked successfully
✔ CustomResourceDefinition: envoyfilters.networking.istio.io.istio-system checked successfully
✔ CustomResourceDefinition: gateways.networking.istio.io.istio-system checked successfully
✔ CustomResourceDefinition: serviceentries.networking.istio.io.istio-system checked successfully
✔ CustomResourceDefinition: sidecars.networking.istio.io.istio-system checked successfully
✔ CustomResourceDefinition: virtualservices.networking.istio.io.istio-system checked successfully
✔ CustomResourceDefinition: workloadentries.networking.istio.io.istio-system checked successfully
✔ CustomResourceDefinition: workloadgroups.networking.istio.io.istio-system checked successfully
✔ CustomResourceDefinition: authorizationpolicies.security.istio.io.istio-system checked successfully
✔ CustomResourceDefinition: peerauthentications.security.istio.io.istio-system checked successfully
✔ CustomResourceDefinition: requestauthentications.security.istio.io.istio-system checked successfully
✔ CustomResourceDefinition: istiooperators.install.istio.io.istio-system checked successfully
✔ ConfigMap: istio.istio-system checked successfully
✔ Deployment: istiod.istio-system checked successfully
✔ ConfigMap: istio-sidecar-injector.istio-system checked successfully
✔ MutatingWebhookConfiguration: istio-sidecar-injector.istio-system checked successfully
✔ PodDisruptionBudget: istiod.istio-system checked successfully
✔ Service: istiod.istio-system checked successfully
✔ EnvoyFilter: metadata-exchange-1.8.istio-system checked successfully
✔ EnvoyFilter: tcp-metadata-exchange-1.8.istio-system checked successfully
✔ EnvoyFilter: stats-filter-1.8.istio-system checked successfully
✔ EnvoyFilter: tcp-stats-filter-1.8.istio-system checked successfully
✔ EnvoyFilter: metadata-exchange-1.9.istio-system checked successfully
✔ EnvoyFilter: tcp-metadata-exchange-1.9.istio-system checked successfully
✔ EnvoyFilter: stats-filter-1.9.istio-system checked successfully
✔ EnvoyFilter: tcp-stats-filter-1.9.istio-system checked successfully
Checked 12 custom resource definitions
Checked 3 Istio Deployments
✔ Istio is installed and verified successfully
```

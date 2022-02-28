# Deliverable 6

## Scale frontend deployment to 2

```bash
>kapp scale --replicas=2 deploy/frontend
deployment.apps/frontend scaled

>kapp get deploy frontend
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
frontend   2/2     2            2           28d
```

## Endpoint configuration

- We now see 2 pod addresses: 172.17.0.7:8080 & 172.17.0.9:8080

```json
istioctl proxy-config endpoints $INGRESS_POD.istio-system --cluster 'outbound|8000||frontend.online-boutique.svc.cluster.local' -o json
[
    {
        "name": "outbound|8000||frontend.online-boutique.svc.cluster.local",
        "addedViaApi": true,
        "hostStatuses": [
            {
                "address": {
                    "socketAddress": {
                        "address": "172.17.0.7", // 1st Replica
                        "portValue": 8080
                    }
                },
                "stats": [
                    {
                        "name": "cx_connect_fail"
                    },
                    {
                        "name": "cx_total"
                    },
                    {
                        "name": "rq_error"
                    },
                    {
                        "name": "rq_success"
                    },
                    {
                        "name": "rq_timeout"
                    },
                    {
                        "name": "rq_total"
                    },
                    {
                        "type": "GAUGE",
                        "name": "cx_active"
                    },
                    {
                        "type": "GAUGE",
                        "name": "rq_active"
                    }
                ],
                "healthStatus": {
                    "edsHealthStatus": "HEALTHY"
                },
                "weight": 1,
                "locality": {}
            },
            {
                "address": {
                    "socketAddress": {
                        "address": "172.17.0.9", // 2nd Replica
                        "portValue": 8080
                    }
                },
                "stats": [
                    {
                        "name": "cx_connect_fail"
                    },
                    {
                        "name": "cx_total"
                    },
                    {
                        "name": "rq_error"
                    },
                    {
                        "name": "rq_success"
                    },
                    {
                        "name": "rq_timeout"
                    },
                    {
                        "name": "rq_total"
                    },
                    {
                        "type": "GAUGE",
                        "name": "cx_active"
                    },
                    {
                        "type": "GAUGE",
                        "name": "rq_active"
                    }
                ],
                "healthStatus": {
                    "edsHealthStatus": "HEALTHY"
                },
                "weight": 1,
                "locality": {}
            }
        ],
        "circuitBreakers": {
            "thresholds": [
                {
                    "maxConnections": 4294967295,
                    "maxPendingRequests": 4294967295,
                    "maxRequests": 4294967295,
                    "maxRetries": 4294967295
                },
                {
                    "priority": "HIGH",
                    "maxConnections": 1024,
                    "maxPendingRequests": 1024,
                    "maxRequests": 1024,
                    "maxRetries": 3
                }
            ]
        }
    }
]
```

- We can validate this further by checking the kubernetes service configuration

```yaml
kapp describe svc frontend
Name:              frontend
Namespace:         online-boutique
Labels:            <none>
Annotations:       <none>
Selector:          app=frontend
Type:              ClusterIP
IP Families:       <none>
IP:                10.102.124.135
IPs:               10.102.124.135
Port:              http  8000/TCP
TargetPort:        8080/TCP
Endpoints:         172.17.0.7:8080,172.17.0.9:8080
Session Affinity:  None
Events:            <none>
```

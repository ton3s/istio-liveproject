# Deliverable 2.4

- As seen below, the request to `/wrongpath` is being proxied by the ingress gateway and forwarded to the frontend service. This is due to the virtualservice configured to send all http traffic to the front end.

```json
// Ingress gateway
> kubectl -n istio-system logs -l app=istio-ingressgateway | jq
{
  "start_time": "2022-01-31T02:41:48.989Z",
  "duration": 1,
  "downstream_remote_address": "172.17.0.1:59628",
  "requested_server_name": null,
  "bytes_sent": 19,
  "upstream_cluster": "outbound|80||frontend.online-boutique.svc.cluster.local",
  "upstream_service_time": "1",
  "protocol": "HTTP/1.1",
  "user_agent": "curl/7.64.1",
  "connection_termination_details": null,
  "x_forwarded_for": "172.17.0.1",
  "upstream_host": "172.17.0.9:8080",
  "authority": "10.97.52.39",
  "bytes_received": 0,
  "response_code": 404,
  "upstream_transport_failure_reason": null,
  "downstream_local_address": "172.17.0.5:8080",
  "route_name": null,
  "response_code_details": "via_upstream",
  "upstream_local_address": "172.17.0.5:47488",
  "request_id": "e9e25141-5f8e-9c24-b553-d32a3d05108d",
  "response_flags": "-",
  "path": "/wrongpath",
  "method": "GET"
}

// frontend
> kubectl -n online-boutique logs -l app=frontend  -c istio-proxy | jq
{
  "requested_server_name": "outbound_.80_._.frontend.online-boutique.svc.cluster.local",
  "response_code": 404,
  "duration": 0,
  "connection_termination_details": null,
  "upstream_service_time": "0",
  "upstream_local_address": "127.0.0.1:44790",
  "upstream_cluster": "inbound|8080||",
  "downstream_local_address": "172.17.0.9:8080",
  "x_forwarded_for": "172.17.0.1",
  "method": "GET",
  "user_agent": "curl/7.64.1",
  "request_id": "e9e25141-5f8e-9c24-b553-d32a3d05108d",
  "downstream_remote_address": "172.17.0.1:0",
  "route_name": "default",
  "bytes_received": 0,
  "response_code_details": "via_upstream",
  "start_time": "2022-01-31T02:41:48.990Z",
  "upstream_host": "127.0.0.1:8080",
  "path": "/wrongpath",
  "bytes_sent": 19,
  "response_flags": "-",
  "protocol": "HTTP/1.1",
  "authority": "10.97.52.39",
  "upstream_transport_failure_reason": null
}
```

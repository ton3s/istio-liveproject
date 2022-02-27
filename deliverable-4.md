# Deliverable 4

```yaml
kubectl apply -n istio-system -f - << EOF
apiVersion: "security.istio.io/v1beta1"
kind: "AuthorizationPolicy"
metadata:
  name: online-boutique
  namespace: istio-system
spec:
  selector:
    matchLabels:
      istio: ingressgateway
  action: DENY
  rules:
  - when:
    - key: "request.auth.audiences"
      notValues: ["boutiquestore.com"]
    to:
    - operation:
        paths: ["/cart"]
        ports: ["8443"]
---
EOF
```

## Successful test: request to `/cart` at 443

```bash
curl -v -H "Authorization: Bearer $VALID_TOKEN" \
  --write-out "%{http_code}" -o /dev/null \
  -H "host: marketplace.boutiquestore.com" \
  --cacert root.crt \
  --resolve "marketplace.boutiquestore.com:443:$INGRESS" \
  "https://marketplace.boutiquestore.com:443/cart"

* Connection #0 to host marketplace.boutiquestore.com left intact
200%
```

### Failed test: request to`/cart` at 443 without a JWT

```bash
❯ curl -v \
  --write-out "%{http_code}" -o /dev/null \
  -H "host: marketplace.boutiquestore.com" \
  --cacert root.crt \
  --resolve "marketplace.boutiquestore.com:443:$INGRESS" \
  "https://marketplace.boutiquestore.com:443/cart"
* Added marketplace.boutiquestore.com:443:10.97.52.39 to DNS cache
* Hostname marketplace.boutiquestore.com was found in DNS cache
*   Trying 10.97.52.39:443...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to marketplace.boutiquestore.com (10.97.52.39) port 443 (#0)
* ALPN, offering h2
* ALPN, offering http/1.1
* successfully set certificate verify locations:
*  CAfile: root.crt
*  CApath: none
* TLSv1.2 (OUT), TLS handshake, Client hello (1):
} [243 bytes data]
* TLSv1.2 (IN), TLS handshake, Server hello (2):
{ [96 bytes data]
* TLSv1.2 (IN), TLS handshake, Certificate (11):
{ [764 bytes data]
* TLSv1.2 (IN), TLS handshake, Server key exchange (12):
{ [300 bytes data]
* TLSv1.2 (IN), TLS handshake, Server finished (14):
{ [4 bytes data]
* TLSv1.2 (OUT), TLS handshake, Client key exchange (16):
} [37 bytes data]
* TLSv1.2 (OUT), TLS change cipher, Change cipher spec (1):
} [1 bytes data]
* TLSv1.2 (OUT), TLS handshake, Finished (20):
} [16 bytes data]
* TLSv1.2 (IN), TLS change cipher, Change cipher spec (1):
{ [1 bytes data]
* TLSv1.2 (IN), TLS handshake, Finished (20):
{ [16 bytes data]
* SSL connection using TLSv1.2 / ECDHE-RSA-CHACHA20-POLY1305
* ALPN, server accepted to use h2
* Server certificate:
*  subject: CN=marketplace.boutiquestore.com; O=boutique store
*  start date: Jan 31 22:49:07 2022 GMT
*  expire date: Jan 31 22:49:07 2023 GMT
*  common name: marketplace.boutiquestore.com (matched)
*  issuer: O=boutiquestore Inc.; CN=boutiquestore.com
*  SSL certificate verify ok.
* Using HTTP2, server supports multi-use
* Connection state changed (HTTP/2 confirmed)
* Copying HTTP/2 data in stream buffer to connection buffer after upgrade: len=0
* Using Stream ID: 1 (easy handle 0x7fcb1000e200)
> GET /cart HTTP/2
> Host: marketplace.boutiquestore.com
> user-agent: curl/7.77.0
> accept: */*
>
* Connection state changed (MAX_CONCURRENT_STREAMS == 2147483647)!
< HTTP/2 403
< content-length: 19
< content-type: text/plain
< date: Sun, 27 Feb 2022 19:50:04 GMT
< server: istio-envoy
<
{ [19 bytes data]
100    19  100    19    0     0   4060      0 --:--:-- --:--:-- --:--:--  4750
* Connection #0 to host marketplace.boutiquestore.com left intact
403%
```

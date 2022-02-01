# Deliverable 3.3

```
>openssl s_client -connect $INGRESS:443 -servername marketplace.boutiquestore.com -CAfile root.crt
CONNECTED(00000003)
depth=1 O = boutiquestore Inc., CN = boutiquestore.com
verify return:1
depth=0 CN = marketplace.boutiquestore.com, O = boutique store
verify return:1
---
Certificate chain
 0 s:/CN=marketplace.boutiquestore.com/O=boutique store
   i:/O=boutiquestore Inc./CN=boutiquestore.com
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIC7jCCAdYCAQAwDQYJKoZIhvcNAQEFBQAwOTEbMBkGA1UECgwSYm91dGlxdWVz
dG9yZSBJbmMuMRowGAYDVQQDDBFib3V0aXF1ZXN0b3JlLmNvbTAeFw0yMjAxMzEy
MjQ5MDdaFw0yMzAxMzEyMjQ5MDdaMEExJjAkBgNVBAMMHW1hcmtldHBsYWNlLmJv
dXRpcXVlc3RvcmUuY29tMRcwFQYDVQQKDA5ib3V0aXF1ZSBzdG9yZTCCASIwDQYJ
KoZIhvcNAQEBBQADggEPADCCAQoCggEBAOZ8PTfR8MO8X7OLyK113Hqd/N9tsc0A
LsegzVW0wLA5gfM+u7DhjAXO2Th0N9+0ytb8PA6gH8j95WahWyVS9/ofjs99licC
8E5kzPiCgRK6AsP9DqVPl9zylMkZtfjuoAYZsUS2QNS+EY+JBLUk3O2POc6P/04D
7lckrWMzwSoIuVdc0++uioZWDBgAwi11qq+lqeVB8kj67UojBwhvRyzU/mTzLvRa
h5s/5Vrt6WHnncoXq7xXBBCFsz1cYm0g2tTnbr62Ir7Ub3PqO6D33MJcNDzmOZUA
5cEG0WkiKfQNoDjvEPdmOa6kijCHTOGCD9CU2JIlxSvva+jMTVC40F8CAwEAATAN
BgkqhkiG9w0BAQUFAAOCAQEAlPhKbkDe5fG58lVGW0QkizYtYAMSNdNM3wafbm8d
UHjKmrji/6+rXwkFvtbz2aui1WIy7BjoK6b1NRrdTTyTI/MfBtq7tKUP4D9g/yDC
U3Pkd4u6XBM6YhhwU8tnfxVIf3LXMBFzb7u+JRtW2jUf5NzVA/24V0WiFyE956jX
7tceDSg7s4zD7J+g/5dZapU7PYrCiZ0fL6gO1iGVZPF8qu+oJHxmR6pLJUsqgMtt
wYN+4VFUeCwHf67P96DIAjQiqCudnhDUW9pILcVeTgnPD94ePL2FZay+l+pOMoEj
gZyS1nqPz/uZiMsXAT+otpZJ4W6SfxIKBsmcxQ3qJSvxow==
-----END CERTIFICATE-----
subject=/CN=marketplace.boutiquestore.com/O=boutique store
issuer=/O=boutiquestore Inc./CN=boutiquestore.com
---
No client certificate CA names sent
Server Temp Key: ECDH, X25519, 253 bits
---
SSL handshake has read 1397 bytes and written 319 bytes
---
New, TLSv1/SSLv3, Cipher is ECDHE-RSA-CHACHA20-POLY1305
Server public key is 2048 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : ECDHE-RSA-CHACHA20-POLY1305
    Session-ID: FF20EBE56BFB3A12C72FFE07C6118F70A318CB29DB583D6ED512BC3BA4CDED4B
    Session-ID-ctx:
    Master-Key: 8543DE4D701D57176F3E6D5E9097E80CD21A85E5728F9348735C35063EBEAF1BAFB4D8023C6ABA14E4870D90882616C2
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 22 f0 04 fe 12 aa 6b e5-46 67 5b b8 6d 0f 81 3b   ".....k.Fg[.m..;
    0010 - 24 5d e6 53 59 0d 68 2a-7f e0 d0 25 ec 7c 83 03   $].SY.h*...%.|..
    0020 - 6f c0 68 bf 3b c3 58 f7-68 04 b8 a0 eb 56 38 de   o.h.;.X.h....V8.
    0030 - c6 5b dd f2 9f 48 dc c3-ae f7 af cd f5 2b 44 8a   .[...H.......+D.
    0040 - 35 59 c9 5a 24 f1 46 c7-a7 3c c7 e2 dd 1e d3 09   5Y.Z$.F..<......
    0050 - 64 56 54 41 55 a4 40 87-62 13 fa 94 a7 fc 1c 07   dVTAU.@.b.......
    0060 - 66 6c fe bc 09 75 a6 1f-e4 1c 8d 7a c7 27 f2 32   fl...u.....z.'.2
    0070 - 8f 9b 47 83 f0 db b9 db-3d 4c 5a 4e fb 94 02 d5   ..G.....=LZN....
    0080 - cf 2d d2 95 a2 d2 19 85-ca f3 3b 50 6d 68 c1 98   .-........;Pmh..
    0090 - bc 7b 76 5f e6 46 c8 48-0e 7f de ba fc b5 28 fd   .{v_.F.H......(.
    00a0 - 5e 07 59 5b c4 73 f5 63-6e 8d e9 88 a7 b6 5e 42   ^.Y[.s.cn.....^B
    00b0 - ea 6f b8 e1 b6 88 a5 20-fa 24 64 fa db d7 b6 5d   .o..... .$d....]

    Start Time: 1643689633
    Timeout   : 7200 (sec)
    Verify return code: 0 (ok)
---
```

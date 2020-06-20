CFSSL-TLS
========================


## Initialize a CA

Before we can generate any certs we need to initialize a CA.

```
$ cfssl gencert -initca ca-csr.json | cfssljson -bare ca
```

### Generate Server and Client Certs

#### Client
```
cfssl gencert \
-ca=ca.pem \
-ca-key=ca-key.pem \
-config=ca-config.json \
-profile=client \
ca-csr.json | cfssljson -bare client
```

#### Server
```
cfssl gencert \
-ca=ca.pem \
-ca-key=ca-key.pem \
-config=ca-config.json \
-profile=server \
ca-csr.json | cfssljson -bare server
```
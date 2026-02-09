# SSL (Secure Socker Layer)/ TLS (Transport Layer Security)
- TLS is newer version of SSL
- HTTPs uses TLS for security.
- It's a Layer between application and [[tcp_udp|TCP]].
- Has three steps:
	1. Handshake
	2. Key derivation
	3. Data Transfer

## Handshake Explanation Packet by Packet

### Packet 1: client -> server
```
ClientHello
	Version: TLS 1.2
	Random: 3fa4c9...
	Cipher Suites:
		TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
		TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
	Extensions:
		server_name: example.com
```

- Random is use for calculating encryption keys
- Cipher Suites are the list of encryption algorithms client supports.
### Packet 2: server -> client
```
ServerHello
	Version: TLS 1.2
	Random: 91bd2e...
	Cipher Suite:
		TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
```

- Server selects one cipher suite from the list user sent to it.
### Packet 3: server -> client
```
Certificate
	Subject: CN=example.com
	Publick Key: RSA 2048-bit
	Signed by: DigiCert Intermediate CA
```

- Server sends it's certificates data to user
### Packet 4: server -> client
```
ServerKeyExchange
	ECDHE Public Key: 04a7c2...
	Signature: signed with server private key
```

- ECDHE used for calculating encryption key.
- With checking signature with CA client can make sure it is talking to the right server.
### Packet 5: server -> client
```
I'm Done
```
### Packet 6: client -> server
```
ClientKeyExchange
	ECDHE Publick Key: 049f31...
```
### Packet 7: client -> server
```
I'm done too, From next packet I will use encryption.
```
### Packet 8: client -> server
```
(Finished + hash of entire handshake so far) [encrypted]
```
### Packet 9: server -> client
```
I'm switching to encryption too.
```
### Packet 10: server -> client
```
(Finished + hash of entire handshake so far) [encrypted]
```

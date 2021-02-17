# Common tips & tricks

## OpenSSL
[The Most Common OpenSSL Commands](https://www.sslshopper.com/article-most-common-openssl-commands.html)

Generate a new private key and Certificate Signing Request
```
openssl req -out CSR.csr -new -newkey rsa:2048 -nodes -keyout privateKey.key
```

Generate a self-signed certificate
```
openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout privateKey.key -out certificate.crt
```

Generate a certificate signing request (CSR) for an existing private key
```
openssl req -out CSR.csr -key privateKey.key -new
```

Generate a certificate signing request based on an existing certificate
```
openssl x509 -x509toreq -in certificate.crt -out CSR.csr -signkey privateKey.key
```

Remove a passphrase from a private key
```
openssl rsa -in privateKey.pem -out newPrivateKey.pem
```

Check a Certificate Signing Request (CSR)
```
openssl req -text -noout -verify -in CSR.csr
```

Check a private key
```
openssl rsa -in privateKey.key -check
```

Check a certificate
```
openssl x509 -in certificate.crt -text -noout
```

Check a PKCS#12 file (.pfx or .p12)
```
openssl pkcs12 -info -in keyStore.p12
```

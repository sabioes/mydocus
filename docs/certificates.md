# Certificates

For full documentation visit [https://www.openssl.org/docs/](https://www.openssl.org/docs/).

## Commands

To get a certiificate from a domain using openssl and human readable format:
```bash
echo | openssl s_client -connect example.com:443 | openssl x509 -noout -text
```

Get the CA of certificate:
```bash
echo | openssl s_client -connect bootstrap-c01-smt-kafka-i.zeiss.org:443 -servername bootstrap-c01-smt-kafka-i.zeiss.org 2>/dev/null | openssl x509 -outform PEM
```

To get a certificate from a domain and save it to a file:
```bash
openssl s_client -connect your.kafka.broker:9093 -showcerts </dev/null
```


Create a truststore and import the certificate into it:
```bash
keytool -import -alias "your_alias" -file CA.pem -keystore truststore.jks -storepass changeit
```


Decrypt the pem file to file key.pem:
```bash
openssl pkcs8 -inform PEM -in key.pem -out key.pem 
```
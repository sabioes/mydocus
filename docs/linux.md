# Linux


## OpenSSL

To get the certificates chain of any domain. It is relevant when for example your company uses ZScaler as proxy: 
```bash
openssl s_client -showcerts -connect example.com:443 </dev/null
```
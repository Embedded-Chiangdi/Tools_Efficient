CA 根证书生成
```shell
# Generate CA private key 
openssl genrsa -out ca.key 2048 
# Generate CSR 
openssl req -new -key ca.key -out ca.csr
# Generate Self Signed certificate（CA 根证书）
openssl x509 -req -days 365 -in ca.csr -signkey ca.key -out ca.crt

mkdir demoCA
mkdir demoCA/newcerts
touch demoCA/index.txt
echo 01 > demoCA/serial
touch demoCA/index.txt.attr

# private key
openssl genrsa -des3 -out server.key 1024 
openssl genrsa  -out server.key 1024 
# generate csr
openssl req -new -key server.key -out server.csr
# generate certificate
openssl ca -in server.csr -out server.crt -cert ca.crt -keyfile ca.key -days 36500
```

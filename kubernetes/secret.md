# K8s Secret

# Create a secret
```shell
kubectl create secret generic db-user-pass \
  --from-file=./username.txt \
  --/rom-literal=password='S!B\*d$zDsb='
```
note: `--from-file` will create a secret value with filename as key field


# Get content of a secret
since GCP Console can't reveal secret value, you should use cli tool to get value

```shell
kubectl get secret db-user-pass -o jsonpath='{.data}'
```

note: secret is base64 encoded

# TLS secrets
a builtin Secret type `kubernetes.io/tls` for storing a certificate
create with command:
```shell
kubectl create secret tls my-tls-secret \
  --cert=path/to/cert/file \
  --key=path/to/key/file
```

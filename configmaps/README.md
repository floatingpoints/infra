# ConfigMap

## Create env

```bash
kubectl apply -f env-staging.yml
```

## Usefull command

```bash
echo -n bar | kubectl create configmap env --dry-run=client --from-env-file=.env -n time4games-staging -o yaml > env-staging.yml
```

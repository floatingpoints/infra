# infra

## Deploy Redis

```bash
kubectl apply -f redis/
```

## Deploy PostGis DB

```bash
kubectl apply -f postgis/
```

## Usefull command

```bash
echo -n bar | kubectl create configmap env --dry-run=client --from-env-file=.env -n some-namespace -o yaml > env-staging.yml
```

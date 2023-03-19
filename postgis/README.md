# Postgus k8s resources

## Sealed Secrets

```bash
export POSTGRES_PASSWORD=toBeReplaced
```

```bash
kubectl create secret generic --dry-run=client \
    postgis-env \
    --namespace=time4games-prod \
    --from-literal=POSTGRES_PASSWORD=$POSTGRES_PASSWORD \
    -o yaml \
    | kubeseal --format=yaml > env.sealed-secret.yaml
```

## Deplopy resources

```bash
kubectl apply -f .
```

## Adminer sealed secret

```bash
kubectl create secret generic --dry-run=client \
    postgis-basic-auth \
    --namespace=time4games-prod \
    --from-file=auth \
    -o yaml \
    | kubeseal --format=yaml > postgis-basic-auth.sealed-secret.yaml
```

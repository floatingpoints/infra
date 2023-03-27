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

## Adminer sealed secret

```bash
export AUTH_USER=toBeReplaced
export AUTH_PASSWORD=toBeReplaced
echo "${AUTH_USER}:$(openssl passwd -stdin -apr1 <<< ${AUTH_PASSWORD})" >> auth
kubectl create secret generic --dry-run=client \
    postgis-basic-auth \
    --namespace=time4games-prod \
    --from-file=auth \
    -o yaml \
    | kubeseal --format=yaml > 0.postgis-basic-auth.sealed-secret.yaml
```

## Deplopy resources

```bash
kubectl apply -f .
```

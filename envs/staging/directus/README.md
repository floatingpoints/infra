# Directus ENVs

## Create sealed env secret

```bash
echo -n bar | kubectl create secret generic directus-env --dry-run=client --from-env-file=.env -n time4games-staging -o yaml > secret.yml
kubeseal -o yaml < secret.yml > secret-env.yml
rm secret.yml
```

## Deploy configmap and secret env

```bash
kubectl apply -f .
```

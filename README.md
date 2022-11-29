# infra

## Secrets

Create a secret in k8s cluster for accessing the github registry (both staging and prod envs)

```bash
kubectl apply -f sealed-secrets/regcred-staging.yml
kubectl apply -f sealed-secrets/regcred-prod.yml
```

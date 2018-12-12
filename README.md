To run Grafana at it's cheapest - yes with possible downtime - execute the following command:

```
cat kubernetes.yaml | HOSTNAME=grafana.myserver.com ADMIN_PASSWORD=*** envsubst | kubectl apply -f -
```

If you want to change the admin password after initial setup you'll have to execute:

```
kubectl exec <grafana pod> -n grafana grafana-cli admin reset-admin-password ***
```
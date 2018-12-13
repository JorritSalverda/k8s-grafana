To run Grafana at it's cheapest - yes with possible downtime - execute the following command:

```
cat kubernetes.yaml | HOSTNAME=grafana.myserver.com ADMIN_PASSWORD=*** envsubst | kubectl apply -f -
```

If you want to change the admin password after initial setup you'll have to execute:

```
kubectl exec <grafana pod> -n grafana grafana-cli admin reset-admin-password ***
```

Check if everything's up and running with:

```
watch -n 2 kubectl get svc,ing,deploy,po,cm,secret,pdb,hpa,ep,pvc -l app=grafana -n grafana
```

Access the service via port-forwarding:

```
kubectl port-forward svc/grafana -n grafana 3000:80
```

And open `http://127.0.0.1:3000/` to see your grafna instance.
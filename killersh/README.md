# CKAD scratch
Spolier alert, these examples are from the CKAD simulator practice exam.

- `vim ~/.vimrc`
```
set expandtab
set tabstop=2
set shiftwidth=2
```

- 2 pods: 
```
k run --image=httpd:2.4.41-alpine $d -o yaml > p2.yaml
k apply -f p2.yaml
k get pod pod2 -o jsonpath="{.status.phase}"
```

- 3 
```
kubectl apply -f - <<EOF
apiVersion: v1
kind: Secret
metadata:
  name: neptune-sa-v2-secret
  namespace: neptune
  annotations:
    kubernetes.io/service-account.name: neptune-sa-v2
type: kubernetes.io/service-account-token
EOF
```

- 20
```
kubectl create deployment backend --image=nginx -n pluton
kubectl create deployment frontend --image=nginx -n pluton
kubectl expose deployment backend --port=80 -n pluton
kubectl expose deployment frontend --port=80 -n pluton

k -n pluton run tmp --restart=Never --rm -i --image=busybox -i -- wget -O- frontend:80

k -n pluton exec frontend-5d7445bdb8-dqcpf -- curl -v www.google.com

k -n pluton exec frontend-5d7445bdb8-dqcpf -- curl  www.google.com
```
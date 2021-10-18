# DevSecOps
- This Deployment file "hello-kubernetes.yaml" creates namespace "hello-kubernetes" and deploy "hello-kubernetes" application in it.
- "hello-kubernetes" application displays 
   * a default Hello world! message
   * namespace, pod, and node details
   * container image details
- created ClusterIP service.
- Execution steps:
  1. kubectl apply -f https://github.com/SwapnaliVKulkarni/DevSecOps/blob/main/hello-kubernetes.yaml
  (for os delimiter issue , need to copy the data from this link create yaml file and execute kubectl apply)

- Output with ClusterIP
------------------------------------------------------------------------
controlplane $ kubectl get all -n hello-kubernetes
NAME                                    READY   STATUS    RESTARTS   AGE
pod/hello-kubernetes-7c6b6df89f-bj2qz   1/1     Running   0          34s
pod/hello-kubernetes-7c6b6df89f-cs4gk   1/1     Running   0          34s

NAME                       TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
service/hello-kubernetes   ClusterIP   10.101.36.184   <none>        80/TCP    35s

NAME                               READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/hello-kubernetes   2/2     2            2           35s

NAME                                          DESIRED   CURRENT   READY   AGE
replicaset.apps/hello-kubernetes-7c6b6df89f   2         2         2       35s

--------------------------------------------------------------------------------
controlplane $ curl http://10.101.36.184:80
<!DOCTYPE html>
<html>
<head>
    <title>Hello Kubernetes!</title>
    <link rel="stylesheet" type="text/css" href="/css/main.css">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Ubuntu:300" >
</head>
<body>

  <div class="main">
    <img src="/images/kubernetes.png"/>
    <div class="content">
      <div id="message">
  Hello world!
</div>
<div id="info">
  <table>
    <tr>
      <th>namespace:</th>
      <td>-</td>
    </tr>
    <tr>
      <th>pod:</th>
      <td>hello-kubernetes-7c6b6df89f-bj2qz</td>
    </tr>
    <tr>
      <th>node:</th>
      <td>- (Linux 4.15.0-122-generic)</td>
    </tr>
  </table>
</div>
<div id="footer">
  paulbouwer/hello-kubernetes:1.10.1 (linux/amd64)
</div>
    </div>
  </div>
</body>
</html>

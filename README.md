# Kubernetes-Volume

<p>If one create a pod and there is a container , It will get volume. Somehow this running container stop it's working then a new container will be created to replace the old one . The newly created  container will get the same volume with same name. Actually the volume owner is pod not the container and that is the reason a new container get the same volume untill the pod is crashed. If the pod is crashed , then the volume will be deleted.Containers in same the pod can share each others volume </p><br />

---

<img src=".\image\k8s volume.drawio.png" width="200" height="100">

---

<h3>Some interesting point</h3>

<ol>

<li> Containers are short lived in nature </li>

<li> All data stored inside a container is deleted if the container crashed(this point is for only the general container, not for a container running in a pod) <br/>

However the kubelet will restart it eith a clean state, ehich means that it will not have any of the old data. </li>

</ol>

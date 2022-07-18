# Kubernetes-Volume

<p>If one create a pod and there is a container , It will get volume. Somehow this running container stop it's working then a new container will be created to replace the old one . The newly created  container will get the same volume with same name. Actually the volume owner is pod not the container and that is the reason a new container get the same volume untill the pod is crashed. If the pod is crashed , then the volume will be deleted.Containers in same the pod can share each others volume </p><br />

<img src=".\image\k8s volume.drawio.png" width="200" height="100">

---

<h3>Some interesting points</h3>

<ol>

<li> Containers are short lived in nature. </li>

<li> All data stored inside a container is deleted if the container crashed(this point is for only the general container, not for a container running in a pod) <br/>

However the kubelet will restart it eith a clean state, ehich means that it will not have any of the old data. </li>

<li> To overcome this problem, kubernetes uaes volume . A volume ia essentially a directory backed by a storage medium. The storage medium and it's contents are determined by the bvolume type.</li>

<li>In kubernetes , a volume is attached to a pod and shared among the containers of that pod.</li>

<li>The volume has the same life span as the pod and it outlives the containers of the pod. This allowes to be preserved container restarts . </li>

</ol>

---

<h3>Volume Types</h3>

A volume type decides the properties of the directory like size, context etc. <br/>

some example of volume types are:

<ol>

<li>node-local type such as emptydir and hostpath</li>

<li> File sharing types such as nfs ( network File system ) </li>

<li>Cloud provider-specific types like aws elastic storage azure disk. </li>

<li>Distributed file system types</li>

<li>Special purpose types like secret, gitrepo</li>

</ol>

---

<h2>Empty Dir </h2>

If somehow pod crashed then the volume attached to pod will get deleted and no data will be founded . After Crashed, the pod will recreates and new volume will reinitialize. The newly created volume will be empty and that is called empty dir.<br/ >

**\*\***some key points about Empty Dir**\***

<ol>

<li> Use this when we want to share contents between multiple containers on the same pod and no to the host machine. </li>

<li> AN empty Dir volume is firstcreates when a pod assign to a node and exist as long as that pod running on that node.</li>

<li>As the name says , it is initially empty.</li>

<li>Containers in the pod can all read and write the same files in the empty dir volume,  through that volume can be mounted at the same or different paths in each containers.</li>

<li> When a pod is removed from a node for any reason, the data in the empty dir is deleted forever.</li>

<li>A  container crashing does not remove a pod from a node, so the data in a empty dir volume is safe across container crashes. </li>

<li></li>

## </ol>

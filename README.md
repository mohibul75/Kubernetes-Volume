# Kubernetes-Volume

    If one create a pod and there is a container , It will get volume. Somehow this running container stop it's working then a new container will be created to replace the old one . The newly created  container will get the same volume with same name. Actually the volume owner is pod not the container and that is the reason a new container get the same volume untill the pod is crashed. If the pod is crashed , then the volume will be deleted. <br />



    <img src="\image\k8s volume.drawio.png" width="200" height="100">

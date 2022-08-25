# neuvector

LAB para a palestra do Devops Experience - 25/08/2022

Parte 1 vamos instalar o DOCKER e posteriormente o RANCHER em um servidor Linux.

Sistema Operacional: UBUNTU SERVER V:20.04

SCRIPT DE INSTALACAO DO DOCKER NO UBUNTU 20.04
$ curl https://releases.rancher.com/install-docker/20.10.sh | sh 
$ sudo usermod -aG docker ubuntu

INSTALAR O RANCHER NO UBUNTU 20.04
$ docker run -d --restart=unless-stopped \
>   -p 80:80 -p 443:443 \
>   --privileged \
>   rancher/rancher:latest

INSTALAR O KUBECTL NO UBUNTU 20.04
$ sudo apt-get update && sudo apt-get install -y apt-transport-https gnupg2
$ curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
$ echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee -a /etc/apt/sources.list.d/kubernetes.list
$ sudo apt-get update
$ sudo apt-get install -y kubectl

COMO  CONFIGURAR AS CREDENCIAIS DO KUBECTL 
$  mkdir -p .kube
$ cd .kube
$ vim config
$ colar o conteudo do arquivo Kubeconfig, salvar o arquivo.
$ kubectl get nodes

SUBIR UMA APLICAÇÃO MARIADB
(use esse comando para definir a senha do root com a "MARIADB_ROOT_PASSWORD" variável de ambiente)
$ kubectl run mariadb-test-pod --image=mariadb --env="MARIADB_ROOT_PASSWORD=secret"

(iniciando o client e fazendo uma consulta)
$ kubectl exec -it mariadb-test-pod -- mariadb -uroot -psecret -e "select current_user()"

(consultando os logs da aplicação)
$ kubectl logs mariadb-test-pod



Parte 2 vamos instalar o KUBERNETES em outro servidor Linux.

SCRIPT DE INSTALACAO DO DOCKER NO UBUNTU 20.04
$ curl https://releases.rancher.com/install-docker/20.10.sh | sh 
$ sudo usermod -aG docker ubuntu

COMO  INSTALAR O KUBERNETES COM 1 COMANDO NO UBUNTU 20.04
$ Só viu quem estava na palestra #AGUARDA_O_DEVOPS_HEROES_SOLTAR_NO_YOUTUBE hehehehe









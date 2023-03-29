# Kubernetes(k8s)

複数のコンテナを効率的に管理するソフトウエア。  
コンテナに対するCPUやメモリなどリソースの割り当て、DNSやポートの設定などのネットワーク、NFSなどのデータ保管に関するボリュームの設定など複数のサーバ・コンテナにまたがって設定するのが大変なものを一括でyamlファイルで設定できる。  
ただし、Kubernetesを構築・運用するのはそれなりのコストが発生する。  
基本的なLinuxサーバの運用の知識、ネットワークを構築・運用する知識、Kubernetesで利用する関連システムの知識など、幅広い知識を求められる。  
そのため、基本的には各クラウドベンダが提供するKubernetesのサービスもしくは、Red Hatが提供するOpenShift、VMwareが提供するTnazuなどを用いて、サポートがある状況で運用するほうが好ましい。  
また、このように各ベンダことにKubernetesのディストリビューションを作成しており、独自機能を有しているものも多い。  

## ディストリビューション

### オンプレミスで運用可能

* [公式](https://kubernetes.io/docs/setup/production-environment/tools/)
  Kubernetes公式のページに、複数の構築するツールやそのドキュメントについて説明されている。  
  基本的なKubernetesの構成について学びたい場合や、すべて自分たちでメンテナンスできるのであれば、最新のKubernetesを利用することができる。    

* [OpenShift](https://www.redhat.com/ja/technologies/cloud-computing/openshift)  
  Red Hatが提供するKubernetesを含む開発からCI/CD、運用までをパッケージング化した製品。  
  オンプレミスに導入する場合には検討する対象とする。  
  個人で使うにはオープンソース版([OKD](https://www.okd.io/))がある。  
  インストール自体は可能だが推奨されたリソースがかなり大きいため、個人で導入するには少しハードルが高い。  
  OpenShiftに必要なリソース要件は公式以外にもこちらの[ブログ記事](https://rheb.hatenablog.com/entry/2022/02/28/OpenShift%E3%81%AEMaster/Worker_Node%E3%81%AE%E3%82%A8%E3%83%83%E3%82%B8%E5%90%91%E3%81%91%E3%83%87%E3%83%97%E3%83%AD%E3%82%A4%E3%83%A1%E3%83%B3%E3%83%88%E3%81%AEHW%E6%9C%80%E5%B0%8F%E8%A6%81%E4%BB%B6)がわかりやすい  

* [Tanzu](https://tanzu.vmware.com/jp/tanzu)  
  VMware社が提供するKubernetesを含む開発からCI/CD、運用までをパッケージング化した製品。  
  VMware vSphereなどのVMware製品が導入済みの場合は検討する対象とする。  
  個人で使うにはコミュニティエディション([Tanzu Community Edition](https://tanzucommunityedition.io/))がある。  
  Dockerで運用する分には比較的簡単に導入でき、さらにクラスタも組みやすいためハードルは低い。  
  こちらの[ブログ記事](https://blogs.vmware.com/vmware-japan/2021/10/tanzu-community-edition-2.html)がわかりやすい。  

* [Rancher](https://www.rancher.com/)  
  Rancher社が提供するKubernetesの管理ツール  
  [RKE(Rancher Kubernetes Engine)](https://www.rancher.com/products/rke)として、Kubernetesを簡単にインストールすることができる。  
  OpenShiftやTanzuよりも容易にクラスタ構成を導入できるため、GUIでの管理があって個人で利用したい場合などに向く。  

* [MicroK8s](https://microk8s.io/)
  Canonical社が提供する軽量なKubernetes。  
  軽量化するため、etcdと呼ばれる機能ではなくdqliteを用いているなど、若干異なる機能を有しているが、ここで上げているすべてのKubernetesのディストリビューションの中で最も軽量である。  
  Ubuntuを利用しているのであれば、snapコマンドで簡単に導入できるうえ、クラスタ構成も10分とかからずできるので、個人で運用したい場合の選択肢としては非常に魅力的。  

### クラウド

* [EKS(Amazon Elastic Kubernetes Service)](https://aws.amazon.com/jp/eks/)  
  Amazonが提供しているKubernetes。  
  AWSを利用しているのであれば選択肢として挙がる。  
  ただし、EKSを選択する前に、以下の選択肢が取れないかは十分に検討する。  
  * ECS
  * AWS Lambda

* [GKE(Google Kubernetes Engine)](https://cloud.google.com/kubernetes-engine?hl=ja)  
  Googleが提供しているKubernetes。  
  Kubernetesの開発もとなので、クラウドベンダが提供しているKubernetesとしては更新が早かったりとメリットがある。  
  ただし、GKEを利用する前に、以下の選択肢が取れないかは十分に検討する。  
  * App Engine
  * Cloud Functions

* [AKS(Azure Kubernetes Service)](https://azure.microsoft.com/en-us/products/kubernetes-service)  
  Microsoftが提供しているKubernetes。  
  Azureを利用しているのであれば選択肢として挙がる。  
  ただし、AKSを選択する前に、以下の選択肢が取れないかは十分に検討する。  
  * Web Apps
  * Azure Container Instance

## Link

[https://kubernetes.io/](https://kubernetes.io/)



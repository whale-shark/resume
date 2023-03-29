# Octant/Lens

## 概要

Kubernetesの状況をGUIで管理する方法として、[公式のダッシュボード](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/)以外のツール。  
ここでは、kubeconfigファイルだけで動作するツールを選択している。  

* Octant  
  VMware Tanzu向けのWebダッシュボードだったが、アーカイブされてしまった。  

* Lens
  Kubernetes向けのインストール型のクライアントダッシュボード。  
  以下のissueにあるように、ログインが必須となってしまい、クローズドの環境では利用できない。  
  https://github.com/lensapp/lens/issues/5444  
  [OpenLens](https://github.com/MuhammedKalkan/OpenLens)として個人？の方がビルドしてくださっている。  

## Link

[https://octant.dev/](https://octant.dev/)

[https://k8slens.dev/](https://k8slens.dev/)

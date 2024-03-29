# Docker/Podman

## 概要

軽量な仮想マシンのような存在  
実際はLinux環境上に別のLinuxのディレクトリやファイルを作成して、そこから別の制限されたユーザで起動するイメージ  
そのためLinux環境下以外では同じ方法が取れないため専用のソフトが必要になる  

仮想マシンはOSをすべて内包する必要があるためファイルサイズが肥大化する傾向にある  
一方でDocker等を利用するコンテナと呼ばれる存在Linuxの基本的なところは再利用するため必要なディスク容量はディスクイメージよりも遥かに小さい  
※この概要ではcontainerdのことをDockerと読んでおり正確性にかけているため注意

同様に起動プロセスもコンテナは共用しているところが多いため、物理マシンをエミュレートする仮想マシンよりも遥かに高速に立ち上がる  

## メリット

* 可搬性  
  コンテナ内にアプリケーションとその依存関係が含まれているため、開発、テスト、本番環境で同じ環境を使うことができる。

* 軽量性
  仮想マシンと比べて、Dockerコンテナは独立したOSを持っていないため、リソース消費が少なく、起動も高速。

* 開発の効率化
  Dockerfileという設定ファイルでアプリケーションの環境を定義することができるため、同じ環境を容易に再現できる

## Podman

Red Hatが開発を支援しているオープンソースのコンテナ管理ツール。  
Dockerとほぼ同じ機能を有していながら、後述するセキュリティ上の問題を解決している。  

## 運用上のセキュリティ

セキュリティは仮想マシンと同様に、コンテナ内にも気を配る必要がある  
共用しているとはいえ、内部ではLinuxが動作しているため定期的なセキュリティパッチの適応が必要  
一方で動作させるLinux側にも検討するべき項目がある  
例えばRootlessコンテナである  
Dockerは標準で利用するとrootでの動作が必須  
rootなため万が一コンテナ外に出られる脆弱性がある場合致命的になる  
そのため一般ユーザで実行可能としたものがRootlessである  
また、DockerではなくPodmanを採用するのも一つの選択肢である  
Podmanは設計当初から上記のような問題をカバーするように設計されている

## 覚えておいたほうが良い概念

* イメージ  
  アプリケーションとその依存関係を格納したファイル  

* コンテナ
  イメージを起動した後、そのイメージが生成するファイルとかが格納される領域

## よく使うコマンド

* コンテナを起動して、起動完了後コンテナを削除する  
  ```
  docker run --rm hello-world:latest
  ```

* 利用していないイメージを一括で削除する
  ```
  docker image prune
  ```

今後増やす予定

## Link

[https://www.docker.com/](https://www.docker.com/)

[https://podman.io/](https://podman.io/)

[https://www.redhat.com/ja/topics/containers/what-is-podman](https://www.redhat.com/ja/topics/containers/what-is-podman)

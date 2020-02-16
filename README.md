# LearnDocker

## Dockerについて
従来のホスト型仮想化とコンテナ型仮想化の違い
1. 仮想化のオーバーヘッド   
- 従来の仮想化
    - リソースの面でオーバーヘッドが多く、起動や停止にも時間がかかる。   
- コンテナ型仮想化
    - コンテナはアプリケーション実行に必要なものだけを含み、ホストOSのカーネルを使用するため、動作が早くリソースの使用率も少なく済む。   
2. アプリケーション実行の再現性   
- 従来の仮想化
    -   仮想マシンの環境の違いによりアプリケーションが動作しなくなることが稀に発生する。
    ※仮想マシンごとで独立しており、MWのバージョン差異などにより、動作に影響がおこる場合がある。
- コンテナ型仮想化
    - 特定のアプリケーションを動作させるために必要なものは、Dockerイメージにまとまっており、同じDockerイメージからコンテナを起動する限り、環境が変わっても同様に動作する。
    →コンテナ型はホストに依存しない！
3. OSの自由度
- 従来の仮想化
    - 仮想マシン上で任意のOSを動作させることができる。
- コンテナ型仮想化
    - コンテナはホストOSのカーネルを使用して動作するので、WidowsOS上で直接Linuxコンテナは動作させることができない。
    ※逆もまた然り
4. 分離レベル
- 従来の仮想化
    - ハードウェアレベルで仮想化されており、ホストOSや仮想マシン間の分離レベルが高く、それぞれが影響を受けにくい。
- コンテナ型仮想化
    - OSの機能を使用した仮想化は、従来の仮想化に比べて分離レベルは低い。
    ※高いセキュリティレベルが求められるシステムにはネックになる。

## Dockerのインストール
### DockerのEditionとバージョン
- Docker Community Edition(Docker CE)   
    - 無償版
    - 基本的な機能は使える
- Docker Enterprise Edition(Docker EE)
    - 有償版
    - Docker社が認定したコンテナやプラグインが使える
    - プライベートリポジトリが利用できる。
    - イメージのセキュリティスキャンが行われる。

### インストール方法
Docker アカウントの作成が必要
#### Windows
- Docker for Windows
検索すればわかる。
- Docker Toolbox
GitHubでインストールする。
#### Mac
- Docker for Mac
検索すればわかる。
- Docker Toolbox
GitHubでインストールする。
#### Linux

## Dockerコンテナの実行
### hello-worldコマンドの実行
実行コマンド
> docker run hello-world   

~~~
$ docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
1b930d010525: Pull complete 
Digest: sha256:9572f7cdcee8591948c2963463447a53466950b3fc15a247fcad1917ca215a2f
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
~~~

docker runコマンドの実行時の動作
1. docker run 実行
2. dockerデーモンにイメージを検索しに行く
3. イメージがない場合インターネットを経由してDocker Hubに探しに行く。
4. イメージをPCダウンロード
5. ダウンロードしたイメージを実行する。

#### docker runコマンドの分割
`docker run`コマンドは以下3つのコマンドを実行したのと同じ意味になる。
- `docker pull`：イメージの取得
- `docker create`：コンテナの作成
- `docker start`：コンテナの起動

### Docker Hubとは
- Dockerイメージのレジストリサービス
- Dockerイメージの公開、検索、ダウンロードを行うことができる。   

※officialなリポジトリを選ぶのが安全

#### Tag
Tagでイメージを分けることができる。
> docker run hello-world`:latest`

`:xxx`　xxxがTag名

### Dockerイメージとは
- コンテナ実行に必要なファイルをまとめたファイルシステム
- AUFSなどの特殊なファイルシステムが使用されている。
- イメージ中のデータはレイヤで構成されており、読み取り専用

Dockerイメージのファイルシステム   
イメージは階層構造で管理されている。
コマンドを実行するとレイヤが積み重ねられる。   
一度作成したイメージのレイヤは読み取り専用になり、削除されないため最低限のコマンドのみを実行しないとイメージ容量が大きくなる。   
dockerのメリットは軽量で短時間で起動できること！！

#### Dockerイメージ継承

ベースイメージから継承できる。   
**メリット**   
イメージ管理・通信量の節約ができる？

### whalesayコンテナの実行とDockerイメージダウンロードの動作
> docker run docker/whalesay `cowsay Hello World!`   

cowsay Hello World! はコンテナ内で呼び出すコマンド

~~~
$ docker run docker/whalesay cowsay Hello World!
 ______________ 
< Hello World! >
 -------------- 
    \
     \
      \     
                    ##        .            
              ## ## ##       ==            
           ## ## ## ##      ===            
       /""""""""""""""""___/ ===        
  ~~~ {~~ ~~~~ ~~~ ~~~~ ~~ ~ /  ===- ~~~   
       \______ o          __/            
        \    \        __/             
          \____\______/   

~~~

### ローカル上のDockerイメージの管理


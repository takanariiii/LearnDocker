# 1. 目次
<a id="markdown-%E7%9B%AE%E6%AC%A1" name="%E7%9B%AE%E6%AC%A1"></a>
<!-- TOC -->

- [1. 目次](#1-%E7%9B%AE%E6%AC%A1)
- [2. Dockerについて](#2-docker%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6)
- [3. Dockerのインストール](#3-docker%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB)
    - [3.1. DockerのEditionとバージョン](#31-docker%E3%81%AEedition%E3%81%A8%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B3)
    - [3.2. インストール方法](#32-%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E6%96%B9%E6%B3%95)
        - [3.2.1. Windows](#321-windows)
        - [3.2.2. Mac](#322-mac)
        - [3.2.3. Linux](#323-linux)
- [4. Dockerコンテナの実行](#4-docker%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E5%AE%9F%E8%A1%8C)
    - [4.1. hello-worldコマンドの実行](#41-hello-world%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%AE%E5%AE%9F%E8%A1%8C)
        - [4.1.1. docker runコマンドの分割](#411-docker-run%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%AE%E5%88%86%E5%89%B2)
    - [4.2. Docker Hubとは](#42-docker-hub%E3%81%A8%E3%81%AF)
    - [4.3. Tag](#43-tag)
    - [4.4. Dockerイメージとは](#44-docker%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%81%A8%E3%81%AF)
    - [4.5. Dockerイメージ継承](#45-docker%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E7%B6%99%E6%89%BF)
    - [4.6. whalesayコンテナの実行とDockerイメージダウンロードの動作](#46-whalesay%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E5%AE%9F%E8%A1%8C%E3%81%A8docker%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%83%80%E3%82%A6%E3%83%B3%E3%83%AD%E3%83%BC%E3%83%89%E3%81%AE%E5%8B%95%E4%BD%9C)
- [5. ローカル上のDockerイメージの管理](#5-%E3%83%AD%E3%83%BC%E3%82%AB%E3%83%AB%E4%B8%8A%E3%81%AEdocker%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%81%AE%E7%AE%A1%E7%90%86)
- [6. Dockerfileを使用したイメージビルド方法](#6-dockerfile%E3%82%92%E4%BD%BF%E7%94%A8%E3%81%97%E3%81%9F%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%83%93%E3%83%AB%E3%83%89%E6%96%B9%E6%B3%95)
- [7. リポジトリにイメージをpushする方法](#7-%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%E3%81%AB%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%82%92push%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95)
    - [7.1. Docker Hubへpushする方法](#71-docker-hub%E3%81%B8push%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95)
- [8. nginxコンテナの実行とでタッチモードの解説](#8-nginx%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E5%AE%9F%E8%A1%8C%E3%81%A8%E3%81%A7%E3%82%BF%E3%83%83%E3%83%81%E3%83%A2%E3%83%BC%E3%83%89%E3%81%AE%E8%A7%A3%E8%AA%AC)
    - [8.1. nginxのコンテナを立ち上げるコマンド](#81-nginx%E3%81%AE%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%82%92%E7%AB%8B%E3%81%A1%E4%B8%8A%E3%81%92%E3%82%8B%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89)
- [9. バインドマウントについて](#9-%E3%83%90%E3%82%A4%E3%83%B3%E3%83%89%E3%83%9E%E3%82%A6%E3%83%B3%E3%83%88%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6)
- [10. DockerfileのCOPY命令、ADD命令](#10-dockerfile%E3%81%AEcopy%E5%91%BD%E4%BB%A4add%E5%91%BD%E4%BB%A4)
    - [10.1. docker cpコマンド](#101-docker-cp%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89)
- [11. コンテナのライフサイクル](#11-%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E3%83%A9%E3%82%A4%E3%83%95%E3%82%B5%E3%82%A4%E3%82%AF%E3%83%AB)
- [12. コンテナのシェルへの接続](#12-%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E3%82%B7%E3%82%A7%E3%83%AB%E3%81%B8%E3%81%AE%E6%8E%A5%E7%B6%9A)
- [13. docker commit](#13-docker-commit)

<!-- /TOC -->

# 2. Dockerについて
<a id="markdown-Docker%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6" name="Docker%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6"></a>
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

# 3. Dockerのインストール
<a id="markdown-Docker%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB" name="Docker%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB"></a>

## 3.1. DockerのEditionとバージョン
<a id="markdown-Docker%E3%81%AEEdition%E3%81%A8%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B3" name="Docker%E3%81%AEEdition%E3%81%A8%E3%83%90%E3%83%BC%E3%82%B8%E3%83%A7%E3%83%B3"></a>
- Docker Community Edition(Docker CE)   
    - 無償版
    - 基本的な機能は使える
- Docker Enterprise Edition(Docker EE)
    - 有償版
    - Docker社が認定したコンテナやプラグインが使える
    - プライベートリポジトリが利用できる。
    - イメージのセキュリティスキャンが行われる。

## 3.2. インストール方法
<a id="markdown-%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E6%96%B9%E6%B3%95" name="%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E6%96%B9%E6%B3%95"></a>
Docker アカウントの作成が必要

### 3.2.1. Windows
<a id="markdown-Windows" name="Windows"></a>
- Docker for Windows
検索すればわかる。
- Docker Toolbox
GitHubでインストールする。

### 3.2.2. Mac
<a id="markdown-Mac" name="Mac"></a>
- Docker for Mac
検索すればわかる。
- Docker Toolbox
GitHubでインストールする。

### 3.2.3. Linux
<a id="markdown-Linux" name="Linux"></a>

# 4. Dockerコンテナの実行
<a id="markdown-Docker%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E5%AE%9F%E8%A1%8C" name="Docker%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E5%AE%9F%E8%A1%8C"></a>

## 4.1. hello-worldコマンドの実行
<a id="markdown-hello-world%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%AE%E5%AE%9F%E8%A1%8C" name="hello-world%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%AE%E5%AE%9F%E8%A1%8C"></a>
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

### 4.1.1. docker runコマンドの分割
<a id="markdown-docker%20run%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%AE%E5%88%86%E5%89%B2" name="docker%20run%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%AE%E5%88%86%E5%89%B2"></a>
`docker run`コマンドは以下3つのコマンドを実行したのと同じ意味になる。
- `docker pull`：イメージの取得
- `docker create`：コンテナの作成
- `docker start`：コンテナの起動

## 4.2. Docker Hubとは
<a id="markdown-Docker%20Hub%E3%81%A8%E3%81%AF" name="Docker%20Hub%E3%81%A8%E3%81%AF"></a>
- Dockerイメージのレジストリサービス
- Dockerイメージの公開、検索、ダウンロードを行うことができる。   

※officialなリポジトリを選ぶのが安全

## 4.3. Tag
<a id="markdown-Tag" name="Tag"></a>
Tagでイメージを分けることができる。
> docker run hello-world`:latest`

`:xxx`　xxxがTag名

## 4.4. Dockerイメージとは
<a id="markdown-Docker%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%81%A8%E3%81%AF" name="Docker%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%81%A8%E3%81%AF"></a>
- コンテナ実行に必要なファイルをまとめたファイルシステム
- AUFSなどの特殊なファイルシステムが使用されている。
- イメージ中のデータはレイヤで構成されており、読み取り専用

Dockerイメージのファイルシステム   
イメージは階層構造で管理されている。
コマンドを実行するとレイヤが積み重ねられる。   
一度作成したイメージのレイヤは読み取り専用になり、削除されないため最低限のコマンドのみを実行しないとイメージ容量が大きくなる。   
dockerのメリットは軽量で短時間で起動できること！！

## 4.5. Dockerイメージ継承
<a id="markdown-Docker%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E7%B6%99%E6%89%BF" name="Docker%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E7%B6%99%E6%89%BF"></a>

ベースイメージから継承できる。   
**メリット**   
イメージ管理・通信量の節約ができる？

## 4.6. whalesayコンテナの実行とDockerイメージダウンロードの動作
<a id="markdown-whalesay%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E5%AE%9F%E8%A1%8C%E3%81%A8Docker%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%83%80%E3%82%A6%E3%83%B3%E3%83%AD%E3%83%BC%E3%83%89%E3%81%AE%E5%8B%95%E4%BD%9C" name="whalesay%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E5%AE%9F%E8%A1%8C%E3%81%A8Docker%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%83%80%E3%82%A6%E3%83%B3%E3%83%AD%E3%83%BC%E3%83%89%E3%81%AE%E5%8B%95%E4%BD%9C"></a>
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

# 5. ローカル上のDockerイメージの管理
<a id="markdown-%E3%83%AD%E3%83%BC%E3%82%AB%E3%83%AB%E4%B8%8A%E3%81%AEDocker%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%81%AE%E7%AE%A1%E7%90%86" name="%E3%83%AD%E3%83%BC%E3%82%AB%E3%83%AB%E4%B8%8A%E3%81%AEDocker%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%81%AE%E7%AE%A1%E7%90%86"></a>
ローカル上にダウンロードズミのイメージ一覧を表示するコマンド
> docker images

イメージにタグ付けするコマンド
>$docker tag 元となるイメージ名 新しいイメージ名

~~~
$ docker images
REPOSITORY              TAG                 IMAGE ID            CREATED             SIZE
hello-world             latest              fce289e99eb9        13 months ago       1.84kB
$
$ docker tag hello-world hello_world 
$ docker images
REPOSITORY              TAG                 IMAGE ID            CREATED             SIZE
hello-world             latest              fce289e99eb9        13 months ago       1.84kB
hello_world             latest              fce289e99eb9        13 months ago       1.84kB
~~~
Tag名は:xxxをつけるだけ
> docker tag hello-world hello-world:version1
~~~
$ docker tag hello-world hello-world:version1
$ docker images
REPOSITORY              TAG                 IMAGE ID            CREATED             SIZE
hello-world             latest              fce289e99eb9        13 months ago       1.84kB
hello-world             version1            fce289e99eb9        13 months ago       1.84kB
hello_world             latest              fce289e99eb9        13 months ago       1.84kB
~~~
イメージの詳細情報を表示するコマンド
> $ docker inspect イメージ名orイメージID

~~~$ docker inspect hello-world
[
    {
        "Id": "sha256:fce289e99eb9bca977dae136fbe2a82b6b7d4c372474c9235adc1741675f587e",
        "RepoTags": [
            "hello-world:latest",
            "hello-world:version1",
            "hello_world:latest"
        ],
        "RepoDigests": [
            "hello-world@sha256:9572f7cdcee8591948c2963463447a53466950b3fc15a247fcad1917ca215a2f"
        ],
        "Parent": "",
        "Comment": "",
        "Created": "2019-01-01T01:29:27.650294696Z",
        "Container": "8e2caa5a514bb6d8b4f2a2553e9067498d261a0fd83a96aeaaf303943dff6ff9",
        "ContainerConfig": {
            "Hostname": "8e2caa5a514b",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/bin/sh",
                "-c",
                "#(nop) ",
                "CMD [\"/hello\"]"
            ],
            "ArgsEscaped": true,
            "Image": "sha256:a6d1aaad8ca65655449a26146699fe9d61240071f6992975be7e720f1cd42440",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {}
        },
        "DockerVersion": "18.06.1-ce",
        "Author": "",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
            ],
            "Cmd": [
                "/hello"
            ],
            "ArgsEscaped": true,
            "Image": "sha256:a6d1aaad8ca65655449a26146699fe9d61240071f6992975be7e720f1cd42440",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": null
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 1840,
        "VirtualSize": 1840,
        "GraphDriver": {
            "Data": {
                "MergedDir": "/var/lib/docker/overlay2/2e995fb1d8c4111282944c66fe974d1fc7174cc7018bb317a0cc93948ee08a2c/merged",
                "UpperDir": "/var/lib/docker/overlay2/2e995fb1d8c4111282944c66fe974d1fc7174cc7018bb317a0cc93948ee08a2c/diff",
                "WorkDir": "/var/lib/docker/overlay2/2e995fb1d8c4111282944c66fe974d1fc7174cc7018bb317a0cc93948ee08a2c/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:af0b15c8625bb1938f1d7b17081031f649fd14e6b233688eea3c5483994a66a3"
            ]
        },
        "Metadata": {
            "LastTagTime": "2020-02-16T13:58:03.1757937Z"
        }
    }
]
~~~

ローカルのイメージを削除するコマンド
> $docker rmi イメージ名orイメージID

※コンテナが起動している場合、先にstopするか、-fで強制削除する。
> $docker rmi -f イメージ名orイメージID

イメージを取得するコマンド
>$docker pull 取得したいイメージ名

※タグ名を指定しないとlatestタグが指定されるが、**latest=最新ではない**。明示的にタグ名をつけて管理するべき。

# 6. Dockerfileを使用したイメージビルド方法
<a id="markdown-Dockerfile%E3%82%92%E4%BD%BF%E7%94%A8%E3%81%97%E3%81%9F%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%83%93%E3%83%AB%E3%83%89%E6%96%B9%E6%B3%95" name="Dockerfile%E3%82%92%E4%BD%BF%E7%94%A8%E3%81%97%E3%81%9F%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%83%93%E3%83%AB%E3%83%89%E6%96%B9%E6%B3%95"></a>

1. 作業用のディレクトリを作成する。
2. Dockerfileを作成する。
- FROM命令：イメージを引用する。
- RUN命令：実行コマンド(各コマンドに-fを付けないと止まる。)
- CMD命令：コンテナが作成された後に実行するコマンド

Dockerfileからイメージをビルドするコマンド
> $docker build -t タグ名の指定 ビルドコンテキストの指定

※ビルドコンテキストのディレクトリのファイル全てがビルド時**一時的に**Dockerデーモンへ送信される。   
　不要な大容量ファイルがあるとビルドに時間がかかる。[(参考：Dockerのビルドコンテキスト(build context)について確認したときのメモ)](https://qiita.com/toshihirock/items/c85f3eb5f4752b15ca3d) 

ビルドキャッシュ：すでにビルドした場合キャッシュを利用する。   
キャッシュの利用を避けたい場合
> docker build --no-cache -t タグ名 ビルドコンテキスト

# 7. リポジトリにイメージをpushする方法
<a id="markdown-%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%E3%81%AB%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%82%92push%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95" name="%E3%83%AA%E3%83%9D%E3%82%B8%E3%83%88%E3%83%AA%E3%81%AB%E3%82%A4%E3%83%A1%E3%83%BC%E3%82%B8%E3%82%92push%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95"></a>

## 7.1. Docker Hubへpushする方法
<a id="markdown-Docker%20Hub%E3%81%B8push%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95" name="Docker%20Hub%E3%81%B8push%E3%81%99%E3%82%8B%E6%96%B9%E6%B3%95"></a>
Docker Hubにログインする場合
> $docker login

Quay.ioにログインする場合
> docker login quay.io

自前リポジトリサーバも作れる。

タグ付けルール
> <`DockerID`>`/`<`イメージ名`>:<タグ名>   
※タグ名は省略可能、その場合はlatestタグ

Pushコマンド
> docker push ＜DockerID＞/＜イメージ名＞:＜タグ名＞

# 8. nginxコンテナの実行とでタッチモードの解説
<a id="markdown-nginx%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E5%AE%9F%E8%A1%8C%E3%81%A8%E3%81%A7%E3%82%BF%E3%83%83%E3%83%81%E3%83%A2%E3%83%BC%E3%83%89%E3%81%AE%E8%A7%A3%E8%AA%AC" name="nginx%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E5%AE%9F%E8%A1%8C%E3%81%A8%E3%81%A7%E3%82%BF%E3%83%83%E3%83%81%E3%83%A2%E3%83%BC%E3%83%89%E3%81%AE%E8%A7%A3%E8%AA%AC"></a>

## 8.1. nginxのコンテナを立ち上げるコマンド
<a id="markdown-nginx%E3%81%AE%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%82%92%E7%AB%8B%E3%81%A1%E4%B8%8A%E3%81%92%E3%82%8B%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89" name="nginx%E3%81%AE%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%82%92%E7%AB%8B%E3%81%A1%E4%B8%8A%E3%81%92%E3%82%8B%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89"></a>

> $ docker run --name <コンテナ名> -d -p <ホストのポート番号>:<コンテナ側のポート番号> <イメージ名>  
※　--name : コンテナに名前をつける  
　 -d：デタッチモード（バックグランド実行）  

# 9. バインドマウントについて
<a id="markdown-%E3%83%90%E3%82%A4%E3%83%B3%E3%83%89%E3%83%9E%E3%82%A6%E3%83%B3%E3%83%88%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6" name="%E3%83%90%E3%82%A4%E3%83%B3%E3%83%89%E3%83%9E%E3%82%A6%E3%83%B3%E3%83%88%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6"></a>

~~~
$docker run --name <コンテナ名> -d -v <ホスト側のディレクトリ >:<コンテナ側のマウントポイント>:<オプション> -p <ホスト側のポート番号>:<コンテナ側のポート番号> <イメージ名>
~~~

> -v で指定するパスは絶対パス

# 10. DockerfileのCOPY命令、ADD命令
<a id="markdown-Dockerfile%E3%81%AECOPY%E5%91%BD%E4%BB%A4%E3%80%81ADD%E5%91%BD%E4%BB%A4" name="Dockerfile%E3%81%AECOPY%E5%91%BD%E4%BB%A4%E3%80%81ADD%E5%91%BD%E4%BB%A4"></a>

## 10.1. docker cpコマンド
<a id="markdown-docker%20cp%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89" name="docker%20cp%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89"></a>

~~~
ホストマシンのファイルをコンテナ内にコピーする場合
$docker cp <ホスト上のコピーしたいファイルのパス> <コンテナ名or ID>:<コピー先のパス>

コンテナ内のファイルをホストマシンにコピーする場合
$docker cp <コンテナ名 or ID>:<コンテナ情のコピーしたいファイルのパス> <コピー先のパス>
~~~

# 11. コンテナのライフサイクル
<a id="markdown-%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E3%83%A9%E3%82%A4%E3%83%95%E3%82%B5%E3%82%A4%E3%82%AF%E3%83%AB" name="%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E3%83%A9%E3%82%A4%E3%83%95%E3%82%B5%E3%82%A4%E3%82%AF%E3%83%AB"></a>

docker inspect 

docker pause

docker unpause

# 12. コンテナのシェルへの接続
<a id="markdown-%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E3%82%B7%E3%82%A7%E3%83%AB%E3%81%B8%E3%81%AE%E6%8E%A5%E7%B6%9A" name="%E3%82%B3%E3%83%B3%E3%83%86%E3%83%8A%E3%81%AE%E3%82%B7%E3%82%A7%E3%83%AB%E3%81%B8%E3%81%AE%E6%8E%A5%E7%B6%9A"></a>
 
~~~bash
$ docker attach <コンテナ名 or コンテナID>
※ただし、シェルに接続できるのは、コンテナでシェルを実行している場合のみ
Ctrl+p,Ctrl+qでコンテナから抜ける。exitで抜けるとコンテナ停止する。

＜推奨＞
$ docker exec -it <コンテナ名 or コンテナID> /bin/bash
※bashがなければ、別のシェルを選択する
~~~

# 13. docker commit
<a id="markdown-docker%20commit" name="docker%20commit"></a>

~~~bash
$ docker commit <コンテナ名 or コンテナID> <イメージ名>:<タグ名>
~~~

どのような操作で作成されたかわからなくなるので、通常はDockerFILEで変更する。
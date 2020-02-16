# 1. 目次
<!-- TOC -->

- [1. 目次](#1-目次)
- [2. Dockerについて](#2-dockerについて)
- [3. Dockerのインストール](#3-dockerのインストール)
    - [1. <a name='DockerEdition'></a>3.1. DockerのEditionとバージョン](#1-a-namedockereditiona31-dockerのeditionとバージョン)
    - [2. <a name=''></a>3.2. インストール方法](#2-a-namea32-インストール方法)
        - [2.1. <a name='Windows'></a>3.2.1. Windows](#21-a-namewindowsa321-windows)
        - [2.2. <a name='Mac'></a>3.2.2. Mac](#22-a-namemaca322-mac)
        - [2.3. <a name='Linux'></a>3.2.3. Linux](#23-a-namelinuxa323-linux)
- [4. Dockerコンテナの実行](#4-dockerコンテナの実行)
    - [3. <a name='hello-world'></a>4.1. hello-worldコマンドの実行](#3-a-namehello-worlda41-hello-worldコマンドの実行)
        - [3.1. <a name='dockerrun'></a>4.1.1. docker runコマンドの分割](#31-a-namedockerruna411-docker-runコマンドの分割)
    - [4. <a name='DockerHub'></a>4.2. Docker Hubとは](#4-a-namedockerhuba42-docker-hubとは)
    - [5. <a name='Tag'></a>4.3. Tag](#5-a-nametaga43-tag)
    - [6. <a name='Docker'></a>4.4. Dockerイメージとは](#6-a-namedockera44-dockerイメージとは)
    - [7. <a name='Docker-1'></a>4.5. Dockerイメージ継承](#7-a-namedocker-1a45-dockerイメージ継承)
    - [8. <a name='whalesayDocker'></a>4.6. whalesayコンテナの実行とDockerイメージダウンロードの動作](#8-a-namewhalesaydockera46-whalesayコンテナの実行とdockerイメージダウンロードの動作)
- [5. ローカル上のDockerイメージの管理](#5-ローカル上のdockerイメージの管理)
- [6. Dockerfileを使用したイメージビルド方法](#6-dockerfileを使用したイメージビルド方法)
- [7. リポジトリにイメージをpushする方法](#7-リポジトリにイメージをpushする方法)
    - [9. <a name='DockerHubpush'></a>7.1. Docker Hubへpushする方法](#9-a-namedockerhubpusha71-docker-hubへpushする方法)

<!-- /TOC -->

# 2. Dockerについて
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

##  1. <a name='DockerEdition'></a>3.1. DockerのEditionとバージョン
- Docker Community Edition(Docker CE)   
    - 無償版
    - 基本的な機能は使える
- Docker Enterprise Edition(Docker EE)
    - 有償版
    - Docker社が認定したコンテナやプラグインが使える
    - プライベートリポジトリが利用できる。
    - イメージのセキュリティスキャンが行われる。

##  2. <a name=''></a>3.2. インストール方法
Docker アカウントの作成が必要

###  2.1. <a name='Windows'></a>3.2.1. Windows
- Docker for Windows
検索すればわかる。
- Docker Toolbox
GitHubでインストールする。

###  2.2. <a name='Mac'></a>3.2.2. Mac
- Docker for Mac
検索すればわかる。
- Docker Toolbox
GitHubでインストールする。

###  2.3. <a name='Linux'></a>3.2.3. Linux

# 4. Dockerコンテナの実行

##  3. <a name='hello-world'></a>4.1. hello-worldコマンドの実行
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

###  3.1. <a name='dockerrun'></a>4.1.1. docker runコマンドの分割
`docker run`コマンドは以下3つのコマンドを実行したのと同じ意味になる。
- `docker pull`：イメージの取得
- `docker create`：コンテナの作成
- `docker start`：コンテナの起動

##  4. <a name='DockerHub'></a>4.2. Docker Hubとは
- Dockerイメージのレジストリサービス
- Dockerイメージの公開、検索、ダウンロードを行うことができる。   

※officialなリポジトリを選ぶのが安全

##  5. <a name='Tag'></a>4.3. Tag
Tagでイメージを分けることができる。
> docker run hello-world`:latest`

`:xxx`　xxxがTag名

##  6. <a name='Docker'></a>4.4. Dockerイメージとは
- コンテナ実行に必要なファイルをまとめたファイルシステム
- AUFSなどの特殊なファイルシステムが使用されている。
- イメージ中のデータはレイヤで構成されており、読み取り専用

Dockerイメージのファイルシステム   
イメージは階層構造で管理されている。
コマンドを実行するとレイヤが積み重ねられる。   
一度作成したイメージのレイヤは読み取り専用になり、削除されないため最低限のコマンドのみを実行しないとイメージ容量が大きくなる。   
dockerのメリットは軽量で短時間で起動できること！！

##  7. <a name='Docker-1'></a>4.5. Dockerイメージ継承

ベースイメージから継承できる。   
**メリット**   
イメージ管理・通信量の節約ができる？

##  8. <a name='whalesayDocker'></a>4.6. whalesayコンテナの実行とDockerイメージダウンロードの動作
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

##  9. <a name='DockerHubpush'></a>7.1. Docker Hubへpushする方法
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


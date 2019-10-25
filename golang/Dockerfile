# API Image 作成

# ベースとなるイメージ
FROM golang:1.12.1-alpine3.9

# Gopkg.toml 等を事前にコピーして dep ensure が実行できるようにする
COPY ./api /go/src/api

# dep ensure を行うプロジェクトルートに移動する
WORKDIR /go/src/api/

# 必要なパッケージをイメージにインストールする
RUN apk update \
  && apk add --no-cache git \
  && go get github.com/codegangsta/gin \
  && go get -u github.com/golang/dep/cmd/dep \
  && dep ensure

# コンテナ実行時のデフォルトを設定する
# ライブリロードを実行する
CMD gin -i run

#Gopkg.lockとGopkg.tomiは最初では作成できないので仮のdocker環境を作成して行った。
#また、docker内部にはdocker run -v $PWD:/go/src/app -it golang:1.12.1-alpine3.9
#で侵入し 先にapk add --no-cache gitを入れる。　これを先に入れないとこける
#go get -u github.com/golang/dep/cmd/dep　して dep initでOK
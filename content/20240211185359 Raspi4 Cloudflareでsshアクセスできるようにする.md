
# 20240211185359 Raspi4 Cloudflareでsshアクセスできるようにする
#raspi #cloudflare #ssh 
## 注意 
[[20240211141946 Raspi4 Cloudflareでトンネルを作る|Raspi4 Cloudflareでトンネルを作る#注意]] と同じ。設定方法がどんどん変わる上、私はその専門ではない

## 前提
[[20240211141946 Raspi4 Cloudflareでトンネルを作る|Raspi4 Cloudflareでトンネルを作る]] の作業が完了している

## 手順
### サーバー側の設定
- [[20240211195201 Cloudflare Access Groupsの作成|Cloudflare Access Groupsの作成]]
- [[20240211195126 Cloudflare Applicationsの作成|Cloudflare Applicationsの作成]]

を終わらせる。他にやることはなかったと思う。

### クライアント側の設定
直接sshではアクセスできず、 cloudflaredコマンドを使う。 以下はwsl2でubuntuを使っていた場合。

cloudflaredをインストールする。 d(daemon)としては使わないけど。
[Downloads · Cloudflare Zero Trust docs](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/downloads/) から、 amd64/x86-64 の .deb をダウンロード、
```
$ sudo dpkg -i coudflared-linux-amd64.deb
```
でインストール。

.ssh/config に、 cloudflaredを使う設定にしたssh設定を追記。

```
Host pi4.kinoshita-lab.org (cloudflareで作ったsshのtunnel)
        Port xxxxx (自分が設定したポート番号)
        ProxyCommand cloudflared access ssh --hostname %h
```

```
$ ssh pi4.kinoshita-lab.org
```

でログインできればOK。

## cf.
- [SSH · Cloudflare Zero Trust docs](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/use-cases/ssh/)
- [Cloudflare Zero TrustでSSH接続](https://zenn.dev/jij_inc/articles/659fe35813b940)
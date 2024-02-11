
# 20240211185359 Raspi4 Cloudflareでsshアクセスできるようにする
#raspi #cloudflare #ssh 
## 注意 
[[20240211141946 Raspi4 Cloudflareでトンネルを作る|Raspi4 Cloudflareでトンネルを作る]] と同じ。設定方法がどんどん変わる上、私はその専門ではない

## 前提
[[20240211141946 Raspi4 Cloudflareでトンネルを作る|Raspi4 Cloudflareでトンネルを作る]] の作業が完了している

## 手順
### サーバー側の設定
- [[20240211195201 Cloudflare Access Groupsの作成|Cloudflare Access Groupsの作成]]
- [[20240211195126 Cloudflare Applicationsの作成|Cloudflare Applicationsの作成]]
を終わらせる。他にやることはなかったと思う。

### クライアント側の設定
直接sshではアクセスできず、 cloudflaredコマンドを使う。 以下はwsl2でubuntuを使っていた場合





## cf.
- [SSH · Cloudflare Zero Trust docs](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/use-cases/ssh/)
- [Cloudflare Zero TrustでSSH接続](https://zenn.dev/jij_inc/articles/659fe35813b940)
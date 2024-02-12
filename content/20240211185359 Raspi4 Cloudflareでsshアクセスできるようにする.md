
# 20240211185359 Raspi4 Cloudflareでsshアクセスできるようにする
#raspi #cloudflare #ssh 
## 注意 
[[20240211141946 Raspi4 Cloudflareでトンネルを作る|Raspi4 Cloudflareでトンネルを作る]] と同じ。設定方法がどんどん変わる上、私はその専門ではない

## 前提
- [[20240211141946 Raspi4 Cloudflareでトンネルを作る|Raspi4 Cloudflareでトンネルを作る]] の作業が完了している
- [[20240211202623 Raspi4 Cloudflare tunnel経由でhttpsサーバーを公開する|Raspi4 Cloudflare tunnel経由でhttpsサーバーを公開する]] の作業が完了している(ユーザー、サービスなどは作成してある)


## 手順
CNAME recordの追加
```
$ cloudflared tunnel route dns **** pi4.kinoshita-lab.org(ここは好きなやつにする)

2024-02-12T11:33:59Z INF Added CNAME pi4.kinoshita-lab.org which will route to this tunnel tunnelID=****
```

\**** は [[20240212183159 cloudflare トンネルのtoken|cloudflare トンネルのtoken(private)]] を入れる。

systemで動いているcloudflaredにsshの設定を追加。



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
- [Cloudflare Tunnel を使って自宅サーバを公開する - hoge な blog](https://akkyorz.hatenablog.com/entry/2022/12/15/012728)
- [\[Cloudflare\] Cloudflare Tunnel の Ingress rules で複数サービスまとめて公開する - てくなべ (tekunabe)](https://tekunabe.hatenablog.jp/entry/2023/08/05/cloudflare_tunnel_ingress_rules)

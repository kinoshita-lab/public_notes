# 20240211202623 Raspi4 Cloudflare tunnel経由でhttpsサーバーを公開する
#raspi #cloudflare #server

## 前提となる作業
- [[20240211141946 Raspi4 Cloudflareでトンネルを作る|Raspi4 Cloudflareでトンネルを作る]]
- [[20240212183719 Raspi4でnginxを設定する|Raspi4でnginxを設定する]]



## WEBサーバーの設定
raspiのwebサーバーは80番(http)で動かして、cloudflareでhttps化してる。
- [[20240212183719 Raspi4でnginxを設定する|raspi4でnginxを設定する]] で、WEBサーバー(nginx)を動かしておく。

## 作ったWEBサーバーをcloudflareのトンネルに登録

```
cloudflare@saipi4$ vim ~/.cloudflared/config.yaml
```
で、中身はこんな感じ。

```
url: http://localhost
tunnel: ******
credentials-file: /var/lib/cloudflare/.cloudflared/******.json
```
\**** の所はトンネルを作ったときの token(or UUID or TunnelID).  [[20240212183159 Cloudflare トンネルのtoken|cloudflare トンネルのtoken(private)]]

```
cloudflare@saipi4:~ $ cloudflared tunnel route dns ***** notes.kinoshita-lab.org
2024-02-12T10:20:56Z INF Added CNAME notes.kinoshita-lab.org which will route to this tunnel tunnelID=****
```
```
cloudflare@saipi4:~ $ cloudflared tunnel --config ~/.cloudflared/config.yaml run
```

これでうまくいったら、 https://notes.kinoshita-lab.org にアクセスすると見える。

### service化
うまくいっていたらserviceとして登録。
```
cloudflare@saipi4:~ $ vim sudo vim /etc/systemd/system/cloudflared.service\
```
中身は
```
[Unit]
Description=cloudflared
After=network.target

[Service]
TimeoutStartSec=0
Type=notify
User=cloudflare
ExecStart=/usr/bin/cloudflared tunnel --config /var/lib/cloudflare/.cloudflared/config.yaml run
Restart=on-failure
RestartSec=5s

[Install]
WantedBy=multi-user.target
```



## cf.

- [Cloudflare Tunnel を使って自宅サーバを公開する - hoge な blog](https://akkyorz.hatenablog.com/entry/2022/12/15/012728)
# 20240211202623 Raspi4 Cloudflare tunnel経由でhttpsサーバーを公開する
#raspi #cloudflare #server

## 前提となる作業
- [[20240211193602 Cloudflare Public Hostnameの設定|Cloudflare Public Hostnameの設定]]
- [[20240211195126 Cloudflare Applicationsの作成|Cloudflare Applicationsの作成]]
- [[20240211141946 Raspi4 Cloudflareでトンネルを作る|Raspi4 Cloudflareでトンネルを作る]]

あたりかな。


## WEBサーバーの設定
- [[20240212183719 raspi4でnginxを設定する|raspi4でnginxを設定する]] で、WEBサーバー(nginx)を動かしておく。
- [[20240205150537 Caddyをraspi4にインストール|Caddyをraspi4にインストール]] で、Caddyを動かしてもよい。

## 作ったWEBサーバーをcloudflareのトンネルに登録

```
cloudflare@saipi4$ vim ~/.cloudflared/config/yaml
```
で、中身はこんな感じ。

```
url: http://localhost
tunnel: ******
credentials-file: /var/lib/cloudflare/.cloudflared/******.json
```
\**** の所はトンネルを作ったときの token(or UUID or TunnelID).  [[20240212183159 cloudflare トンネルのtoken|cloudflare トンネルのtoken(private)]]

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
cloudflare@saipi4:~ $ vim 

```

## cf.


- [Cloudflare Tunnel を使って自宅サーバを公開する - hoge な blog](https://akkyorz.hatenablog.com/entry/2022/12/15/012728)
- [Set up Cloudflare · Cloudflare Fundamentals docs](https://developers.cloudflare.com/fundamentals/setup/)
- [How to use Caddy with Cloudflare's SSL settings](https://samjmck.com/en/blog/using-caddy-with-cloudflare/)
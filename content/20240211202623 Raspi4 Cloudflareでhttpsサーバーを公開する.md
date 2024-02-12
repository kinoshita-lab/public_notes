# 20240211202623 Raspi4 Cloudflareでhttpsサーバーを公開する
#raspi #cloudflare #server

## 前提となる作業
- [[20240211193602 Cloudflare Public Hostnameの設定|Cloudflare Public Hostnameの設定]]
- [[20240211195126 Cloudflare Applicationsの作成|Cloudflare Applicationsの作成]]
- [[20240212184429 Cloudflare SSL_TLS setup|cloudflare SSL/TLS setup]]

あたりかな。


## WEBサーバーの設定
- [[20240212183719 raspi4でnginxを設定する|raspi4でnginxを設定する]] で、WEBサーバー(nginx)を動かしておく。
- [[20240205150537 Caddyをraspi4にインストール|Caddyをraspi4にインストール]] で、Caddyを動かしてもよい。

## cf.

- - [Cloudflare Tunnel を使って自宅サーバを公開する - hoge な blog](https://akkyorz.hatenablog.com/entry/2022/12/15/012728)
- [Set up Cloudflare · Cloudflare Fundamentals docs](https://developers.cloudflare.com/fundamentals/setup/)
- [How to use Caddy with Cloudflare's SSL settings](https://samjmck.com/en/blog/using-caddy-with-cloudflare/)
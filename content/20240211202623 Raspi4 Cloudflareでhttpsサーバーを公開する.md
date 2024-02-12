# 20240211202623 Raspi4 Cloudflareでhttpsサーバーを公開する
#raspi #cloudflare #server

## 前提となる作業
- [[20240211193602 Cloudflare Public Hostnameの設定|Cloudflare Public Hostnameの設定]]
- [[20240211195126 Cloudflare Applicationsの作成|Cloudflare Applicationsの作成]]
あたりかな。

## SSL/TLS setup
[Get started with SSL/TLS · Cloudflare SSL/TLS docs](https://developers.cloudflare.com/ssl/get-started/) を見ながら作業。
  [Add a site · Cloudflare Fundamentals docs](https://developers.cloudflare.com/fundamentals/setup/manage-domains/add-site/)
デフォルトの encryption modeはFlexible
[Origin CA certificates · Cloudflare SSL/TLS docs](https://developers.cloudflare.com/ssl/origin-configuration/origin-ca#1-create-an-origin-ca-certificate)

作ったキーをサーバーに保存
[[20240212132340 CloudFlareのkey pairs|20240212132340 CloudFlareのkey pairs(private)]]

- certificateを `/etc/ssl/certs/certificate.pem` 
- private key を `/etc/ssl/private/key.pem` に保存


## WEBサーバーの設定
- [[20240212183719 raspi4でnginxを設定する|raspi4でnginxを設定する]]
## cf.
- [Set up Cloudflare · Cloudflare Fundamentals docs](https://developers.cloudflare.com/fundamentals/setup/)
- [How to use Caddy with Cloudflare's SSL settings](https://samjmck.com/en/blog/using-caddy-with-cloudflare/)
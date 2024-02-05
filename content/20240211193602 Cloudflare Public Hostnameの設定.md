# 20240211193602 Cloudflare Public Hostnameの設定
#cloudflare #config #server  #raspi 


Cloudflareの同じ画面で、"Public Hostname" をクリック。
"+ Add a public hostname"
をクリック。
subdomain: sshでアクセスしたい場合のサブドメインを設定(optional)
Domain: 使いたいドメイン ([[#サイトを追加する]] で追加したものしか選べない)を選ぶ

### SSHの追加
Service 
Type: sshを選択
URL: localhost:`[sshのポート]` 
Save hostname をクリック。

### HTTP/HTTPSの追加
Service 
Type: https or  httpを選ぶ
URL: localhost 
Save hostname をクリック。


自分の場合とりあえずこんな感じにしてある。
![[Pasted image 20240211193442.png]]


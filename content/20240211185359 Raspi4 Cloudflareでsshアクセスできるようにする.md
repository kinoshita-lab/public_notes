
# 20240211185359 Raspi4 Cloudflareでsshアクセスできるようにする
#raspi #cloudflare #ssh 
## 注意 
[[20240211141946 Raspi4 Cloudflareでトンネルを作る|Raspi4 Cloudflareでトンネルを作る]] と同じ。設定方法がどんどん変わる上、私はその専門ではない

## 前提
[[20240211141946 Raspi4 Cloudflareでトンネルを作る|Raspi4 Cloudflareでトンネルを作る]] の作業が完了している

## 手順
#### Access Groupsの作成
cloudflareにログイン、 Zero Trustをクリック。
AccessからAccess Groupsを選択。 "+ Add a Group"をクリック。
遷移した画面で、"Assign as default group" に チェック。 Include の所のSelectorは適切に設定する。
Everyone/Everyone という設定も可能だが、セキュリティ上あまりよろしくない。
ドメインでメールの設定をしている場合、それが使えるので、 Selectorに"Emails ending in" を選んで、Valueにメールアドレスのドメインを記入した。複数指定できる。
こんなかんじ。

![[Pasted image 20240211191414.png]]



#### Applicationsの作成
これが何かよくわかっていない。
todo: RTFM [Applications · Cloudflare Zero Trust docs](https://developers.cloudflare.com/cloudflare-one/applications/)
Zero Trustのダッシュボードで、 Access -> Applicationsを選択。 "+ Add an application"をクリック。



 

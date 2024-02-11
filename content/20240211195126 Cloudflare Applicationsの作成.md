#### 20240211195126 Applicationsの作成
※ これが何かよくわかっていない。
todo: RTFM [Applications · Cloudflare Zero Trust docs](https://developers.cloudflare.com/cloudflare-one/applications/)

Zero Trustのダッシュボードで、 Access -> Applicationsを選択。 "+ Add an application"をクリック。
次の画面では "Self Hosted"を選ぶ

Application name: default にした
Application domain: subdomain: [[20240211193602 Cloudflare Public Hostnameの設定|Cloudflare Public Hostnameの設定]] で設定したサブドメインを追加。
こんな感じ。pi4はsshアクセス、notesはhttps。
 
![[Pasted image 20240211195107.png]]

Policiesタブをクリックして、policyを作成する。
default_policyというのを作り、 設定はデフォルトとした。
Assing a group で、 [[20240211195201 Cloudflare Access Groupsの作成|Cloudflare Access Groupsの作成]] で作ったdefault_groupにチェック。 "Save policy"でPolicyを作成。
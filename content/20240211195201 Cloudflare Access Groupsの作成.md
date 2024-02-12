#### 20240211195201 Cloudflare Access Groupsの作成
cloudflareにログイン、 Zero Trustをクリック。
AccessからAccess Groupsを選択。 "+ Add a Group"をクリック。
遷移した画面で、"Assign as default group" に チェック。 Include の所のSelectorは適切に設定する。
Everyone/Everyone という設定も可能だが、セキュリティ上あまりよろしくない。
ドメインでメールの設定をしている場合、それが使えるので、 Selectorに"Emails ending in" を選んで、Valueにメールアドレスのドメインを記入した。複数指定できる。
こんなかんじ。
Group nameは "default_group"に設定した。

![[Pasted image 20240211191414.png]]


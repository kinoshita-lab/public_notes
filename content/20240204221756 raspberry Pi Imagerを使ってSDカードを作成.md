### 20240204221756 raspberry Pi Imagerを使ってSDカードを作成
#raspi 
[Install Raspberry Pi OS using Raspberry Pi Imager](https://www.raspberrypi.com/software/) のDownload for * で自分の環境用のRaspberry Pi Imagerをダウンロード、インストール

起動したら、 
- Raspberry PIデバイス: RASPBERRY PI4
- OS: Raspberry Pi OS(other) -> Raspberry Pi OS Lite(64-bit)
- ストレージ: マイクロSDカードをPCに接続して、それを選ぶ
`Would you like to apply OS customization settings?` 
で「設定を編集する」ボタンを押す。
- 一般 ホスト名、ユーザー名とパスワード、ロケールなど適切に設定
- サービス SSHを有効にする をチェック パスワード認証を使う
- オプション 編集せず
で保存ボタンを押す。
`Would you like to apply OS customization settings?`  で、 「はい」を選んで書き込み。

SSDブートにしたい場合
完全に同じことを、USBのSSDで実施する。
microSDはブートの設定を変更する目的で作って、設定を変更してSSDからブートできるようになった後には使用しない。
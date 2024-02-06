# 20240206132752 IAR Embedded workbench の画面がめちゃくちゃになったときのworkaround
#IAR #eww #workaround

いったん終了し、以下フォルダを削除して再起動する。
 - 出力フォルダ
　 　　`プロジェクトオプション > 一般オプション > 出力 > 出力ディレクトリ`
　 　　で指定されるフォルダ。デフォルトの場合Debugフォルダ。
　- .dep / .ewtファイル（存在する場合）
　- settings フォルダ
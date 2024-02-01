# 20240123115736 wsl2からwindowsのvs codeが起動できない
#wsl2 #wsl #vscode

[WSL2 (Preview) cannot run .exe files: exec format error: wsl.exe · Issue #8952 · microsoft/WSL · GitHub](https://github.com/microsoft/WSL/issues/8952#issuecomment-1568212651)
```
sudo sh -c 'echo :WSLInterop:M::MZ::/init:PF > /usr/lib/binfmt.d/WSLInterop.conf'
sudo systemctl restart systemd-binfmt
```

次の人のやつも一応やった
```
sudo sh -c 'echo :WSLInterop:M::MZ::/init:PF > /usr/lib/binfmt.d/WSLInterop.conf'
sudo systemctl unmask systemd-binfmt.service
sudo systemctl restart systemd-binfmt
sudo systemctl mask systemd-binfmt.service
```

念の為wslを再起動 
pwshで `wsl --shutdown`

これでうまくいった。


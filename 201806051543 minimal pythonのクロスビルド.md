# 201806051543 minimal pythonのクロスビルド
#python #programming #embedded  #linux 

cross compileの方法
config.siteっていうファイルをつくる

中身
ac_cv_file__dev_ptmx=no
ac_cv_file__dev_ptc=no

```sh
 CFLAGS='-Os' CONFIG_SITE=config.site ./configure --build=x86_64-linux-gnu --host=arm-unknown-linux-gnueabihf --disable-ipv6 prefix=`pwd`/build
```

とかやると小さめのができるが、stripはしてくれていないみたい。

んでmake; make install

176MiBとかある

pyc, `__pycache__`を削除
62MB

encodingsがないと困ってしまうみたい。ここサイズでかいな。
などなど、必要なmoduleだけにしていったところ、

```shell
 $ du -h .
 1.8M    ./bin
 40K     ./lib/python3.6/encodings
 288K    ./lib/python3.6
 292K    ./lib
 2.1M    .
```

こんくらいまでは減らせた。

そこから import socketができるようにした段階

```shell
 1.8M    ./bin
 40K     ./lib/python3.6/encodings
 368K    ./lib/python3.6/lib-dynload
 56K     ./lib/python3.6/collections
 908K    ./lib/python3.6
 912K    ./lib
 2.7M    .
```


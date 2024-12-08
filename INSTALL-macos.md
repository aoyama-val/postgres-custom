pkgconfでライブラリにパスを調べる:

```
export PKG_CONFIG_PATH="/opt/homebrew/opt/icu4c@76/lib/pkgconfig:/opt/homebrew/opt/openssl@3.4/lib/pkgconfig"

$ pkgconf openssl --cflags
-I/opt/homebrew/Cellar/openssl@3/3.4.0/include

$ pkgconf openssl --libs
-L/opt/homebrew/Cellar/openssl@3/3.4.0/lib -lssl -lcrypto
```

調べたパスをexport:
```
export CFLAGS="-I/opt/homebrew/Cellar/openssl@3/3.4.0/include"
export LDFLAGS="-L/opt/homebrew/Cellar/openssl@3/3.4.0/lib -lssl -lcrypto"
```

configureしてインストール:
```
./configure --prefix=/opt/pg17 --with-ssl=openssl
make -j $(nproc) && make install
```

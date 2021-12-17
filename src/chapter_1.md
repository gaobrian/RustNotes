# Static linking with OpenSSL

如果程序使用了[openssl](https://docs.rs/openssl/latest/openssl/#)包，在进行静态编译时，需要按照下面的步骤执行

### 1. 设置相应的环境变量，相关的值可以用pkg-config查看

```bash
1.  export OPENSSL\_INCLUDE\_DIR=/usr/local/include/&#x20;

2.  export OPENSSL\_LIB\_DIR=/usr/local/lib

3.  export OPENSSL\_STATIC=yes

4.  export PKG_CONFIG=/usr/bin/pkg-config
```

```bash
> pkg-config --libs --cflags openssl
-I/usr/local/include -L/usr/local/lib -lssl -lcrypt
```

### 2. 设置编译参数并编译Rust代码

RUSTFLAGS="-C target-feature=+crt-static" cargo build --release  --frozen --offline


### Prerequisites
```
$ sudo apt update && sudo apt install git cmake autoconf automake libtool build-essential
$ cd ~ && git clone https://github.com/milkv-duo/host-tools.git
```
For Milk-V Duo (RISC-V)
========
```
$ cd ~
$ export PATH=$PATH:~/host-tools/gcc/riscv64-linux-musl-x86_64/bin
$ export CC=riscv64-unknown-linux-musl-gcc
$ git clone https://github.com/Nine9Seven/duo-wiringx.git && cd duo-wiringx/
$ rm -rf build && mkdir build && cd build
$ cmake .. -DCMAKE_SYSTEM_NAME=Linux -DCMAKE_SYSTEM_PROCESSOR=riscv64 -DCMAKE_C_COMPILER=$CC
$ make
```
### Verify
```
$ file libwiringx.so  # Should show "RISC-V"
```
### Deploy to Duo
```
$ ssh root@192.168.42.1 "mv /usr/lib/libwiringx.so /usr/lib/libwiringx.so.bak"
$ scp libwiringx.so root@192.168.42.1:/usr/lib/
$ scp wiringx-* root@192.168.42.1:/usr/sbin/
```
### Test blink
```
$ ssh root@192.168.42.1 "wiringx-blink milkv_duo256m 25"
```

For AArch64 (64-bit ARM)
========
```
$ cd ~
$ export PATH=$PATH:~/host-tools/gcc/gcc-linaro-7.3.1-2018.05-x86_64_aarch64-linux-gnu/bin
$ export CC=aarch64-linux-gnu-gcc
$ git clone https://github.com/Nine9Seven/duo-wiringx.git && cd duo-wiringx/
$ rm -rf build && mkdir build && cd build
$ cmake .. -DCMAKE_SYSTEM_NAME=Linux -DCMAKE_SYSTEM_PROCESSOR=aarch64 -DCMAKE_C_COMPILER=$CC
$ make
```
### Verify
```
$ file libwiringx.so  # Should show "ARM aarch64"
```
### Deploy to target
```
$ ssh root@192.168.42.1 "mv /usr/lib/libwiringx.so /usr/lib/libwiringx.so.bak"
$ scp libwiringx.so root@192.168.42.1:/usr/lib/
$ scp wiringx-* root@192.168.42.1:/usr/sbin/
```
### Test blink
```
$ wiringx-blink milkv_duo256m 25
```


Documentation
========
Please refer to the documentation at https://manual.wiringx.org or in the docs folder.
### Donations
donate@pilight.org

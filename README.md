# openssl-1.1.1d_mingw_static
Static build of openssl-1.1.1d With MinGW Compiler

- go https://www.openssl.org/source/ and download openssl source code desire your preferred version
- i choose openssl-1.1.1i.tar.gz file, it's lastest source code
- after downloaded, extract it, ie C:\openssl-1.1.1i
- to extract this, you need 7zip (download from this - https://www.7-zip.org/download.html)

- go https://www.msys2.org/wiki/MSYS2-installation/ and download 32bit or 64bit as you need
- i choose  to download 'msys2-x86_64-20210105.exe' and install this
- run msys2 console
- type 'pacman -S make perl' to install perl
- type 'pacman -S make msys2-devel' to install msys2-devel
- type 'pacman -S make libcrypt-devel'
- type 'pacman -S make perl-CPAN'
- type 'pacman -S mingw-w64-i686-gcc' if you need 32 bit
- type 'pacman -S mingw-w64-x86_64-gcc' if you need 64 bit
- install both mingw 32bit and 64bit if you have plan to build both 32bit/64bit release

After this, 
you need to set environment path
if you installed msys2 32 bit and want to build on 32 bit mingw
- export PATH="/c/msys2/mingw32/bin:$PATH"
if you installed msys2 64 bit and want to build on 64 bit mingw
- export PATH="/c/msys64/mingw32/bin:$PATH"
if you installed msys2 32 bit and want to build on 32 bit mingw
- export PATH="/c/msys32/mingw64/bin:$PATH"
if you installed msys2 64 bit and want to build on 64 bit mingw
- export PATH="/c/msys64/mingw64/bin:$PATH"

after this, check gcc path is ok for this command
- which gcc
if it shows gcc path, it's ok


now ready to build 
- make 'C:\openssl_release' dir for making release files
change dir path to openssl src file at this command
- 'cd /c/openssl-1.1.1i'
and make configure with this command
- './Configure --prefix=/c/openssl_release --openssldir=/c/openssl_release no-threads no-idea no-shared mignw' (32 bit mingw)
- './Configure --prefix=/c/openssl_release --openssldir=/c/openssl_release no-threads no-idea no-shared mignww64' (64 bit mingw)
if you need dynamic library, change no-shared to shared

after configure, ready to build type these commands
- make depend
- make 
- make install 

that's all 
your static library is on c:\openssl_release\lib

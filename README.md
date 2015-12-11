# react-native-ubuntu
Cara Setting development environment react-native di Ubuntu, beserta contoh aplikasi.
Pada contoh ini saya menggunakan Ubuntu 14.04 LTS dan sudah terinstall git.
Semua download zip ditaruh di folder

```bash
$ /home/(user)
```

Jika ada pertanyaan, silahkan bertanya di group Facebook [ReactJS Indonesia](https://www.facebook.com/groups/442974152553174/).

[Contoh Aplikasi](examples/README.md)

## Setting development environment react-native di ubuntu

Checklist yang harus dilakukan:

- [x] Install node.js v4.0 keatas atau menggunakan NVM
- [x] Install Watchman (beserta setting compability watchman di ubuntu)
- [x] Install Flow
- [x] Install & Setting Environment Variabel Android JDK dan SDK
- [x] Install SDK yang akan digunakan untuk react-native android
- [x] Install VirtualBox dan GenyMotion
- [x] Download dan Run virtual Device android
- [x] Install react-native-cli & init project
- [ ] Contoh menggunakan library 3rd party dari npm
- [ ] Deploy APK

## Install node.js v4.0 keatas atau menggunakan NVM

Pastikan node -v anda v4.0 keatas
untuk mengecek versi node anda

```bash
$ node -v
```

jika belum v4.0 keatas install [NVM](https://github.com/creationix/nvm#installation)
```bash
$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
```

Close dan buka terminal anda,
Install node 4.2.3 menggunakan NVM
```bash
$ nvm install 4.2.3
$ nvm use 4.2.3

$ node -v
$ #v4.2.3
$ nvm alias default node
```
## Install Watchman

Install [Watchman](https://facebook.github.io/watchman/docs/install.html). Jika './autogen.sh' tidak jalan, anda mungkin perlu menginstall automake 'sudo apt-get install automake' dan [python-dev](http://packages.ubuntu.com/search?keywords=python-dev).

```bash
$ git clone https://github.com/facebook/watchman.git
$ cd watchman
$ git checkout v4.1.0  # the latest stable release
$ ./autogen.sh
$ ./configure
$ make
$ sudo make install
```

### Setting Compability watchman pada ubuntu
Pada kondisi default, watchaman pada ubuntu hanya bisa jalan 1 user. Sehingga perintah 'react-native start' pada ubuntu hanya bisa jalan 1 kali (untuk start lagi harus merestart komputer).

Untuk memperbaikinya anda harus menambah value [inotify watchers](https://github.com/guard/listen/wiki/Increasing-the-amount-of-inotify-watchers) pada ubuntu.

## Install Flow
Flow saat ini support untuk arsitektur 64 bit, untuk ubuntu versi lain silahkan kunjungi [website flow](http://flowtype.org/docs/getting-started.html#_).

```bash
$ wget https://facebook.github.io/flow/downloads/flow-linux64-latest.zip
$ unzip flow-linux64-latest.zip
$ cd flow
$ echo -e "\nPATH=\"\$PATH:$(pwd)/\"" >> ~/.bashrc && source ~/.bashrc

$ flow version
$ #Flow, a static type checker for JavaScript, version 0.19.1
```

## Install & Setting Environment Variabel Android JDK dan SDK

untuk ubuntu 64bit 13.10 keatas, anda harus menginstall additional pacckage ini terlebih dahulu
```bash
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install libncurses5:i386 libstdc++6:i386 zlib1g:i386
```

Download [JDK](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
copy hasil download ke /home/(user) lalu jalankan perintah
```bash
$ tar -xvzf jdk-8u65-linux-x64.tar.gz
```

Download [standalone android SDK](https://developer.android.com/sdk/installing/index.html?pkg=tools)
copy hasil download ke /home/(user) lalu jalankan perintah
```bash
$ tar -xvzf android-sdk_r24.4.1-linux.tgz
```

```bash
$ nano ~/.bashrc
```

Akan terbuka nano text editor, lalu masukan kode berikut

```bash
#JavaDev PATH
export JAVA_HOME=~/jdk1.8.0_65
export PATH=$PATH:~/jdk1.8.0_65/bin
#AndroidDev PATH
export ANDROID_HOME=~/android-sdk-linux
export PATH=${PATH}:~/android-sdk-linux/tools
export PATH=${PATH}:~/android-sdk-linux/platform-tools
```

setelah itu save dengan menekan ctr+x enter, lalu Y dan enter.

```bash
$ nano ~/.bash_profile
```
Akan terbuka nano text editor, lalu masukan kode berikut

```bash
#JavaDev PATH
export JAVA_HOME=~/jdk1.8.0_65
export PATH=$PATH:~/jdk1.8.0_65/bin
#AndroidDev PATH
export ANDROID_HOME=~/android-sdk-linux
export PATH=${PATH}:~/android-sdk-linux/tools
export PATH=${PATH}:~/android-sdk-linux/platform-tools
```

Tutup dan buka lagi terminal.
lalu ketik
```bash
$ javac -version
$ #javac 1.8.0_65

$ android
```
Setelah dialog Android SDK Manager muncul tinggal menginstall SDK yang diperlukan

## Install SDK yang akan digunakan untuk react-native android
Install SDK seperti gambar dibawah ini

![SDK1](img/androidSDK1.png "react-native ubuntu Indonesia android SDK 1")
![SDK2](img/androidSDK2.png "react-native ubuntu Indonesia android SDK 2")

## Install VirtualBox dan GenyMotion

Silahkan download [GenyMotion & Virtualbox](https://www.genymotion.com/#!/developers/user-guide), ikuti langkah-langkah pada websitenya tinggal register dan download versi freenya.

## Download dan Run virtual Device android

Pada contoh ini saya menggunakan virtual device Sony Xperia Z
![Genymotion1](img/genymotion1.png "react-native ubuntu Indonesia genymotion 1")

Setelah selesai download, silahkan run virtual device.
Tampilan jika Genymotion berjalan dengan baik
![Genymotion1](img/genymotion2.png "react-native ubuntu Indonesia genymotion 2")

Tarik icon yang saya tandai dalam kotak merah keatas, agar mudah mengakses menu ReloadJS (pada saat develop react native nanti).

## Install react-native-cli & init project

```bash
$ sudo npm install -g react-native-cli #pastikan node -v anda 4.0 keatas
$ react-native init hariini
```
run watcher JS server react-native
```bash
$ react-native start
```
Buka terminal baru,
build project dan jalankan pada Genymotion (jangan ada device android yg terkonek dengan komputer saat perintah dijalankan)
```bash
$ react-native run-android
```
Jika muncul tampilan seperti ini, maka "SLAMAT!!", anda sukses men-setting development environment react-native di Ubuntu.

![ReactNativeUbuntu](img/react-native-ubuntu1.png "React Native Ubuntu")

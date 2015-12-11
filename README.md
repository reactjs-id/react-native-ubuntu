# react-native-ubuntu
Cara Setting development environtment react-native di Ubuntu, beserta contoh aplikasi.

Pada contoh ini saya menggunakan Ubuntu 14.04 LTS.

## Setting development environtment react-native di ubuntu

Checklist:

- [ ] Install node.js v4.0 keatas atau menggunakan NVM
- [ ] Install Watchman (beserta setting compability watchman di ubuntu)
- [ ] Install Flow
- [ ] Install Android SDK
- [ ] Setting Environtment Variable untuk ANDROID_HOME
- [ ] Install SDK yang akan digunakan untuk react-native android
- [ ] Install VirtualBox dan GenyMotion
- [ ] Download dan Run virtual Device android
- [ ] install react-native-cli
- [ ] Init project
- [ ] Contoh menggunakan library 3rd party dari npm
- [ ] Deploy APK

## Install node.js v4.0 keatas atau menggunakan NVM

Pastikan node -v anda v4.0 keatas
untuk mengecek versi node anda

- node -v

jika belum v4.0 keatas install [NVM](https://github.com/creationix/nvm#installation)

- curl -o- 'https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash'

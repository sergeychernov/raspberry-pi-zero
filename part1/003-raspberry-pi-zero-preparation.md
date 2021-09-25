# Подготовка Raspberry Pi Zero

## Установка операционной системы Linux на Raspberry PI Zero

Для начала установи последнюю версию Raspberry PI OS LITE (32-bit), используя [Raspberry Pi Imager](https://www.raspberrypi.org/software/)

## Подключите Raspberry PI к Wifi и включите ssh.

Сначала подключите вашу micro sd карту к компьютеру, компьютер увидет ее с именем тома boot. В корне тома создайте файл `wpa_supplicant.conf` со следующим содержанием:
```
country=RU
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
network={
    ssid="Имя Wifi сети"
    psk="Пароль Wifi сети"
    key_mgmt=WPA-PSK
}
```

Создайте пустой файл `ssh` в корне тома.

Безопасно отключите micro sd карту и вставьте ее в Raspberry PI.

Включаете ее, ждете пару минут и можете подключаться:

`ssh pi@ВАШ_IP`

ВАШ_IP адрес можно узнать, из списка подключенных устройств на роутере, либо подключив Raspberry PI к монитору, но для этого нужен переходник с mini HDMI.

## NodeJS установка

Подключаемся к Raspberry PI по ssh, как написано выше.

Скачиваем последний релиз nodejs, в примере 16.9.1 (помним, что начиная с 12 версии, они не стабильные, но для обучения это не имеет значения):

`wget https://unofficial-builds.nodejs.org/download/release/v16.9.1/node-v16.9.1-linux-armv6l.tar.xz`

Распаковываем архив:

`tar xvfJ node-v16.9.1-linux-armv6l.tar.xz node-v16.9.1-linux-armv6l/`

Копируем в дирректорию local:

`sudo cp -R node-v16.9.1-linux-armv6l/* /usr/local`

Удаляем архив и распакованную версию из домашней дирректории:

`rm -rf node-*`

Перезагружаем наш миникомпьютер:

`sudo reboot`

Ждем, подключаемся по ssh, как написано выше. Проверяем что все работает:

`node -v && npm -v`

## Установка Git

Git это система контроля версий. Дело в том, что мы не будем разрабатывать на raspberry pi zero, это возможно но абсолютно не удобно. Мы будем разрабатывать для raspberry pi zero на своем персональном компьютере. И git нам понадобится, чтобы поставлять наши программы на raspberry pi zero.

Чтобы установить git выполните следующую команду:

`sudo apt install git`

Если все прошло правильно, то следующая команда должна вывести версию git

`git --version`

Склонируйте данный репозиторий для продолжения

`git clone https://github.com/sergeychernov/raspberry-pi-zero.git`

## Выключение Raspberry PI

Чтобы выключить надо выполнить следующую команду:

`sudo shutdown -h now`

[К оглавлению](../README.md)

# Операционные системы и виртуализация (Linux)
## Подключение сторонних репозиториев, ручная установка пакетов
### 1. Подключить дополнительный репозиторий на выбор: Docker, Nginx, Oracle MySQL. Установить любой пакет из этого репозитория.

 - sudo apt install curl gnupg2 ca-certificates lsb-release ubuntu-keyring
 - curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor     | sudo tee /usr/share/keyrings/nginx-archive-keyring.gpg >/dev/null
 - gpg --dry-run --quiet --no-keyring --import --import-options import-show /usr/share/keyrings/nginx-archive-keyring.gpg
 - echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] \
http://nginx.org/packages/ubuntu `lsb_release -cs` nginx"     | sudo tee /etc/apt/sources.list.d/nginx.list
 - sudo apt-get update
 - sudo apt-get install nginx
### 2. Установить и удалить deb-пакет с помощью dpkg.
 - apt-get download apt-move
 - sudo dpkg -i apt-move_4.2.27-6_amd64.deb
### 3.* Установить и удалить snap-пакет
 - sudo snap install fifo

    fifo 1.2.2 от SnailDOS установлен
 - sudo snap list

    Название            Версия                      Правка  Канал          Издатель     Примечание

    fifo     1.2.2                       7       latest/stable  snaildos     -
 - sudo snap remove fifo
 - sudo snap list
 
    Название            Версия                      Правка  Канал          Издатель     Примечание
### 4. Добавить задачу для выполнения каждые 3 минуты (создание директории, запись в файл).
 - crontab -e

    */3 * * * * mkdir -p /home/roman/folder && echo test >> /home/roman/folder/file.txt
### 5. * Подключить PPA-репозиторий на выбор. Установить из него пакет. Удалить PPA из системы.
 - add-apt-repository ppa:someone/blablabla
 - sudo apt-get update
 - sudo apt-get install blablabla
 - sudo add-apt-repository --remove ppa:someone/blablabla

 ### 6. * Создать задачу резервного копирования (tar) домашнего каталога пользователя. Реализовать с использованием пользовательских crontab-файлов.
 - crontab -e
    
    \# Каждый месяц в 3 утра
    
    0 3 * * 1 tar -zcf /var/backups/home.tgz /home/  






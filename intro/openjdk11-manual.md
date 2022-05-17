# Инструкция по установке OpenJDK11

**Важно**: если у вас что-то не получилось, то оформляйте Issue [по установленным правилам](../report-requirements.md).

## Windows

Шаг 1. Перейдите на сайт [adoptopenjdk](https://adoptium.net/temurin/releases/?version=11). 

Шаг 2. Выберите среди списка подходящую для вашей операционной системы версию как на скриншоте ниже и нажмите на кнопку скачивания (главное выбрать 11ю версию джавы, другие цифры могут не совпадать):

![image](https://user-images.githubusercontent.com/53707586/168825819-184c203b-90f7-4d6d-9582-60d63d5c9e91.png)

Выбор между 32битной и 64битной версией. Узнать какая битность у вашей ОС можно по инструкции [тут](https://support.microsoft.com/ru-ru/windows/32-%D1%80%D0%B0%D0%B7%D1%80%D1%8F%D0%B4%D0%BD%D0%B0%D1%8F-%D0%B8-64-%D1%80%D0%B0%D0%B7%D1%80%D1%8F%D0%B4%D0%BD%D0%B0%D1%8F-%D0%B2%D0%B5%D1%80%D1%81%D0%B8%D1%8F-windows-%D0%B2%D0%BE%D0%BF%D1%80%D0%BE%D1%81%D1%8B-%D0%B8-%D0%BE%D1%82%D0%B2%D0%B5%D1%82%D1%8B-c6ca9541-8dce-4d48-0415-94a3faa2e13d).

Шаг 3. Запустите на установку скачанный MSI-файл и нажмите кнопку "Next":

![](pic/win-step1.png)

Шаг 4. Прочитайте и согласитесь с условиями лицензии:

![](pic/win-step2.png)

Шаг 5. Выберите опции как на экране (удостоверьтесь, что установка происходит в `Program Files` и опция `Add to PATH` выбрана):

![](pic/win-step3.png)

Шаг 6. Нажмите на кнопку "Install":

![](pic/win-step4.png)

Шаг 7. Дождитесь окончания установки и нажмите на кнопку "Finish":

![](pic/win-step5.png)

Откройте терминал и выполните команду:
```shell script
java -version
```

Вы должны увидеть вывод подобный:
```
openjdk version "11.0.5" 2019-10-15
OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.5+10)
OpenJDK 64-Bit Server VM AdoptOpenJDK (build 11.0.5+10, mixed mode)
```

**Важно**: вы должны открывать терминал уже после того, как произвели установку.

## MacOS

Шаг 1. Перейдите на сайт [adoptopenjdk.net](https://adoptium.net/temurin/releases/?version=11). 

Шаг 2. Выберите опции как на скриншоте ниже и нажмите на кнопку скачивания в соответствии с версии вашего мака:

![image](https://user-images.githubusercontent.com/53707586/168826353-0df847f5-73eb-4ce5-bd6d-16637da610ce.png)

Шаг 3. Запустите на установку скачанный PKG-файл и нажмите кнопку "Продолжить":

![](pic/mac-step1.png)

Шаг 4. Прочитайте и согласитесь с условиями лицензии:

![](pic/mac-step2.png)

Шаг 5. Выберите диск для установки:

![](pic/mac-step3.png)

Шаг 6. Нажмите на кнопку "Установить":

![](pic/mac-step4.png)

Шаг 7. Дождитесь окончания установки и нажмите на кнопку "Закрыть":

![](pic/mac-step5.png)

Откройте терминал и выполните команду:
```shell script
java -version
```
Вы должны увидеть вывод подобный:
```
openjdk version "11.0.5" 2019-10-15
OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.5+10)
OpenJDK 64-Bit Server VM AdoptOpenJDK (build 11.0.5+10, mixed mode)
```

**Важно**: вы должны открывать терминал уже после того, как произвели установку.

## Linux

Указанные инструкции приведены для дистрибутива Ubuntu 18.04+. Если у вас другой дистрибутив Linux - пишите в канал Slack.

Откройте консоль (`Ctrl + Alt + T` в Ubuntu 18+). В консоли выполните следующие команды:

```shell script
sudo apt update
sudo apt install openjdk-11-jdk openjdk-11-source
```

Удостоверьтесь, что java установлена:
```shell script
java -version
```

Вы должны увидеть вывод подобный:
```
openjdk version "11.0.5" 2019-10-15
OpenJDK Runtime Environment (build 11.0.5+10-post-Ubuntu-0ubuntu1.1)
OpenJDK 64-Bit Server VM (build 11.0.5+10-post-Ubuntu-0ubuntu1.1, mixed mode, sharing)
```

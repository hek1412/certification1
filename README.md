#                             Certification 1T (DevOps)
## Задание 1. Создание Docker-контейнера с простым Python-приложением
Это Docker-контейнер, который запускает Python-скрипт для анализа файловой системы и вывода приветствия.

Файл app.py запускает скрипт, который выполняет следующие задачи:
1) Вычисляет количество файлов в заданном пути (по умолчанию — корневой каталог файловой системы).
   *(Задание пути производится следующим образом: в скрипте app.py определяется переменная  path, содержащая путь например: /home/; если же переменная не определена (закомментирована), то используется корневой каталог файловой системы.)*
2) Выводит топ-10 файлов по размеру в заданном пути (по умолчанию — корневой каталог файловой системы)(в Кб).
3) Принимает аргумент с именем пользователя из командной строки при запуске контейнера для вывода приветствия с указанным именем, а также текущей даты и времени. (По умолчанию User)

Для монтирования контейнера используйте команду:
```
docker build -t work1-app . 
```
![Результат монтирования.](/docker%20build.png)

Пример команды запуска:
```
docker run --rm -e USER_NAME=SUPERUSER work1-app
```

После запуска контейнера вы должны увидеть вывод в терминале, который будет включать:
```
Привет, SUPERUSER! Текущая дата и время: 2024-11-17 19:51:26
Количество файлов в директории '/': 20941
Топ-10 файлов по размеру:
1. /sys/devices/LNXSYSTM:00/LNXSYBUS:00/ACPI0004:00/VMBUS:00/460fa902-2fd4-4118-bf08-206c98b7671c/pci2fd4:00/2fd4:00:00.0/resource4 - 8388608.00 KB
2. /sys/kernel/btf/vmlinux - 5677.99 KB
3. /usr/local/lib/libpython3.11.so - 5219.96 KB
4. /usr/local/lib/libpython3.11.so.1.0 - 5219.96 KB
5. /usr/lib/x86_64-linux-gnu/libcrypto.so.3 - 4619.27 KB
6. /usr/bin/perl5.36.0 - 3715.27 KB
7. /usr/bin/perl - 3715.27 KB
8. /usr/lib/x86_64-linux-gnu/libgnutls.so.30 - 2145.74 KB
9. /usr/lib/x86_64-linux-gnu/libgnutls.so.30.34.3 - 2145.74 KB
10. /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.30 - 2139.10 KB
```
![Результат выполнения.](/docker%20run.png)

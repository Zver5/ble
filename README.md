Xiaomi Flower Care, Mijia Sensor добавляем в Domoticz
=========================================================
* Создайте в Domoticz 4 виртуальных переключателя с именами для Xiaomi Flower Care
* Влажность %  (custom sensor)
* Температура °C (температура)
* Освещение (Lux) (освещенность)
* Удобрение uS/cm (custom sensor)
* Создайте в Domoticz виртуальный переключатель с типом Температура+влажность для Mijia запомните IDX
* Скачайте 
* `sudo git clone https://github.com/zver5/ble`
* перейдите в папку
* `cd ble`
* Запустите поиск устройств
* `sudo hcitool lescan`
* Нас интересует мак адрес у вас будет другой, к примеру:
* C4:7C:8D:62:0E:F4 Flower care =  это Xiaomi Flower Care
* 4C:65:A8:D0:45:D0 MJ_HT_V1 = это Mijia Sensor
==========================================================
* Добавим свой Xiaomi Flower Care, вводим в консоли
`sudo nano miflora.py`
* В открывшемся окне меняем, указывая ваш ip:порт Domoticz, листаем в самый вниз вписываем свой мак адрес и IDX созданного ранее датчика. Сохраняем файл.
* Проверяем работу 
`python3 miflora.py`
* Если вы получили показания значит все сделали правильно
===========================================================
* Добавим свой Mijia Sensor, вводим в консоли
`sudo nano domoticz_mijia.py`
* В открывшемся окне меняем, указывая ваш ip:порт Domoticz, листаем в самый вниз вписываем свой мак адрес и IDX созданного ранее датчика. Сохраняем файл.
* Проверяем работу 
`python3 domoticz_mijia.py`
* Если вы получили показания значит все сделали правильно
* Перемещаем файлы для дальнейшей работы 
* `cd ~/ble`
* `cp -r ble ~/domoticz/scripts/python/`
* `cp miflora.py ~/domoticz/scripts/python/miflora.py`
* `cp domoticz_mijia.py ~/domoticz/scripts/python/domoticz_mijia.py`
* переходим в папку 
 `cd ~/domoticz/scripts/python`
* Даем права файлам на выполнение
* `sudo chmod +x miflora.py`
* `sudo chmod +x domoticz_mijia.py`
* добавьте в crontab
* `*/30 * * * * /usr/bin/python3 /home/pi/domoticz/scripts/python/mijia-sensor-domoticz/domoticz_mijia.py >/dev/null 2>&1`
* `*/30 * * * * /usr/bin/python3 /home/pi/domoticz/scripts/python/miflora.py >/dev/null 2>&1`

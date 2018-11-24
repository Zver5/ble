Xiaomi Flower Care, Mijia Sensor, Bluetooth добавляем в Domoticz
===============================================
* Создайте в Domoticz два виртуальных переключателя с именами Mijia и Орхидея запомните их IDX
* Скачайте 
* `sudo git clone https://github.com/zver5/ble`
* перейдите в папку
* `cd ble`
* Запустите поиск устройств
* `sudo hcitool lescan`
* Нас интересует мак адрес  у вас булет другой!
* C4:7C:8D:62:0E:F4 Flower care = Xiaomi Flower Care
* 4C:65:A8:D0:45:D0 MJ_HT_V1 = Mijia Sensor
* Добавим сначала Xiaomi Flower Care, вводим в консоли 
`sudo nano miflora.py`
* в открывшемся окне меняем, указывая ваш ip:порт Domoticz, листаем в самый вниз вписываем свой мак адрес и IDX созданного ранее датчика. Сохраняем файл.
Проверяем работу 
`python3 miflora.py`
 если вы получили показания значит все сделали правильно
 * перемещаем файлы для дальнейшей работы 
* `cd ~/ble`
* `cp -r ble ~/domoticz/scripts/python/`
* `cp miflora.py ~/domoticz/scripts/python/miflora.py`
* `cp domoticz_mijia.py ~/domoticz/scripts/python/domoticz_mijia.py`
 переходим в папку 
 `cd ~/domoticz/scripts/python`
* Даем права файлу на выполнение
`sudo chmod +x miflora.py`





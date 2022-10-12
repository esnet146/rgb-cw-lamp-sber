# rgb-cw-lamp-sber
Прошивка умной лампочки от Сбера на модуле WBLC9 (чип BK7231T) и драйвере BP1658

Предназначена для работы из приложения сбера или через приложение от TUYA https://play.google.com/store/apps/details?id=com.tuya.smartlife&hl=ru&gl=US 

После прошивки ( основанной на тасмота ) может работать c MQTT брокером и управлятся локально из Home Assitaint, без всяких облаков и других глюков.

Программа для прошивки под питон https://github.com/OpenBekenIOT/hid_download_py ( ставим питон с офсайта )

Или просто windows приложение https://github.com/openshwprojects/OpenBK7231T/blob/master/bk_writer1.60.zip ( обязательно правильно выбрать чип - ни в коем случае не BK7231N или что-то еще. И работает не всегда под питоном все веселее ) 

Прошивки и подробные инструкции от автора тут: https://github.com/openshwprojects/OpenBK7231T_App

Открываем [релизы](https://github.com/openshwprojects/OpenBK7231T_App/releases) , скачиваем UA файл под чип BK7231T

![image](https://user-images.githubusercontent.com/64173457/195286727-aeb4b799-60ca-4d8e-a934-6c399074276c.png)

Например https://github.com/openshwprojects/OpenBK7231T_App/releases/download/1.12.103/OpenBK7231T_UA_1.12.103.bin

Для бэкапа нужна прога для работы с SPI флешем.  
Рекомендую NeoProgrammer ( https://4pda.to/forum/index.php?showtopic=884713&view=findpost&p=96411343 ),
или Asprogrammer ( https://github.com/nofeletru/UsbAsp-flash )
или еще куча разных других, но не все будут корректно определять флэш.
[NeoProgrammer_2.2.0.10.zip](https://github.com/esnet146/rgb-cw-lamp-sber/files/9763350/NeoProgrammer_2.2.0.10.zip)
[USBASP_USBISP_Driver_and_Firmware.zip](https://github.com/esnet146/rgb-cw-lamp-sber/files/9763354/USBASP_USBISP_Driver_and_Firmware.zip)


Риски: сломать при разборке ( нужны прямые руки и немного инструмента ), при прошивке аккуратнее - не сотрите загрузчик, , не сотрите калибровки ( всегда можно восстановить из полного бэкапа, даже чужого, если дадут, но только через spi программатор )

Упаковка и маркировка

![msg1652874704-36669](https://user-images.githubusercontent.com/64173457/195269552-a5eb8cb0-0087-45f1-ba43-0c86f336c0cf.jpg)
![msg1652874704-36670](https://user-images.githubusercontent.com/64173457/195269545-0e5f60ec-3beb-40f9-8329-870e8e616069.jpg)
Описание модуля https://developer.tuya.com/en/docs/iot/wblc9-module-datasheet?id=K9hgglry2jp5h

Разборка:

Нагреваем феном паяльной станции обод лампы в месте крепления плафона с корпусом:

![msg1652874704-36673](https://user-images.githubusercontent.com/64173457/195270192-eeff047d-b255-499a-8e21-6a8ca91aeda2.jpg)
![msg1652874704-36671](https://user-images.githubusercontent.com/64173457/195270193-815748e8-3d77-401a-bb05-dc3d99a3e8ef.jpg)

Пока горяченькая берем одной рукой за корпус, другой за плафон и раскачивая отсоединяем плафон от корпуса ( разламывать не нужно, ковырять ножиками тоже! )

Снимаем центральный контакт цоколя

![msg1652874704-36676](https://user-images.githubusercontent.com/64173457/195271157-b295cb1f-8b05-4677-a5ba-f25deebadec6.jpg)

Снимаем резьбовой контакт цоколя, аккуратно тупым ножом сдвигая с корпуса по кругу, потихоньку, ничего не сгибая и не прорезая

![msg1652874704-36677](https://user-images.githubusercontent.com/64173457/195271650-26155e1a-7540-4149-a99d-919bc20b6f52.jpg)
![msg1652874704-36678](https://user-images.githubusercontent.com/64173457/195271686-ac7d7af9-5cf1-4899-b422-4e10750d9535.jpg)

срезаем заводской клей с верхней части светодиодной матрицы, не царапая подложку матрицы, без фанатизма, главное - освобоить самый край матрицы у корпуса лампы ( ну и красоту навести)

![msg1652874704-36680](https://user-images.githubusercontent.com/64173457/195272100-3097d64a-bc9c-4620-afdb-38c3f51a8509.jpg)

аккуратно вставляем внутрь лампы отвертку, достаточно тонкую и крепкую. Главное - не оторвать ничего внутри, берем конструкцию в руки, упираем отвертку в край матрицы и выталкиваем весь пакет из корпуса преодолевая сопротивление остатков клея и фиксатора матрицы в радиаторе корпуса лампы. Берегите руки, не проткните их отверткой, они еще пригодятся. не сломайте ничего внутри лампы и светодиодную матрицу, они нужны.

![msg1652874704-36679](https://user-images.githubusercontent.com/64173457/195272932-6ba335be-289e-449d-863a-095b2abf1c61.jpg)

Отсоединяем матрицу от платы управлениея ( необязательно, но дальше работать будет удобнее )

![msg1652874704-36681](https://user-images.githubusercontent.com/64173457/195274072-acb08f37-1176-482f-974e-a5f91d4448f4.jpg)

Облуживаем точки подключения

![msg1652874704-36685](https://user-images.githubusercontent.com/64173457/195281837-057672c5-c5df-4d7d-8765-f21e7ce253c5.jpg)

Припаиваем внешнее питание ( пока не подключаем, нужно будет уже при работе с прошивкой )

![msg1652874704-36682](https://user-images.githubusercontent.com/64173457/195282183-be4c12bc-4ef1-4572-8237-c9792ba913d1.jpg)

Далее определитесь: если нужно сохранить возможность вернуть обратно возможность работы с облаком - нужен бэкап внутренней флешки чипа и программатор SPI. Например совсем не дорогой CH341A. Другой вариант - сразу безвозратно прошить для работы через MQTT брокер и забыть навсегда про tuya. Тогда нужен просто любой UART и можно пропустить все что связано с чтением, а перейти сразу к прошивке.

Бэкап внутренней памяти:

Берем SPI программатор

![image](https://user-images.githubusercontent.com/64173457/195288277-49069350-1e15-4f58-a919-fc451d045431.png)

Подключаем к модулю 4 провода шины SPI, CEN, сразу первый UART и питание ( внешнее 3,3 вольта или с CH243a )

![image](https://user-images.githubusercontent.com/64173457/195291562-6e441003-2683-44fb-862b-d4bfd16b6061.png)

схема TP и контактов

![photo_5345780381711974440_y](https://user-images.githubusercontent.com/64173457/195275589-a5aa3367-8504-4cd9-802f-dfdd666ca6b7.jpg)

Паятся тонкими проводами ( МГТФ или обмоточный с катушек ) никогда не дергать во избежании отрыва TP от платы. потом будет значительно сложнее подключится.

![msg1652874704-36684](https://user-images.githubusercontent.com/64173457/195297084-1559ecaa-66ca-40a8-9039-7b7925e17588.jpg)

Для перевода чипа в режим доступа к памяти для программы нужен скрипт, набросал вот такой:
```
{$ INIT_AND_READ_FLASH_ID}
begin
  ID:= CreateByteArray(4);
  RESP:= CreateByteArray(250);
  if not SPIEnterProgMode(_SPI_SPEED_MAX) then LogPrint('Error setting SPI speed');
  LogPrint ('Read JEDEC ID');
    // init SPI
  for i:=0 to 250 do
  begin
    SPIWrite (0, 1, $D2);
    ProgressBar(1);
  end;
    // read response
  SPIRead(1, 3, ID);
    // logprint('RESP: ' + inttohex((GetArrayItem(RESP, 0)),2)+ inttohex((GetArrayItem(RESP, 1)),2));
    // read ID to test installation
  SPIWrite (0, 4, $9F, $00, $00, $00);
  SPIRead(1, 4, ID);
  logprint('CHIP ID: ' + inttohex((GetArrayItem(ID, 2)),2) + inttohex((GetArrayItem(ID, 1)),2)+ inttohex((GetArrayItem(ID, 0)),2));
  LogPrint ('End read JEDEC ID');
  SPIExitProgMode ();
end
```
Тайный смысл - послать в чип 250 сиволов D2 и прочитать идентификатор флэша. Это нужно сделать сразу после сброса ( или подачи питания на чип )
Далее чип остается в режиме доступа к памяти пока не перезагрузим. нужно положить файл с таким содержимым в папку со скриптами ПО программатора

Подключаем программатор, ( перемычка режима работы установлена ), загружаем скрипт, выбираем секцию
Нажимаем на кнопку ( CEN на землю ), запускаем скрипт на исполнение и в тот же момент отпускаем кнопку ( убираем землю с CEN )
Ждем цифр 15701 в логе программатора. если есть - отлично. если там в id чипа нули - повторяем пока не получится.

Жмем кнопку "Detect" в ПО программатора и выбираем чип EN25Q16

Жмем Read IC и читаем флешку, в логе должно быть так:
```
Currently selected: EN25QH16 [3.3V] 16 Mbits, 2 Mbytes
---------------------------------------------------------------------------
Current programmer: CH341 Black
21:19:22
Reading memory... Main Memory
Success
Execution time: 00:00:17.072
CRC32 = 0x********
```
Жмем в меню File  и  Save, сохраняем наш дамп в надежном месте. Бэкап готов.

Прошивка нового ПО:

Переводим CH341 в режим UART ( снимаем перемычку и перетыкаем в usb порту)

Или подключаем rx tx через любой UART 

для загрузки из питоновского коплекта uartprogram правим компорт и имя файла прошивки ( адрес загруки по умолчанию 0x11000 )
```
python uartprogram c:\temp\OpenBK7231T_UA_1.12.103.bin -d COM3 -w
```
или в BKwriter 1.60 exe указываем порт,имя файла для прошивки и чип BK7231 ( не N !!!) адрес загрузки не должен быть равен нулю!!!

Если у вас хитрый уарт который не может работать на скорости 921600 укажите скорость порта.
```
python uartprogram c:\temp\OpenBK7231T_UA_1.12.103.bin -d COM3 --baudrate 115200 -w
```

теперь давим кнопку коротя CEN на землю, запускаем запись прошивки, отпускаем кнопку. Если через 3 секунды процесс прошики не запустился - жмем на кнопку еще секунду.
 Если закончилось время ожидания прошивальщика - повторяем до достижения нужного результата.
 ![image](https://user-images.githubusercontent.com/64173457/195309879-bd15b9c7-cfc6-493b-8651-3f21447e5391.png)
 
После прошивки запустится точка доступа с открытой сетью. подключаемся. по адресу 192.168.4.1 будет web-морда конфигуратора.

![image](https://user-images.githubusercontent.com/64173457/195342867-c27c0ca4-9699-4378-9ec5-a66e00a921f2.png)

Настраиваем: 
```
Configure module:
P24 выбираем BP1658CJ_DAT
P26 выбираем BP1658CJ_CLK
```
![image](https://user-images.githubusercontent.com/64173457/195343274-297fda76-9396-421d-85a0-cfdfbd335ca9.png)

Configure General:

Ставим галочку на Flag4 ( Если нужно включать в предыдущем состоянии при подаче питания то и галочку на flag12 )

![image](https://user-images.githubusercontent.com/64173457/195343548-96e13e51-394d-47f5-b98c-3dc9d490374f.png)


Change Startup command text:

BP1658CJ_Map 2 1 0 4 3 ( порядок цветов. у меня так, если нужно можно изменить: 01234 это будет rgbcw )

![image](https://user-images.githubusercontent.com/64173457/195343784-6b725f3e-a000-4bbe-8d0c-765356b43391.png)


Прописываем ip MQTT брокера, топик, логин, пароль. Само в Home assistaint не приползет. Нужно прописать в configuration.yaml как-то так, например, исправивь имя топика
```
mqtt:
  light:
  - unique_id: "Name_Id"
    name: "Name"
    rgb_command_template: "{{ '%02x%02x%02x' | format(red, green, blue)}}"
    rgb_state_topic: "obkMAC/led_basecolor_rgb/get"
    rgb_command_topic: "cmnd/obkMAC/led_basecolor_rgb"
    rgb_value_template: "{{ value[0:2]|int(base=16) }},{{ value[2:4]|int(base=16) }},{{ value[4:6]|int(base=16) }}"
    command_topic: "cmnd/obkMAC/led_enableAll"
    state_topic: "obkMAC/led_enableAll/get"
    availability_topic: "obkMAC/connected"
    payload_on: "1"
    payload_off: "0"
    brightness_command_topic: "cmnd/obkMAC/led_dimmer"
    brightness_scale: 100
    brightness_state_topic: "obkMAC/led_dimmer/get"
    brightness_value_template: "{{value}}"
    color_temp_command_topic: "cmnd/obkMAC/led_temperature"
    color_temp_state_topic: "obkMAC/led_temperature/get"
    retain: true
```
В итоге получается так:

![image](https://user-images.githubusercontent.com/64173457/195317594-a0277494-b401-46f6-aa06-9c95890d3185.png)
![image](https://user-images.githubusercontent.com/64173457/195317650-82e83b80-d128-4cc6-94a3-9272b836f527.png)
![image](https://user-images.githubusercontent.com/64173457/195317714-3a7171c2-16bb-4f74-9c02-9f6460e6bd54.png)
![image](https://user-images.githubusercontent.com/64173457/195317798-31f11951-de68-4c4c-abd0-afb4aa9b7a36.png)

Выражаю огромную благодарность пользователям [btsimonh](https://github.com/btsimonh) и [Refuhr](https://github.com/Refuhr) !




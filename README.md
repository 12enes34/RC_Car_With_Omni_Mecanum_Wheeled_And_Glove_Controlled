# README in Two Languages: Rc Car With Mecanium Wheels And Glove Conrtolled

![Car](https://github.com/12enes34/Camera_RC_Car_With_Omni_Mecanum_Wheeled_And_Glove_Controlled/blob/main/omniProject-ezgif.com-crop.gif)


- [Türkçe](#turkce-bolum)
- [English](#english-section)


<h1 align="center" style="font-size: 62px;" id="turkce-bolum">TÜRKÇE</h1>
# Mecanium Tekerlekli ve Eldiven Kontrollü Rc Araba

Bu proje, omni tekerlekler kullanarak hareket eden bir mobil robot geliştirme üzerine odaklanmaktadır. Araç, dört yönlü hareket kabiliyetine sahip olup, joystick ile kontrol edilebilir ve çeşitli görevler için özelleştirilebilir.

## Proje Özeti

Omni tekerlekler, aracın herhangi bir yönde kolayca hareket etmesine olanak sağlar. Projede, [ESP32-S3 mini](https://www.espressif.com/en/products/socs/esp32-s3) mikrodenetleyici ve çeşitli sensörler (ADXL345 gibi) kullanılarak stabil hareket ve veri toplama işlemleri gerçekleştirilmiştir.Aynı zamanda mobil uygulaması tasarlanmış olup aracın mobilden kontrol edilmeside sağlanmıştır.

### Özellikler:
- **Çok yönlü hareket**: 360 derece dönme, yan hareketler, ileri ve geri.
- **Joystick ile kontrol**: Kolay ve hassas yönlendirme.
- **Mobil ile kontrol**: Pratik kullanım.
- **Motor kontrol**: ADXL345 sensörü ile hareket doğrultusunda hassas ayarlamalar.
- **Wi-Fi bağlantısı**: ESP32 üzerinden kablosuz kontrol.
- **Gerçek zamanlı veri izleme**: Sensör verilerinin anlık takibi.

## Gereksinimler

Bu projeyi çalıştırmak için aşağıdaki donanım ve yazılım gereksinimleri karşılanmalıdır:

### Donanım:
- Omni tekerlekli araç platformu
- 4 adet 6V dc motor
- [ESP32-S3 mini](https://www.espressif.com/en/products/socs/esp32-s3)
- [ESP8266](https://www.espressif.com/en/products/socs/esp8266)(Elimde üzerinde oled ekranlı versiyonu vardı onu kullandım)
- ADXL345 ivmeölçer
- Motor sürücüleri
- 12V-9V batarya
- Joystick modülü (opsiyonel)
- Hotspot özelliği bulunan bir telefon

### Yazılım:
- Python 3.x
- Arduino IDE (ESP32 kütüphaneleri)
- MicroPython
- Unity C#

## Kurulum

### Donanım Bağlantıları:
- **ESP32-S3 mini** pinlerine motor sürücüler bağlanmalıdır.

| Cihaz               | ESP32 S3 Pin|
|---------------------|-------------|
| Front_Left_PWM   | 6              |
| Front_Right_PWM  | 1              |
| Front_Left_in1   | 5              |
| Front_Left_in2   | 4              |
| Front_Right_in3  | 2              |
| Front_Right_in4  | 3              |
| Behind_Left_PWM  | 8              |
| Behind_Right_PWM | 13             |
| Behind_Left_in1  | 9              |
| Behind_Left_in2  | 10             |
| Behind_Right_in3 | 12             |
| Behind_Right_in4 | 11             |

Motor sürücülerin + ve - girişlerine 9v - 12V arası bir batarya bağlanmalıdır.

- **ESP8266** pinlerine I2C üzerinden ivmeölçer bağlanmalıdır.

| Cihaz               | ESP8266 Pin |
|---------------------|-------------|
| SCL                 | 5           |
| SDA                 | 4           |

**Opsiyonel** Oled ekran varsa 
| Cihaz               | ESP8266 Pin |
|---------------------|-------------|
| SCL                 | 12          |
| SDA                 | 14          |

- 6V dc motorlar yerleştirilir
- Araç gövdesine uygun omni tekerlekler yerleştirilir.

### Yazılım Adımları:
1. ESP32'yi Arduino IDE ile programlamak için gerekli sürücüleri yükleyin.
2. TCP ile kurmak istiyorsanız Car/TCP/ klasörü altındaki dosyayı esp32 ye yükleyin<br>
   UDP ile kurmak istiyorsanız Car/UDP/ klasörü altındaki dosyayı esp32 ye yükleyin
4. ESP8266'yı MicroPython ile programlamak için gerekli sürücüleri yükleyin.
5. TCP ile kurmak istiyorsanız Glove_Control/TCP/ klasörü altındaki dosyayı esp8266 ya yükleyin<br>
   UDP ile kurmak istiyorsanız Glove_Control/UDP/ klasörü altındaki dosyayı esp8266 ya yükleyin
6. Pc üzerinden kontrol etmek istiyorsanız Pc nizin hotspotunu açın ve eps32 nin kodlarının içinde belirlediğiniz Wifi adını ve şifresini girin sonra idenizden UDP için Pc_Control/PcControllerEsp32S3UDP.py , TCP için PcControllEsp32S3TCP.py dosyasını açın ve esp32'nizin ip numarasını değiştirip çalıştırın.
7. Mobil üzerinden kontrol etmek istiyorsanız Omni Car Controller mobil app'i telefonunuza kurun Hotspotunuzu açın ve aracın üzerinde mavi yeşil yanan ledin sabit mavi yanmasını bekleyin.Uygulamayı açdıktan sonra en üst orta konumda bulunan IP kısmına esp32s3 ' ün IP 'sini yazın, en üst sol köşeden maksimum hızı ayarlayabilirsiniz(varsayılan hız 155).
NOT:Varsayılan Wifi:Tulpar Şifre:12345687


Artık hazırsınız.

### Mobil Kullanım Adımları:
Mobil applikasyon üzerindeki joystick ile aracı ileri geri ve kendi etrafında hareket ettirebilirsiniz.
Joystick üzerinde bulunan sağa ve sola olan oklar ile de aracın ok yönünde yengeç yürüyüşü yapmasını sağlayabilirsiniz.
Sağ tarafda bulunan yönlendirme okları ile de okun yönüne göre çapraz yengeç yürüyüşü gerçekleştirebilirsiniz.
Sağ tarafda bulunan ses butonu ile de aracın melodi çalmasını sağlayabilirsiniz.
Sol üst tarafda bulunan Max Hız değişkenine 50-255 arasında bir değer girerek aracın maximum hızını belirleyebilirsiniz.

### Kullanım Adımları:

| Hareket               |Tuş|
|-----------------------|---|
| İleri                 | w |
| Geri                  | s |
| 360 dönüş sağdan      | d |
| 360 dönüş soldan      | a |
| Sağa yengeç yürüyüşü  | e |
| Sola yengeç yürüyüşü  | q |
| Sol üst çapraza       | r |
| Sağ üst çapraza       | t |
| Sol alt çapraza       | f |
| Sağ alt çapraza       | g |
| Arka sabit sağa       | u |
| Arka sabit sola       | y |
| Ön sabit sağa         | j |
| Ön sabit sola         | h |
| Sağ sabit sağa        | z |
| Sağ sabit sola        | x |
| Sol sabit sağa        | v |
| Sol sabit sola        | c |

Not eldiven ile kontrolde UDP önerilir
Eldivenin baglanması için en az 10 sn eldiveni yere paralel sabit tutmanız tavsiye edilir.

   
<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

<h1 align="center" style="font-size: 62px;" id="english-section">ENGLISH</h1>
# Mecanium Wheeled and Glove Controlled Rc Car

This project focuses on the development of a mobile robot that moves using omni wheels. The vehicle has four-way mobility, can be controlled with a joystick and can be customized for various tasks.

## Project Summary

Omni wheels allow the vehicle to move easily in any direction. In the project, [ESP32-S3 mini](https://www.espressif.com/en/products/socs/esp32-s3 ) stable motion and data acquisition operations were performed using a microcontroller and various sensors (such as the ADXL345).At the same time, a mobile application has been designed and the vehicle can be controlled from a mobile device.

### Features:
-**Multi-directional movement**: 360 degree rotation, side movements, forward and backward.
- **Control by joystick**: Easy and precise orientation.
- **Control via mobile**: Practical use.
- **Motor control**: Precise adjustments in the direction of movement with the ADXL345 sensor.
- **Wi-Fi connection**: Wireless control via ESP32.
- **Real-time data monitoring**: Instant tracking of sensor data.

## Requirements

To run this project, the following hardware and software requirements must be met:

### Hardware:
- Omni wheeled vehicle platform
- 4 pcs 6V dc motor
- [ESP32-S3 mini](https://www.espressif.com/en/products/socs/esp32-s3 )
- [ESP8266](https://www.espressif.com/en/products/socs/esp8266 )(I had an oled screen version on it, I used it)
- ADXL345 accelerometer
- Engine drivers
- 12V-9V battery
- Joystick module (optional)
- A phone with hotspot feature

### Software:
- Python 3.x
- Arduino IDE (ESP32 libraries)
- MicroPython

## Installation

### Hardware Connections:
-**Motor drives must be connected to the ESP32-S3 mini** pins.

| Device  | ESP32 S3 Pin |
|--------------------|---|
| Front_Left_PWM     | 6 |
| Front_Right_PWM    | 1 |
| Front_Left_in1     | 5 |
| Front_Left_in2     | 4 |
| Front_Right_in3    | 2 |
| Front_Right_in4    | 3 |
| Behind_Left_PWM    | 8 |
| Behind_Right_PWM   | 13|
| Behind_Left_in1    | 9 |
| Behind_Left_in2    | 10|
| Behind_Right_in3   | 12|
| Behind_Right_in4   | 11|

A battery between 9 Dec- 12 V must be connected to the + and - inputs of the motor drives.

- **Accelerometer must be connected to ESP8266** pins via I2C.

| Device | ESP8266 Pin |
|---------------------|-------------|
| SCL | 5 |
| SDA | 4 |

**Optional** If there is an Oled screen 
| Device | ESP8266 Pin |
|--------|-------------|
| SCL    |       12    |
| SDA    |       14    |

- Suitable omni wheels are placed on the vehicle body.

### Software Steps:
1. Install the necessary drivers to program the ESP32 with the Arduino IDE.
2. If you want to install it with TCP, upload the file under the Car/TCP/ folder to esp32<br>
   If you want to install it with UDP, upload the file under the Car/UDP/ folder to esp32
4. Install the necessary drivers to program the ESP8266 with MicroPython.
5. If you want to install it with TCP, upload the file under the Glove_Control/TCP/ folder to esp8266<br>
   If you want to install it with UDP, upload the file under the Glove_Control/UDP/ folder to esp8266
6. If you want to control it via a PC, open your PC's hotspot and enter the Wifi name and password that you set in the eps32 codes, and then use your ID for UDP Pc_Control/PcControllerEsp32S3UDP.py , For TCP PcControllEsp32S3TCP.py open the file and change the ip number of your esp32 and run it.
7. If you want to control it via mobile, install the Omni Car Controller mobile app on your phone. Turn on your hotspot and wait for the blue-green led on the vehicle to turn solid blue. After opening the application, write the IP of the esp32s3 in the IP section at the top middle position, at the top You can set the maximum speed from the left corner (default speed is 155).
NOTE: Default Wifi: Tulpar Password: 12345687

You're ready now.

### Mobile Usage Steps:
You can move the vehicle back and forth and around itself with the joystick on the mobile application.
You can also make the vehicle crab walk in the direction of the arrow with the right and left arrows on the joystick.
With the direction arrows on the right, you can perform a diagonal crab walk according to the direction of the arrow.
You can also make the vehicle play a melody with the volume button on the right side.
You can determine the maximum speed of the vehicle by entering a value between 50-255 in the Max Speed ​​variable on the top left.

### Steps of Use:

| Movement                    |Key|
|-----------------------------|---|
| Forward                     | w |
| Back                        | s |
| 360 turns from the right    | d |
| 360 turns from the left     | a |
| Crab walk to the right      | e |
| Crab walk to the left       | q |
| To the upper left diagonal  | r |
| To the upper right diagonal | t |
| To the lower left diagonal  | f |
| To the lower right diagonal | g |
| Rear fixed to the right     | u |
| Rear fixed to the left      | y |
| Front fixed to the right    | j |
| Front fixed to the left     | h |
| Right hard right            | z |
| Right constant left         | x |
| Left hard right             | v |
| Left fixed left             | c |

Note UDP is recommended for control with gloves
It is recommended to keep the glove stationary parallel to the ground for at least 10 seconds to connect the glove.

1.ESP8266连接：确保串口正常使用；RST->AT->AT+CWMODE->CWJAP->CIPSTART;

        CWJAP连接WIFI,CIPSTART连接平台网站；

2.与平台进行连接：调用MQTT协议包，

3.进行消息的发布：设置发送间隔，用JSON格式进行发送

4.通过ESP8266获取平台下发的数据，捕获数据包，在调用解包函数进行解包，利用 cJSON进行解包，获取信息，进行设备的控制。

{"clientId":"k19g7hBjoOD.testdevice1|securemode=2,signmethod=hmacsha256,timestamp=1729065411543|",
    "username":"testdevice1&k19g7hBjoOD",
    "mqttHostUrl":"iot-06z00d9jq7p2pgk.mqtt.iothub.aliyuncs.com",
    "passwd":"7b2e3f79724bdb04e581d822a04044129a11c8cd4e8fc4bdfec69ee335de7e05",
    "port":1883}





阿里云平台连接：

1.创建一个公共实例，若该实例有ID则为新公共实例

![8c7c30f8-753c-4237-b990-cf84ed5c9ff8](file:///C:/Users/SHARK/Pictures/Typedown/8c7c30f8-753c-4237-b990-cf84ed5c9ff8.png)

2.创建一个产品

[如何在物联网平台创建产品_物联网平台(IoT)-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/iot/user-guide/create-a-product?spm=5176.11485173.console-base_help.dexternal.4f2e59afF4dTYD)

可在上方选择地区

点击实例 -->设备管理 -->产品-->创建产品（MQTT:只可以选新建产品，建议选择自定义品类，联网方式依据自己需求选择，其它不用管 ）

3.创建一个设备

[物联网平台中注册单个设备_物联网平台(IoT)-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/iot/user-guide/create-a-device?spm=5176.11485173.console-base_help.dexternal.4f2e59afF4dTYD)

点击设备-->添加设备-->选择要添加的产品-->输入devicebname

![bd0c3635-6321-4259-ba39-9c7aa7628941](file:///C:/Users/SHARK/Pictures/Typedown/bd0c3635-6321-4259-ba39-9c7aa7628941.png)

4.创建物模型

[定义物模型属性、事件和服务_物联网平台(IoT)-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/iot/user-guide/add-a-tsl-feature?spm=5176.11485173.console-base_help.dexternal.4f2e59afF4dTYD)

点击产品-->查看产品-->功能定义-->编辑草稿

<img src="file:///C:/Users/SHARK/Pictures/Typedown/8004e5b6-8283-4c12-b88a-a60058c601f9.png" title="" alt="8004e5b6-8283-4c12-b88a-a60058c601f9" style="zoom:50%;">

（MQTT设备不可添加物模型，这里添加自定义功能）

![0064b707-9f87-4b68-86f1-7d12ae01e7f4](file:///C:/Users/SHARK/Pictures/Typedown/0064b707-9f87-4b68-86f1-7d12ae01e7f4.png)

最后点击 **发布上线**（发布上线后才会有效，不同于产品发布）

![dec7154b-03aa-497c-846d-ceb50b6127b4](file:///C:/Users/SHARK/Pictures/Typedown/dec7154b-03aa-497c-846d-ceb50b6127b4.png)

5.根据自己需求可以加主题

![79d0a993-eef2-4d5d-9247-dad321aa2893](file:///C:/Users/SHARK/Pictures/Typedown/79d0a993-eef2-4d5d-9247-dad321aa2893.png)



6.选择接入阿里云方式

[物联网平台LinkSDK集成方式和功能特性_物联网平台(IoT)-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/iot/developer-reference/link-sdks?spm=5176.11485173.console-base_help.dexternal.4f2e59afF4dTYD)

[使用TLS加密设备和物联网平台的MQTT通信_物联网平台(IoT)-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/iot/user-guide/establish-mqtt-connections-over-tcp?spm=a2c4g.11186623.0.i2)

[如何计算MQTT签名参数_物联网平台(IoT)-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/iot/user-guide/how-do-i-obtain-mqtt-parameters-for-authentication?spm=a2c4g.11186623.0.0.6fc2283cwa1lxp#task-2100587)

[如何下载设备端SDK_物联网平台(IoT)-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/iot/user-guide/download-device-sdks?spm=a2c4g.11186623.0.0.7df23b30NiJ9vP)

   1.选择SDK，这里暂不使用

    2.MQTT自主协议接入

![7a6d7c3e-d0ab-46b4-8bba-7ea2e58e3535](file:///C:/Users/SHARK/Pictures/Typedown/7a6d7c3e-d0ab-46b4-8bba-7ea2e58e3535.png)

这里选择MQTT-TLS的一机一密接入

![17757b94-cf1a-4c74-83c5-2e41a8a1f989](file:///C:/Users/SHARK/Pictures/Typedown/17757b94-cf1a-4c74-83c5-2e41a8a1f989.png)

![e70bf833-b869-4888-8617-d7c066c63f97](file:///C:/Users/SHARK/Pictures/Typedown/e70bf833-b869-4888-8617-d7c066c63f97.png)

![fa5de728-3b4f-4fbc-a7f8-3a51bb26aa2c](file:///C:/Users/SHARK/Pictures/Typedown/fa5de728-3b4f-4fbc-a7f8-3a51bb26aa2c.png)

踩的坑（开始没有仔细看阿里的开发文档，直接看的github上的博客，改一下别人的配置，准备复刻一下，发现一直登录不上去，然后又参考了好几份代码和案例，还是不行，也没搞懂，最后发现他们连接的方式和阿里给的案例有所不同。

于是开始研究阿里的文档，发现通过接入阿里云有很多方式，大致分为用SDK接入和协议自主接入

![481e268e-b444-444a-b60d-9b02fd0286f3](file:///C:/Users/SHARK/Pictures/Typedown/481e268e-b444-444a-b60d-9b02fd0286f3.png)

![ae72edb6-dede-459f-a9be-2094aea67bb6](file:///C:/Users/SHARK/Pictures/Typedown/ae72edb6-dede-459f-a9be-2094aea67bb6.png)（MQTT,HTTPS,COAP,ALINK））,而我们要使用的就是MQTT协议；而MQTT协议接入又分好几种

![1601960c-0248-4884-aa64-cee1bd941152](file:///C:/Users/SHARK/Pictures/Typedown/1601960c-0248-4884-aa64-cee1bd941152.png)

只有企业版本支持MQTT5.0

所以就剩下四种方式

MQTT-TLS ： 设备和物联网平台使用发布/订阅模式的MQTT进行通信。

MQTT-WEBSOCKET :物联网平台支持基于WebSocket的MQTT协议,与浏览器上的应用程序通信。



MQTT-IPV6 :可以使用MQTT直连方式，直接接入物联网平台



这里选择使用MQTT-TLS协议接入;









二、STM32+ESP8266配置

ESP8266: 无需烧录MQTT固件，拿到手里调试好基本的AT指令，能连上网就能用



STM32配置：

                ESP866-USART3

                DEBUG-USART1

                DHT11-1WIRE

                LIGHTSENSOR-AD

                LED-PIN

            阿里云连接需要的文件：

                   串口收发驱动、ESP8266连接路由器、通过TCP接入到MQTT服务器、发送AT指令、进入透传模式传输数据、接受平台下发的报文数据的驱动； MQTT协议包（包含了MQTT协议的各种包头，对包的处理函数）；ALiIOT 对接云平台的驱动，包括接入云平台（使用MQTT连接参数，调用MQTT协议包的连接函数）、断开云平台（![a5d2aa9b-4cb3-4a19-ab2e-deaedf3ad252](file:///C:/Users/SHARK/Pictures/Typedown/a5d2aa9b-4cb3-4a19-ab2e-deaedf3ad252.png)）、订阅（![6b8d8f04-e239-4736-b673-c2808c40bdcd](file:///C:/Users/SHARK/Pictures/Typedown/6b8d8f04-e239-4736-b673-c2808c40bdcd.png)）、发布（![a8a7a7b7-c163-4614-a3ee-e90a81bf2255](file:///C:/Users/SHARK/Pictures/Typedown/a8a7a7b7-c163-4614-a3ee-e90a81bf2255.png)）、

![db5190e6-983c-43b1-b7bd-40733303dd42](file:///C:/Users/SHARK/Pictures/Typedown/db5190e6-983c-43b1-b7bd-40733303dd42.png)

[如何将MQTT协议的设备接入物联网平台_物联网平台(IoT)-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/iot/developer-reference/example#title-yyz-j0w-wyy)

2.设备订阅和发布

[为产品自定义Topic类及设备自定义Topic通信说明_物联网平台(IoT)-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/iot/user-guide/use-custom-topics?spm=a2c4g.11186623.0.0.5b521c5ahVWRrK)

[设备接收云端应用（业务服务器）下发的指令或消息_物联网平台(IoT)-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/iot/getting-started/send-commands-from-iot-platform-to-devices-1?spm=a2c4g.11186623.0.0.58643a21rsP0A3)

[设备和服务器使用自定义Topic进行上下行通信_物联网平台(IoT)-阿里云帮助中心 (aliyun.com)](https://help.aliyun.com/zh/iot/use-cases/use-custom-topics-for-communication?spm=a2c4g.11186623.0.0.58643a21rsP0A3)

设备发布到云平台 ：

使用物模型通信Topic

![47f62f2d-e9eb-4dcb-ab00-140170b7f5ba](file:///C:/Users/SHARK/Pictures/Typedown/47f62f2d-e9eb-4dcb-ab00-140170b7f5ba.png)



使用该主题，在设备调试里面![ffa2cd9a-b597-455a-985d-a10adc69d559](file:///C:/Users/SHARK/Pictures/Typedown/ffa2cd9a-b597-455a-985d-a10adc69d559.png)

设置，通过查看日志，获取发送数据的格式

![4a30d29b-933b-4fe1-bf8e-d2e914cc93a5](file:///C:/Users/SHARK/Pictures/Typedown/4a30d29b-933b-4fe1-bf8e-d2e914cc93a5.png)

{"method":"thing.service.property.set","id":"1924954941","params":{"CurrentHumidity":66,"NightLightSwitch":1,"CurrentTemperature":66},"version":"1.0.0"}

再改成这样的格式/“/”



![ce571bfe-25b7-4fb0-a840-e10e9927a8c0](file:///C:/Users/SHARK/Pictures/Typedown/ce571bfe-25b7-4fb0-a840-e10e9927a8c0.png)

![2e75f143-5422-4b85-a8ed-fdd5832df624](file:///C:/Users/SHARK/Pictures/Typedown/2e75f143-5422-4b85-a8ed-fdd5832df624.png)

![b92df618-0299-4be7-af42-82e00b9d11ee](file:///C:/Users/SHARK/Pictures/Typedown/b92df618-0299-4be7-af42-82e00b9d11ee.png)![a706d9ab-4b00-4f28-8516-68cf59bd1a32](file:///C:/Users/SHARK/Pictures/Typedown/a706d9ab-4b00-4f28-8516-68cf59bd1a32.png) 

![f6b5e41a-c234-41c1-a0b9-267e3e53d2af](file:///C:/Users/SHARK/Pictures/Typedown/f6b5e41a-c234-41c1-a0b9-267e3e53d2af.png)

![8af23e5c-06e1-408b-a066-b118c2772b4b](file:///C:/Users/SHARK/Pictures/Typedown/8af23e5c-06e1-408b-a066-b118c2772b4b.png)

未完待续........

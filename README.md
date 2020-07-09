# test1

## Install DHT11 sensor
```
git clone https://github.com/adafruit/Adafruit_python_DHT.git
cd Adafruit_python_DHT
sudo python setup.py install 
cd Adafruit_python_DHT/examples
```
  -run
  ```
  python AdafruitDHT.py 11 4
  ```  
  
기본 디렉토리 명령어
```
ls 현재 경로 팡ㄹ 리스트
cd 디렉토리 변경
mkdir 디렉토리 생성
pwd 현재 디렉토리
```
운영 관련 명령어
```
ps -aux 현재 실행중인 프로세스
netstat - tnl 현재 사용중인 tcp 포트
uft 방화벽 설정
history 명령어 history
apt-get 소프트웨어 설치/제거
sudo 슈퍼유저권한 대행
su 유저 변경
vim 편집기
```

 깃허브 불러오는 방법 kimmingyu<user name>, test1<repository>
git clone https://github.com/kimmingyu97/test1
  
  ## vim 편집기 사용법
  ```
  vim .vimrc <vim 편집설정하는 곳으로 들어가기
  set nu //line number
  set cindent // c문법에 맞게
  set ts=4 //탭 눌렀을 경우 스페이스바 4번이랑 동일하게 설정
  if has("syntax") //syntax on
    syntax on
  endif
```

set softtabstop=4
set bg=dark
set expandtab
let python_version_2 =1
let python_highlight_all=1
filetype id:ent plugin on
```
#!/usr/bin/python
  
  import time
  import RPI.GPIO as GPIO
 
  print GPIO.VERSION
  GPIO.setmode(GPIO.BCM)
  GPIO.setup(4, GPIO_IN)
 
  def interupt_fired(channel):
      print("interrupt Fired")
      print(channel)
 
  GPIO.add_event_detect(4, GPIO.FALLING, callback=interrupt_fired)
 
  while(True):
      time.sleep(1)
      print("timer fired")
```
```
 1 #!/usr/bin/python
  2
  3 import time
  4 import RPi.GPIO as GPIO
  5 import Adafruit_DHT
  6 import requests, json
  7 from influxdb import InfluxDBClient as influxdb
  8 GPIO.setmode (GPIO.BCM)
  9 GPIO.setup(4,GPIO.IN)
 10
 11 def interrupt_fired(channel):
 12     print("interrupt Fired")
 13     print(channel)
 14     a=5
 15
 16     data=[{
 17         'measurement' : 'pir',
 18         'tags':{
 19             'visionUni':'2410',
 20             },
 21         'fields':{
 22             'pir':a,
 23             }
 24         }]
 25     client = None
 26     try:
 27         client = influxdb('localhost',8086,'root','root','pir')
 28     except Exception as e:
 29         print "Exception write" + str(e)
 30     if client is not None:
 31          try:
 32              client.write_points(data)
 33          except Exception as e:
 34              print "Exception write" + str(e)
 35          finally:
 36              client.close()
 37     print(a)
 38 GPIO.add_event_detect(4,GPIO.FALLING,callback=interrupt_fired)
 40 while(True):
 41     time.sleep(1)
 42     a=1
 43     data=[{
 44         'measurement' : 'pir',
 45         'tags':{
 46             'visionUni':'2410',
 47             },
 48         'fields':{
 49             'pir':a,
 50             }
 51         }]
 52     client = None
 53     try:
 54         client = influxdb('localhost',8086,'root','root','pir')
 55     except Exception as e:
 56         print "Exception write" + str(e)
 57     if client is not None:
 58          try:
 59              client.write_points(data)
 60          except Exception as e:
 61              print "Exception write" + str(e)
 62          finally:
 63              client.close()
 64          print("running influxdb ok")
```

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

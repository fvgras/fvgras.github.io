
### Micro Python Project:

#### Problem/Challenge: Explore simplicity of Python with download uPython to ESP8266

#### Why: Explore (1) REPL interface (2) rshell interface

#### Description: use the platform as a wifi detector (Thanks2 Ccooper)

#### Technical Components: (1) esp8266-20180511-v1.9.4.bin (size 604kb)

```code
>>> help('modules')
__main__          http_client       socket            upip  
_boot             http_client_ssl   ssd1306           upip_utarfile 
_onewire          http_server       ssl               upysh
_webrepl          http_server_ssl   struct            urandom 
apa102            inisetup          sys               ure 
array             io                time              urequests 
binascii          json              uasyncio/__init__ urllib/urequest
btree             lwip              uasyncio/core     uselect 
builtins          machine           ubinascii         usocket 
collections       math              ucollections      ussl 
dht               micropython       ucryptolib        ustruct 
ds18x20           neopixel          uctypes           utime 
errno             network           uerrno            utimeq
esp               ntptime           uhashlib          uzlib 
example_pub_button                  onewire           uheapq            webrepl
example_sub_led   os                uio               webrepl_setup 
flashbdev         port_diag         ujson             websocket
framebuf          random            umqtt/robust      websocket_helper
gc                re                umqtt/simple      zlib
hashlib           select            uos                                                                                                               
Plus any modules on the filesystem
>>> import uos
>>> (cntl-D)  <-- soft reboot 
MicroPython v1.10-8-g8b7039d7d on 2019-01-26; ESP module with ESP8266
Type "help()" for more information.
>>> help()
Welcome to MicroPython!

For online docs please visit http://docs.micropython.org/en/latest/esp8266/ .
For diagnostic information to include in bug reports execute 'import port_diag'.

Basic WiFi configuration:

import network
sta_if = network.WLAN(network.STA_IF); sta_if.active(True)
sta_if.scan()                             # Scan for available access points
sta_if.connect("<AP_name>", "<password>") # Connect to an AP
sta_if.isconnected()                      # Check for successful connection
# Change name/password of ESP8266's AP:
ap_if = network.WLAN(network.AP_IF)
ap_if.config(essid="<AP_NAME>", authmode=network.AUTH_WPA_WPA2_PSK, password="<password>")

Control commands:
  CTRL-A        -- on a blank line, enter raw REPL mode
  CTRL-B        -- on a blank line, enter normal REPL mode
  CTRL-C        -- interrupt a running program
  CTRL-D        -- on a blank line, do a soft reset of the board
  CTRL-E        -- on a blank line, enter paste mode

For further help on a specific object, type help(obj)
>>> import network
>>> sta_if = network.WLAN(network.STA_IF); sta_if.active(True)

>>> sta_if.connect("BCMudCC","BCMud16318")
-OR-
>>> sta_if.connect("ATXHackerspace","hackon!!")
>>> sta_if.isconnected()
True
>>> sta_if.scan()
... arp-table...
>>> import webrepl_setup
WebREPL daemon auto-start status: disabled

Would you like to (E)nable or (D)isable it running on boot?
(Empty line to quit)
> E
To enable WebREPL, you must set password for it
New password (4-9 chars): replYes
Confirm password: replYes
Changes will be activated after reboot
Would you like to reboot now? (y/n) y
...
>>> import network
>>> sta = network.WLAN(network.STA_IF)
>>> sta.ifconfig()
('192.168.2.14', '255.255.255.0', '192.168.2.1', '192.168.2.1')
>>>
WebREPL connection from: ('192.168.2.11', 47702)
>>> import machine
>>> dir(machine)
['__name__', 'mem8', 'mem16', 'mem32', 'freq', 'reset', 'reset_cause', 'unique_id', 'idle', 'sleep', 'deepsleep', 'disable_irq', 'enable_irq', 'time_pulse_us', 'RTC', 'Timer', 'WDT', 'Pin', 'Signal', 'PWM', 'ADC', 'UART', 'I2C', 'SPI', 'DEEPSLEEP', 'PWRON_RESET', 'HARD_RESET', 'DEEPSLEEP_RESET', 'WDT_RESET', 'SOFT_RESET']
>>> p=machine.Pin(2,machine.Pin.OUT)
>>> p.on()
>>> p.off()
>>> p2=machine.PWM(p)
>>> type(p2)
<class 'PWM'>
>>> dir(p2)
['init', 'deinit', 'freq', 'duty']
>>> p2.freq(1)
>>> p2.duty(50)
>>> p2.deinit()
>>> dir(machine.Pin)
['init', 'value', 'off', 'on', 'irq', 'IN', 'OUT', 'OPEN_DRAIN', 'PULL_UP', 'IRQ_RISING', 'IRQ_FALLING']
>>>

$rshell
Welcome to rshell. Use Control-D to exit.
>help

Documentated commands (type help <topic>):
args    cat   connect echo  filesize  help mkdir   rm   shell
boards  cd    cp      edit  filetype  ls   repl    rsync

>help connect
connect TYPE TYPE_PARAMS
connect serial port [baud]
connect telnet ip-address-or-name

>connect serial /dev/ttyUSB0
Connecting to /dev/ttypUSB0 (buffer-size 512)...
Testing if sys.stdin.buffer exists ... Y
Retrieving root directories ... /boot.py/
Setting time ...
Evaluating board_name ... pyboard
Retrieving time epoch ...

>boards
pyboard @ /dev/ttyUSRB0 connected Epoch: 2000 Dirs: /boot.py /webrepl_cfg.py /pyboard/boot.py 
...

>ls /pyboard/
...
>repl
Entering REPL. Use Control-X to exit.
>
MicroPython v1.10-8-g8b7039d7d on 2019-01-26; ESP module with ESP8266
Type "help()" for more information.
>>>
>>>
   cntl-X  (will exit repl to rshell, then cntl-D to exit) 
Note: my unique wifi-enabled network is --> MycroPython-1ace8c

```

#### Results: Project works, thanks ChrisC.

#### References: (a) MicroPython on a ESP8266@PyTexas2017.pdf
#### References: (b) https://github.com/micropython/webrepl

```markdown
```
#### **Android_Transfer_Pics page:-) ------>** [next page](./android_transfer_pics.md)

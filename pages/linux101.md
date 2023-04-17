title : Linux 101
author: zvevqx
published: 2025-11-22
cat: linux
desc: ws

...

learn more about `ssh` -> [https://www.ssh.com/ssh/](https://www.ssh.com/ssh/)

- **linux** :

start terminal <key>ctrl</key> + <key>alt</key> + <key>t</key>

~~~ bash
ssh pi@er401.duckdns.org:22
ssh user @ distant_server.address : connection_port (default to 22 )
~~~


>⚠️ linux user :
> to copy inside the `terminal` :  <key>ctrl</key> + <key>shift</key> + <key>c</key>
> to paste inside the `terminal` : <key>ctrl</key> + <key>shift</key> + <key>v</key>

- **Osx**  :

    start terminal  ( <key> &#127822;  </key> +  <key> 	space 	 </key>  and search for `terminal`)

~~~bash
ssh pi@er401.duckdns.org:22
~~~

- **Windows** :
- install ```putty``` 
    - got to [putty download page](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
        - `putty` will give ~~windows~~ `ssh` ability ...   
- connect to:
    - server:    ```er401.duckdns.org```
    - port      ```22```
    - user      `pi`

---

---


## create your new `home`

### first

1. *create a User* 
```
    sudo useradd -m <username> -p <password>
```

2. *add user to groups and privilege* 

- add user to ```admin``` list 

```bash
    sudo usermod -a -G sudo yourUserName
```

- change shell to ```zsh``` ( optional )

```bash
    chsh -s /bin/zsh
```

- exit user ```pi```

```bash
    exit
```

3. *reconnect with your `username` and `password`* 

```bash
    ssh YOUR_USER_NAME@er401.duckdns.org:22 
```
    
4. welcome to your new `home`

    1. your *home folder* is in `/home/yourUserName` 
        1. hint : you can check where you are with the command `pwd` (**P**rint **W**orking **D**irectory) 
    2. learm about linus folder structure -> [random first article on ddg search :) ](https://linuxhandbook.com/linux-directory-structure/)


---

## create folder in ```apache``` server

wft is `apache` :

>   apache is a http web server  [wiki page](https://en.wikipedia.org/wiki/Apache_HTTP_Server)

there other solution like [https://www.lighttpd.net/]{https://www.lighttpd.net/} 

`apache` is well documented and often the one you'll find on a web server service 

  

1.  create folder first with your username 
```bash
    sudo mkdir -p /var/www/html/$USER 
```
2.  change ownership to your user
```bash
    sudo chown -R $USER:$USER /var/www/html/$USER
```
3. make sure permissions on ```www``` are ok 
```bash
    sudo chmod -R 755 /var/www
```
4. create your first webpage to serve  
```bash
    touch /var/www/html/$USER/index.html
```
5. put something in it 
```bash
    nano /var/www/html/$USER/index.html
    or 
    vim /var/www/html/$USER/index.html
```


6. content example



~~~html
    <html>
       <head>
          <meta charset="UTF-8">
          <title>Welcome to my page</title>
       <style>
         h1{
         font-size : 42px;
         }
        </style>
       </head>
    <body>
          <h1> 📡 Success!! 📡 </h1>
    </body>
    </html>
~~~



# DO SOME STUFF

## general `cli` commands

### navigate

- `.` the current directory ( folder)
- `..`  the parent directory 
- `man` : view the **man**ual of a command ( ex : ` man ls` )
- `pwd   `   : Use the **pwd** command to find out the path of the current working directory (folder) you’re in
- `cd` : **c**hange **d**irectory to go inside a new directory 
- `ls` : **l**i**s**t the current directory content 
- `cp` : to **c**o**p**y documents / folders
- `mv`: to **m**o**v**e documents / folder 
- `mkdir`: **m**a**k**e **dir**ectory create a folder 
- `touch`: create an empty file 
- `rm` : **r**e**m**ove folder and files ***⚠️*** no return possible / read and think twice before smashing <key> enter </key> 
- `find`: to find / search for files

### system stuffs

- `sudo` : **s**uper **u**ser **do** get super privileges to do system stuff ***⚠️*** `sudo` can do **ANYTHING** , even destroy system
- `du` : **d**isk **u**sage ... to see .. disk usage ( use it with `-h` argument for human readable output )
- `top` and `htop` : to monitor system ( application / ram / cpu usage)
- `killall` : kill a process by name e:`killall firefox` will quit and kill all *firefix* process    
- `uname ` : view system information ( kernel /  linux version ....)
- `sudo reboot` : restart computer ( must be `sudo` to execute )
- `sudo halt` || `sudo shutdown now` : shutdown computer ( must be `sudo`)

### general help

- <key>ctrl</key> + <key>r</key> : search in history for already used commands
- <key>ctrl</key> +  <key>c</key> : **kill** running command 
- list of softwares : [go to page](soft.html) 

## mjpeg-streamer ( video server )

```https://github.com/jacksonliam/mjpg-streamer```

[github project page](https://github.com/jacksonliam/mjpg-streamer)

***⚠️*** don't follow the instructions during this class ( installation already done )

- after install
    - add your user to `video` group
      
         ~~~bash
         usermod -a -G video $USER
        ~~~
        
        this will give your user to access camera equipement
      
    - logout and back in 
    
    - go have a look
        - start server 
        ~~~bash
        cd ~/mjpg-streamer/mjpg-streamer-experimental &&  ./mjpg_streamer -o "output_http.so -w ./www" -i "input_raspicam.so"
        ~~~
        
    - go check 
    
        ~~~bash
        #in a local network
        http://IP_FOR_THE_RASPBERRY_PI:8080/?action=stream
        #in that case with dyndns service ( duckdns ) and port redirection ( 666 -> 8080)
        http://er401.duckdns.org:666/?action=stream
        ~~~

# getting started with python

==underconstruction==

![uc](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fi.pinimg.com%2Foriginals%2F0b%2F12%2Fd9%2F0b12d9ff85bf365bc7acde04a992d938.gif&f=1&nofb=1)

just some code to try 

~~~python
import time
import math
x = 0
try :
    while True:
        x = x+1
        time.sleep(0.5)
        print(" la vlaeur de x est de = {}".format(x))
        if x>100:
            x=0
            
except KeyboardInterrupt:
    print('Hello user you have pressed ctrl-c button.')
~~~




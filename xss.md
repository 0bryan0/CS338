# Cookies and cross-site scripting (XSS)
## NAME: Bryan Yang

#### PART 1: COOKIES
 - a.   
    There is 1 cookie:
        Name: theme 
        Value: default
 - b.   
    Yes, it changed to the theme I chose.
 - c.   
    The Cookie header hold the current theme, not the one I want to change it to. There is no Set-Cookie header, 
        Cookie: theme=red (I just pressed the button for the blue theme)
 - d.
    Yes, it remained blue for me.
 - e.
    The browser sends a cookie to the server, called 'theme', and the value of that cookie is the current theme. So when I request a new theme, this cookie still has the value of the current theme, not the theme I just reuqested. 
 - f.
    It is part of the request querey. My GET request looks like:
        GET /fdf/?theme=default HTTP/1.1
    My current theme was blue, but I requested the default theme. 
 - g. 
    I just replaced the theme in the inspector (by literally just typing the value of the theme I wanted, such as 'red' where it said 'default'). Then I reloaded the page and got a red theme. 
 - h.
    When the GET request is intercepted in Burp, I can change the Cookie header value to be whatever color I want(that is an existing theme)
 - i.
    Googling says linux stores cookies in specific directories associated with/in directories of specific browsers. However, on Kali, doing a 'find' command on the terminal shows only one result when looking for "Cookies":
        /usr/share/perl5/HTTP/Cookies
    Some browsers apparantly use SQL instead of directories so there may be more than just that one directory I found. 

#### PART 2: XSS
 - a.
    Moriarty made a post early than me(he has the 2nd, and 3rd post).
    The post included some scripts.
    I visited his post later and his scripts ran on my browser.
    So he was able to affect people in the future(relative to when he wrote his post)
 - b. I belive Javascript can fetch cookies, so you could grab people's cookies
 - c. Users could be redirected to a malicious website
 - d. Server can blacklist certain patterns of text that look like scripts.
      Browsers can stop cookies from being sent cross-site, or at least warn that it is happening. 
    
    

# Day 3
## Task name
Hydra is Coming to Town 
### Learning

1. CRUNCH - Crunch is a wordlist generator where you can specify a standard character set or any set of characters to be used in generating the wordlists. The wordlists are created through combination and permutation of a set of characters. You can determine the amount of characters and list size.
2. HYDRA - Hydra is a parallelized login cracker which supports numerous protocols to attack. It is very fast and flexible, and new modules are easy to add.This tool makes it possible for researchers and security consultants to show how easy it would be to gain unauthorized access to a system remotely.
Hydra is a free and open-source password-cracking tool. It can try numerous passwords till the correct password is found. It can be used to crack passwords for various network services, including SSH, Telnet, FTP, and HTTP.

GENERATING THE PASSWORDS FILE:-

After reading the man file for crunch we will get a basic understanding of what options to be used, we want crunch to create 3 digit passwords from 0123456789ABCDEF and save then to a file called passwd.txt

The command we use is `$ crunch <min size> <max size> <character set> -o <filename>`

thus we use `$ crunch 3 3 0123456789ABCDEF -o passwd.txt`

We get the following output and the file is created.
![image](https://github.com/vishwatejD/advent-of-cyber-2023/assets/141154035/4d7859b5-0102-4382-8e50-ea75d1925c93)

Now we need to know of the method in which the website takes the input from the user and verifies it.
By taking a look at the source code (ctrl+U) we can know that the method is post.

![image](https://github.com/vishwatejD/advent-of-cyber-2023/assets/141154035/abf2a40e-def8-4fd4-9dd2-dfdf166e54be)

The main login page http://10.10.1.227:8000/pin.php receives the input from the user and sends it to /login.php using the name pin.

Now we use the command `hydra -l '' -P passwd.txt -f -v 10.10.1.227 http-post-form "/login.php:pin=^PASS^:Access denied" -s 8000`


  ` l '' `indicates that the login name is blank as the security lock only requires a password
    
 ` -P ` passwd.txt specifies the password file to use
    
  `-f `stops Hydra after finding a working password
    
  ` -v` provides verbose output and is helpful for catching errors
    
   `10.10.1.227` is the IP address of the target
    
   `http-post-form ` specifies the HTTP method to use
    
   `"/login.php:pin=^PASS^:Access denied"` has three parts separated by :
    
   `/login.php` is the page where the PIN code is submitted
        
   `pin=^PASS^` will replace ^PASS^ with values from the password list
        
  `Access denied` indicates that invalid passwords will lead to a page that contains the text “Access denied”
   
 ` -s 8000` indicates the port number on the target

After sometime we get the task terminates and we get the password.

![image](https://github.com/vishwatejD/advent-of-cyber-2023/assets/141154035/1e437ac0-bf86-4434-b7ab-2d5991f3ed32)

We enter the password and click open door to get the flag

![image](https://github.com/vishwatejD/advent-of-cyber-2023/assets/141154035/2a39d743-6402-4771-855c-4156721434bd)

FLAG:- THM{pin-code-brute-force}


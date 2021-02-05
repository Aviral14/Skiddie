# Solution

The first task is to end the timer and enable the the submit button. Looking at the source code of html we find two js files and a script that validates the credentials. The submit button has id "rgefr".For disabling this button, some js function may be using this id to recognize this HTML element.Upon deobfuscating the js files we find that akm.js has a function that controls the timer and the value of the timer element equals the value of the variable "v". Hence making v=0 on the console, ends the timer and enables the button.

Now we plug in the `username="userxyvw"` and the `password="easyhuh!"` which we see in the script that validates them. But we get a prompt which declares these credentials as invalid. This indicates that the other two scripts might be changing the value of these variables. We get the actual value of passwd as `"realpasswd!!"` by printing it on console.

Alternatively we can use curl or a short python script to bypass the timer-
```
curl http://skiddie.pythonanywhere.com/web4/ -d username=userxyvw -d password=realpasswd%21%21
```

## Flag
```
flag:LaDiDa!
```
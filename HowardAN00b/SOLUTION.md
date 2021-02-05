# Solution

The html source and the webpage does not give any hint about the challenge, but upon inspecting the webpage URL, we find that two parameters are passed with the get request, one is "file" and the other is "font". The file parameter makes it evident that it's a challenge based on `Local File Inclusion attack`. We can use this vulnerability to get the content of some file. Since we are asked the secret key, we can try `/etc/passwd` and `/etc/shadow` as the file. The message displayed indicates that /etc/passwd is the correct file.

We have to get the authority to access the content of the file. Upon examining the Http cookies, we find that the value of the `admin_access` cookie can be changed to 1 to expose the flag!

## Flag
```
flag:Bazzinga!!
```
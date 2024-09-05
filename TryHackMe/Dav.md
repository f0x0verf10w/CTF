**This chall is on Tryhackme**

[Click here](https://tryhackme.com/r/room/bsidesgtdav)

![nmap](https://github.com/user-attachments/assets/83ac7817-f49e-439f-b7d3-8db143975ecf)
see ya !,we had a website on port 80,So I paste the IP adress in the browser and it shows us the default apache server page. =)) <br>

![apache2](https://github.com/user-attachments/assets/7cc6cbfb-b7e0-4c5d-ad28-1620fe4641c9)



Next ,we will use Gobuster to enum Directory on the website:


![gobuster](https://github.com/user-attachments/assets/72f4c174-9ef5-473d-9837-d35496642c36)


we had /webdav directory.Let's discover it. <br>
oh,it requires user and password to login and I don't have both,but don't worry,After seeing this I googled about WebDAV login vulnerability and after a lot of search 
 I have wampp as default user and xampp as default password so I try this and it worked.
 ![crendential](https://github.com/user-attachments/assets/4aa3815b-3d01-44cf-ad89-91c0a5c28944)

 website is [here](http://xforeveryman.blogspot.com/2012/01/helper-webdav-xampp-173-default.html) <br>

 perfectly,I find a password.dav,It has default crendentials that we login into /webdav <br>
 ![passwd](https://github.com/user-attachments/assets/e8f1822d-bce5-43ed-bb4e-7465f0847750)
 ![wapp](https://github.com/user-attachments/assets/d6015894-fda1-4422-bda1-1d4b2aed69bb)


  After this I searched for webdav vulnerability and get that we can upload files to it's server. 
  I think if I can upload the shell and connect to it we can login into the system easily. <br>
First,we will copy reverse shell and modify Ip and port with vim or nano :
![shell](https://github.com/user-attachments/assets/87c304bc-6a86-443c-b44f-81a0f1bf7f9c)
I use vim to modify shell with command: vim php_reverse_shell.php 
![modify](https://github.com/user-attachments/assets/b74b5f77-581c-46a5-a131-1d5f78995da1)
Next,we will use Curl to send reverse shell to website:

![upload](https://github.com/user-attachments/assets/131ee76c-371b-4e1f-84f6-135eb3287402)
we reload the website and see the our reverse shell:
![shell](https://github.com/user-attachments/assets/c1d1b22c-28ee-4596-92d9-2e890359a8c2)
Next, I use Netcat to catch the connect with our shell and and click to activate the shell:
 ![nc](https://github.com/user-attachments/assets/e24ed001-d37c-4b7e-932c-9a4271017b56)
I find the user's flag in /home/merlin
![usr](https://github.com/user-attachments/assets/6eed8092-c2f0-40e1-a953-8d9cdcbdb185)
To get root's flag,I have to escalate privileges
Let's do it!!!

here i found "cat" command which can be used to read file as root without escalating privileges, it's so simple 

![sudo -l](https://github.com/user-attachments/assets/fe05467a-2c50-4279-ab91-c6607d0504be)
I really succeeded! <br>
![root](https://github.com/user-attachments/assets/d690bf5e-24f9-4ac3-b997-c42687838ad6)


That's interesting challenge !!!

 

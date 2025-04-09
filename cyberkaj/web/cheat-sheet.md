# Cheat sheet

## SSH into target with their private key

Assume we have a target **root**, which we want to ssh into

1. Get the private key of root (might be located in /root/_.ssh/id\_rsa_ )

```
Target: root
Private key: /root/.ssh/id_rsa:
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABlwAAAAdzc2gtcn
<...>
ICLgLxRR4sAx0AAAAPcm9vdEBsaW5rdm9ydGV4AQIDBA==
-----END OPENSSH PRIVATE KEY-----

```

2. Save it.

```bash
┌──(kali㉿kali)-[~/htb/boxes/linkvortex/ssh]
└─$ vim id_rsa

```

3. Remember to change to strict permissions (Se the error below)

<pre class="language-bash"><code class="lang-bash">└─$ ssh -i id_rsa root@&#x3C;hostname or IP>
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0664 for 'id_rsa' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "id_rsa": bad permissions
root@&#x3C;hostname or IP>'s password: 

<strong>└─$ chmod 700 id_rsa   
</strong></code></pre>

4. ssh into the target

```bash
└─$ ssh -i id_rsa root@<hostname or IP> 
Welcome to Ubuntu 22.04.5 LTS (GNU/Linux 6.5.0-27-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

This system has been minimized by removing packages and content that are
not required on a system that users do not log into.

To restore this content, you can run the 'unminimize' command.
Failed to connect to https://changelogs.ubuntu.com/meta-release-lts. Check your Internet connection or proxy settings

Last login: Mon Dec  2 11:20:43 2074 from 10.10.xx.xx
root@<hostname or IP>:~# ls
```


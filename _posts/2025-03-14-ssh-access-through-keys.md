To continue the path on my homelab the most secure i can, we want right now to generate access keys in our laptop and put them in the server. When accessing through SSH, the server is going to check first if the ip is allowed in UFW and then, if who’s accessing has the compatible keys. 

With this we should eliminate the password for accessing (or not?)

This really makes me feel completing a great task, i’ts been great so far!

for this all we need to do is:

```bash
sudo ssh-keygen -t rsa -b 4056 -f ~/.ssh/81_key
```

then we must copy this generated key, into the right folder inside the server

```bash
ssh-copy-id -i ~/.ssh/81_key.pub pozzi@10.0.0.115
```

If you decide to eliminate the password access, the server will still be secured by the keys, and for testing it’s ok, but in production, the both authentications together makes a better secure 

```bash
sudo vim /etc/ssh/sshd_config
```

Look for the line PassWordAuthentications, and change the value to “Yes” exactly like this bottom example

![image.png](attachment:9f4c2cc3-ce26-4f30-ab59-f75219b0e2fa:image.png)

Make a test and it works!!
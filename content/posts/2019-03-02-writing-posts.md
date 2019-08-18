---
title: "Love and HTTPS"
description: "Adding https to my girlfriend's blog."
date: 2019-08-13 15:00:00
author: Chibuzor Obiora
slug: love-and-https
tags:
    - technology
    - ssl
    - letsencrypt
cover: ''
fullscreen: true
---
So, a few days ago, I get a message from bae and it read, "Babe, something went wrong. My blog is down. Please help me put it back up. Nkem". Now if you know Igbo, the language and its people, then you know that "Nkem" is one of the greatest terms of endearment.

My mission was manifest. Love had summoned me and, my task was clear.

I visited her blog and realized the problem; the site's SSL certificate had expired.

*Back up. So this is your first post? Really?*

*Yes, really. And you want to know why?*

*S.O.T.I once said that "If you want to write, write what you know."

What do I know? A few things.
* HTTPS is critical for the modern web. 
* You can obtain authentic SSL certificates for free. Thanks to [Let’s Encrypt](https://letsencrypt.org/getting-started/).
* And bae loves me. :-)

With all of that knowledge, I got to fixing it and, then decided to write about how I did it. 

Should love and https ever come calling for you. ;-)


### CLI aka School of the Hard Knocks
What you will need:
* <strong>certbot</strong> installed on your system
* <strong>Access</strong> to the cPanel for the site
* Your <strong>wits</strong> about you
  
With your access to the cPanel, find your way to the File Manager

Then make sure you can access the `public` folder. This is typically the part of the website that is shown to the world. 

Within this part, create this directory structure if it does not exist 
```
   .well-known/acme-challenge/
```
Make sure to leave this window open because later you'll be adding a very important file here.

> Now for the good stuff. Follow closely on your terminal

run
```
    certbot --version
```
Mine gives this
```
    certbot 0.36.0
```
To let you know that certbot is installed. Please go [here](https://certbot.eff.org/instructions) to learn how you can install certbot.


```
certbot certonly -d <YOUR DOMAIN HERE> --manual -m <YOUR EMAIL HERE> --agree-tos

```

The domain name is the what you want the SSL certificate for. The email address is for notifications related to the status of the certificate. 

Now, on running this command, it will pause and ask that you create a file on your webserver that it can access. With instructions looking like this

![Certbot instructions](/images/posts/example-com-intructions.png)

This means that you create a file with file name `hPL3AQ4EJNPcFwkOVDXkMnCOoGyGXlEG7IWERwIN4Lk` in this example case. And have its contents be exactly `hPL3AQ4EJNPcFwkOVDXkMnCOoGyGXlEG7IWERwIN4Lk.Q4nCIb-goUnTjeoDaIJrGQLzXUcfD1wKt-KENHYlgp0`

That is all. 

Remember our folder `.well-known/acme-challenge/` inside our file manager. 

Go back to it and create the file with the name and edit the contents accordingly. Make sure to save it.

When you're done come back to your terminal and hit "Enter". Certbot on your terminal will make a request to that url and sees if the content it receives matches what it is expecting.

if it all goes according to plan, certbot will two files; a certificate `fullchain.pem` and also a private key `privkey.pem`

Copy the contents and one way is to use `cat` command

As in
```
cat /etc/letsencrypt/live/DOMAIN_NAME/fullchain.pem

```  
it might generate two so make sure to only copy from one (inclusive)
```
-----BEGIN CERTIFICATE-----

```
  to 
```
-----END CERTIFICATE----- 
```
I copied the first block and did the same for private key.

```
cat /etc/letsencrypt/live/DOMAIN_NAME/privkey.pem
```

Only one thing left to do and, that is to host the copied text on the webserver.

And to do that you'll have to locate SSL/TLS manager and head into where you can manage your sites. 

Look for where to manually register certificates; add your domain name and then make sure you add the certificate text to the certificate slot
and private key text to the private key slot. 

Save and, that should be that. 

*Lets Encrypt provides direct integrations to a few providers. See [here](https://community.letsencrypt.org/t/web-hosting-who-support-lets-encrypt/6920) if you are one of the lucky ones.
*SOTI - Someone On The Internet
### SSL for free

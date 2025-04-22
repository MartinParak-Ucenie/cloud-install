# Mailovy server
### docker-mailserver (v15.0.2)
mailserver konfigurovat az po prihlaseni ako admin (Configure Email Notifications: Later)

na cielovom serveri sa vytvoria adresare s datami na `/srv/mailserver/`

### vytvorenie uzivatela mail servera
`docker exec -it mailserver setup email add hardy@rpi5.local <heslo>`

### prezretie zoznamu emailovych adries, zaregistrovanych na mailserveri
`docker exec -it mailserver setup email list`

### prezeranie emailov uzivatela ABC
`root@mailserver:cd /var/mail/<domainname>/ABC/`

### prezretie nakonfigurovanych domen
`docker exec -it mailserver cat /etc/postfix/main.cf | grep mydestination`

### pri nastavovani SMTP Host
Host name: mailserver


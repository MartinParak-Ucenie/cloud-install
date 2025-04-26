# Jenkins
pri prvom spusteni pyta admin heslo

## Unlock Jenkins
To ensure Jenkins is securely set up by the administrator, 
a password has been written to the log  and this file on the server:

`/var/jenkins_home/secrets/initialAdminPassword`

Please copy the password from either location and paste it below.

### prihlasenie do Jenkins docker kontajnera

`docker exec -it jenkins bash`

`$ cat /var/jenkins_home/secrets/initialAdminPassword`

po zadani hesla
- opyta sa na instalovanie pluginov - nateraz staci
odporucane (trva to cca do 3 minut na Rpi5)
- vytvorenie uzivatela, Jenkins admina
- konfiguracia instancie Jenkinsa (nastavenie URL, staci nechat, co ponukne)
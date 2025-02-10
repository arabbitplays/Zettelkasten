---
date created: 21.08.2023 16:39
date modified: 18.08.2024 13:48
---

```bash
ssh -p 4222 maddin@obrechtindustries.ddns.net
```
## General

### Port Stuff
```bash
sudo ufw allow 8081
sudo ufw reload
```
Im Router den Port auch öffnen!

### Maven
https://maven.apache.org/download.cgi
```bash
sudo wget url
sudo tar -xzf tarFile
```

Und path variable in ~/.bash_profile anpassen

```
sudo -E printenv
```

## Java

```bash
#This will list all the installed Java versions and their corresponding paths.
update-alternatives --list java 

#Install Java
sudo apt update 
sudo apt install openjdk-11-jdk

#Choose Java Version
sudo update-alternatives --config java

java --version
```


## Frontend

```bash
cd /var/www/haushalt-frontend
sudo ng build
```

## Backend
```bash
sudo git reset --hard origin/main
```
```bash
# fat jar files needed (sheded plugin)
mvn clean install
sudo systemctl start RezeptDeamon.service
```
For seeing the console:
Run Jar File in Target dir with 
```bash 
java -jar target/Haushalt-1.0-SNAPSHOT.jar
```

<mark style="background: #FF5582A6;">!!! Deamon spezifiziert eigenen Port als Command Line arguemnt und nutzt NICHT das application.properties file !!!</mark>

### Versions

- Java 19
- Maven 3.8.8

## Mongo DB
```bash
# Anderes Zeug davor, siehe https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/
sudo apt-get install -y mongodb-org
```

```bash
sudo systemctl start mongod

# Für start be reboot
sudo systemctl enable mongod
```


## Maddin

```bash
# Apache2 configuration for sites 
cd /etc/apache2/sites-available/ 
sudo nano /etc/apache2/sites-available/ 
# The 420 Project Frontend path: 
/var/www/The420Frontend/dist/obrechtindustries 

#REAL 
/var/www/The420Frontend 
ng build --configuration=production 
sudo service apache2 restart 
sudo service apache2 reload 

# Index Paths, for later configuration index HTML in here ^^ 
/var/www/haushalt-frontend/dist/haushalt-frontend /var/www/ObrechtIndustriesWebsite/src
```

# Huginn Installation auf Debian 10
Installationsanleitung: https://gist.github.com/mjhea0/b6b58eefc38985380ff9

### Standard Abhängigkeiten
```
sudo apt update
sudo apt install git default-mysql-server ruby 
```
### Abhängigkeiten für bundle install und foreman
```
sudo apt install ruby-dev make gcc g++ zlib1g-dev default-libmysqld-dev libcurl4
gem install iconv dotenv
```
### Optionale Pakete
```
sudo apt install screen
```
### GIT Repository
```
git clone https://github.com/huginn/huginn.git
cd huginn
```
### rake und bundle installation
```
gem install rake bundle
```
### bei Problemen 
```
gem install bundle:1.17.3
gem install rake:13.0.1
```
### MySQL Dienst starten
```
sudo service mysql start
```
### Installation der Abhängigkeitenfür Huginn
```
bundle install
```
### Erstellen des APP_SECRET_TOKEN für .env
```
rake secret
```
### Bei Problemen 
```
/var/lib/gems/2.5.0/gems/rake-13.0.1/exe/rake secret
```
### Erstellen der Datenbank (ggf. mit rake-13.0.1 ausführen)
```
rake db:create
rake db:migrate
rake db:seed
```
### Webserver starten
```
foreman start
```
### Ggf. in screen starten
```
screen -S huginn
foreman start
[Strg]+[a] [d]
```

### Konfigurationen in .env
```
DOMAIN=hostname
PORT=80
...
RAILS_ENV=production # oder development, je nachdem was passender ist
```
### Konfiguration in config/environemnts/development.rb # oder production.rb, je nach Wahl
```
Rails.application.configure do
  ...
  config.hosts << "hostname"
  ...
```

Anschließend foreman stoppen (Strg+c) und wieder starten. Logindaten für die neue Installation sind `admin` und `password`.

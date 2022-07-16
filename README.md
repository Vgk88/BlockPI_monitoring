# BlockPI_monitoring

1. Встановлюємо графану 
2. Настройка конфигурации prometheus 


# Grafana

Grafana - це платформа для візуалізації моніторингу та аналізу даних

Для встновлення Grafana і робочої схеми ми повині також встановити такі прогарами як Prometheus і Node-exporte

### Заходимо в root користувача
```
sudo su

```

### Спочатку оновлюємо пакети
```
sudo apt update && sudo apt upgrade -y

```
![Image text](https://github.com/cybernekit/RouterSetupGuide/blob/main/img/Screenshot%20from%202022-05-17%2016-49-11.png)
### Устанавливаем docker
(не обов'язково якщо встановлений docker)
```
sudo apt-get install ca-certificates curl gnupg lsb-release -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io -y

```
### Завантажуємо docker-compose.yml
```
cd ~
git clone https://github.com/cybernekit/Grafana-Prometheus.git
cd ~/Grafana-Prometheus

```
![Screenshot from 2022-05-28 13-24-48](https://user-images.githubusercontent.com/59205554/170821373-17d41ca2-0a57-4721-a64d-1dce8ee9f8a3.png)

### Створюємо контейнер
```
docker swarm init
docker stack deploy -c ~/Grafana-Prometheus/docker-compose.yml monitoring

```
![Screenshot from 2022-05-28 13-27-26](https://user-images.githubusercontent.com/59205554/170821426-25288648-174f-4687-a245-08a4746925a9.png)

![Screenshot from 2022-05-28 13-25-13](https://user-images.githubusercontent.com/59205554/170821366-794d7c42-8f30-43fb-8281-30aa0b98c5b5.png)

### Провіряємо чи запустилися контейнери
Не спіши запускати зачикай деякий час щоб воно все запустило.

```
docker ps

```

![Screenshot from 2022-05-28 13-35-21](https://user-images.githubusercontent.com/59205554/170821748-022e38d8-d824-465a-8979-334cff2ca31f.png)

### Тепер провіряємо чи запускається графана 
Відкриваємо google на своєму компютері. 

Водимо адрес через браузер з портом `3000`:
```
http://<IP_address>:3000
```
Ми побачимо наступне(Звичайно якщо все правильно встановилося)

![ngazd4U](https://user-images.githubusercontent.com/102728347/179351515-3004bcf9-edff-4445-8658-416eadf7e41d.jpeg)

Перший раз уведення паролю реєстраційний. Коли ми перший раз ведемо емаіл і пароль, графана запише його в базу даних і з наступного разу, щоб зайти на свою графану потрібно буде вести ці дані.

# Налаштування конфігурації prometheus
Переходимо до конфігурацюї promtheus. Файл називадться `promtheus.yml` і запінюємо його на файл з правильною конфігурацюєю.
```
cd /var/lib/docker/volumes/monitoring_prom-configs/_data
rm prometheus.yml
wget https://raw.githubusercontent.com/MaxMavaIll/BlockPI_monitoring/main/prometheus.yml

```

Тепер замінюємо в цьому файлі `targets` на ваш адрес
```
sed -i 's/your_address/<Your_address>/' /var/lib/docker/volumes/monitoring_prom-configs/_data/prometheus.yml

```

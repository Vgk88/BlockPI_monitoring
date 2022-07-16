# BlockPI_monitoring

1. Встановлюємо графану 
2. Встановлюємо node-exporter
3. Встановлюємо prometheus
4. Настройка конфигурации prometheus 


# Grafana

Grafana - це платформа для візуалізації моніторингу та аналізу даних

Для встновлення Grafana і робочої схеми ми повині також встановити такі прогарами як Prometheus і Node-exporte. 

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
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt update
apt-cache policy docker-ce
sudo apt install docker-ce

```
### Устанавливаем git
(не обов'язково якщо встановлений git)
```
apt install git

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
sudo docker swarm init
sudo docker stack deploy -c ~/Grafana-Prometheus/docker-compose.yml monitoring

```

![Screenshot from 2022-07-16 16-00-16](https://user-images.githubusercontent.com/102728347/179355943-5608a86a-2b56-4a56-b2f7-b31afaabc575.png)


### Провіряємо чи запустилися контейнери
Не спіши запускати зачикай деякий час щоб воно все запустило.

```
sudo docker ps

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

Позамовчуванню user -> `admin`; password -> `admin`.
Далі ви вам запропонує встановити свій пароль, grafana запише його в базу даних і з наступного разу, щоб зайти на свою grafana потрібно буде вести ці дані.

# Налаштування конфігурації prometheus
Переходимо до конфігурацюї promtheus. Файл називадться `promtheus.yml` і запінюємо його на файл з правильною конфігурацюєю.
```
cd /var/lib/docker/volumes/monitoring_prom-configs/_data
rm prometheus.yml
wget https://raw.githubusercontent.com/MaxMavaIll/BlockPI_monitoring/main/prometheus.yml

```

Тепер замінюємо в цьому файлі `your_address` на ваш адрес
```
sed -i 's/your_address/<Your_address>/' /var/lib/docker/volumes/monitoring_prom-configs/_data/prometheus.yml
```
### Перезапускаємо prometheus
Для того щоб перезапустити прометеус нам потрібно дізнатися id контейнера
```
sudo docker ps

```
![Screenshot from 2022-07-16 15-17-24](https://user-images.githubusercontent.com/102728347/179354582-efc6efda-bd83-4a37-93c6-0f3a2b43e6e8.png)

```
sudo docker restart <CONTAINER ID>
```
Все ви підняли prometheus.
Тепер щоб провірити чи він в справному стані, ми водимо в браузері.
```
http://<your_address_grafana>:9090
```
Натискамо Status -> Targets

![tearTmY](https://user-images.githubusercontent.com/102728347/179355096-409b3161-6675-43d9-b543-80b9ecafb370.jpeg)

Якщо у вас такий вигляд то все підключилося і правильно працює 

![Screenshot from 2022-07-16 15-36-24](https://user-images.githubusercontent.com/102728347/179355199-eed91018-6d6c-49bc-a3e3-463b04f64932.png)


wget -q -O node_exporter.sh https://github.com/MaxMavaIll/BlockPI_monitoring/blob/main/node-exporter.sh && chmod +x node_exporter.sh && sudo /bin/bash node_exporter.sh

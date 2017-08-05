# hive

docker-compose.yaml

![Alt text](/services_screenshot.png "Services")

```yaml
version: '3'

services:
  proxy:
    image: no0dles/hive-proxy
    ports:
      - 8000:80
    links:
      - web
      - api
    networks:
      - hive-net
  web:
    image: no0dles/hive-web
    networks:
      - hive-net
  api:
    image: no0dles/hive-api
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    environment:
      - SECRET_KEY=nobodyknowsotto
      - ADMIN_USERNAME=admin
      - ADMIN_PASSWORD=123456
    networks:
      - hive-net

networks:
  hive-net:
```

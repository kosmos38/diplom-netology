# Дипломный блок профессии DevOps-инженер
# Студент Иванов Антон

## Задание 1.











## Задание 1. Яндекс.Облако

Основной файл конфигурации: [main.tf](main.tf.pub)

Файл конфигурации с nat-instance и instance-group: [instance.tf](instance.tf.pub)

Для передачи index.html и ssh ключей использовал файл: [user-kosmos-vm.yaml](user-kosmos-vm.yaml.pub)

При привязке load-balancer к target-group с виртуалками из instance-group столкнулся с проблемой, terraform ругается на отсутвтвие ресурса target-group.id, если же создать отдельный ресурс target-group, то instance-group далее ругается на то что target-group с таким названием уже существует при добавлении ВМ в эту группу...
Решение в документации увидел только одно, целиться на подсеть или отдельные ip адреса, но это не совсем правильно, поэтому сделал "полуавтоматический режим":

    * Балансировщник создаю через terraform
    * target-group при создании instance-group через terraform
    * Добавление target-group в балансировщик через веб консоль

### Скриншоты результатов выполнения:

![alt text](screenshots/grafana_cluster.png "grafana_cluster")​
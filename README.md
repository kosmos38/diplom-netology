# Дипломный блок профессии DevOps-инженер
# Студент Иванов Антон

В данном репозитории находится только теоритическая часть и описание инфраструктуры.
Все конфигурационные файлы расположены в [приватном репозитории](https://github.com/kosmos38/diplom-yandexcloud), ссылку и доступ преподавателю предоставил лично.

Внешняя ссылка на тестовое приложение:
http://diplom.helpdesk38.ru/

Внешняя ссылка на мониторинг grafana:
http://diplom.helpdesk38.ru/grafana/

## Создание облачной инфраструктуры
Конфигарционные файлы в директории terraform/stage, приватного репозитория.

Инфраструктура состоит из:

    * nat-instance      gateway, bastionб NAT и единая точка входа из внешнего мира
    * openvpn-instance  vpn сервер для доступа к закрытой части сети
    * k8s-master1       мастер кластера kubernetes
    * k8s-node1         worker node kubernetes
    * k8s-node2         worker node kubernetes
    * gitlab-instance   сервер GitLab

Скриншот получившейся инфраструктуры в Яндекс.Облако:
![alt text](screenshots/yacloud_overview.png "yacloud_overview")​

Все ресурсы создаются с помощью terraform с использованием Terraform Cloud в качестве backend с привязкой к репозиторию. 

Конфигурационный файл разбит на файлы:

    * main.tf       описание провайдера и бэкенда
    * instance.tf   описание выделяемых серверов
    * network.tf    описание приватной, частной сети, создание ДНС записей и маршрутов

Скриншот проекта в Terraform Cloud:
![alt text](screenshots/tf_overview.png "tf_overview")​

Коммиты в репозиторий привязанный к terraform, с изменениями инфраструктуры:
![alt text](screenshots/github_tf_commits.png "github_tf_commits")​

Применение изменений в репозитории со стороны Terraform Cloud:
![alt text](screenshots/tf_network_dns_apply.png "tf_network_dns_apply")​


## Создание Kubernetes кластера

Кластер устанавливал самостоятельно при помощи готовой ansible конфигурации kubespray. 
Конфигарционные файлы находятся в директории kubespray, приватного репозитория.

Скриншот успешной установки с помощью kubespray:
![alt text](screenshots/kubespray_install.png "kubespray_install")​

Скриншот успешного выполнения kubectl get po -A, .kube/config настроен:
![alt text](screenshots/kube-config.png "kube-config")​



Дополнительно для удобства администрирования установил Lens на локальную машину. 


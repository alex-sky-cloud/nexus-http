#### Развертывание Nexus repository работающего по HTTP

- Описывается быстрый способ развертывания локального репозитория.

 Нужно скопировать конфигурационный файл **nexus.vmoptions** на _хост_, 
 чтобы исправить ошибку.

``bash
docker cp  bb977e7d4742:/opt/sonatype/nexus/bin/nexus.vmoptions  d:/tmp
``

- Добавьте в конец строк

``
-Djava.util.prefs.userRoot=/home/nexus/.java
``

- Скопируйте файл обратно

``bash
docker cp d:/tmp/nexus.vmoptions  bb977e7d4742:/opt/sonatype/nexus/bin
``

- Затем заново войдите в контейнер

``
winpty docker exec -it nexus-http bash
``


- Проверьте что строчка была записана

``
cat /opt/sonatype/nexus/bin/nexus.vmoptions
``

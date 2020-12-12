# innopolis_gitlab
Установка гитлаб с помощью докер

export GITLAB_HOME=/srv/gitlab

docker run --detach   --hostname gitlab003  --publish 443:443 --publish 80:80 --publish 2222:22   --name gitlab   --restart always   --volume $GITLAB_HOME/config:/etc/gitlab   --volume $GITLAB_HOME/logs:/var/log/gitlab   --volume $GITLAB_HOME/data:/var/opt/gitlab   gitlab/gitlab-ce:latest



Согласно официальной документации, контейнеру можно при создании задать политику перезапуска параметром --restart, и демон Docker будет при определённых условиях перезапускать контейнеры сам.

    no - не перезапускает, по умолчанию
    on-failure и on-failure:N - перезапускает контейнер, если его процесс завершается с ошибкой (код возврата не 0), максимум N раз (или постоянно)
    unless-stopped - запускает контейнер при старте демона Docker, если контейнер был активен (не был stopнут ранее)
    always - перезапускает всегда, был ли он ранее остановлен или упал

Но это не особо поможет, если контейнер должен быть запущен только когда некая служба будет запущена на хост-системе. В этом случае за порядком должен следить процесс, который об этой службе знает.


Проблема общения контейнеров между собой

firewall-cmd --zone=public --add-masquerade --permanent 

firewall-cmd --reload 

Логирование:

docker run --log-driver gelf --log-opt gelf-address=udp://localhost:12201 ...

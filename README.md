# innopolis_gitlab
Установка гитлаб с помощью докер

export GITLAB_HOME=/srv/gitlab

docker run --detach   --hostname gitlab003  --publish 443:443 --publish 80:80 --publish 2222:22   --name gitlab   --restart always   --volume $GITLAB_HOME/config:/etc/gitlab   --volume $GITLAB_HOME/logs:/var/log/gitlab   --volume $GITLAB_HOME/data:/var/opt/gitlab   gitlab/gitlab-ce:latest

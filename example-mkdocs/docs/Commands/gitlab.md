# Gitlab Commands

# Backup & migration
root@eoaagit001nx:/data/backup# chmod 777 garthur_gitlab_backup.tar 
root@eoaagit001nx:/data/backup# gitlab-backup restore BACKUP=garthur

# Rsync artifacts
rsync -avz --progress root@redgit002:/git/gitlab/artifacts /data/gitlab/

rsync -avz --progress root@redgit002:/git/gitlab/container-registry /data/gitlab/

# Gitlab Backup final testing

Start Backup (with registry images and artifacts skipped)
Command used:
root@redgit002:~# gitlab-rake gitlab:backup:create SKIP=artifacts,registry RAILS_ENV=production

# restore
root@eoaagit001nx:/data/backup# gitlab-backup restore BACKUP=1709194307_2024_02_29_16.3.2

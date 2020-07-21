# Linux commands

```
# Switch user
sudo su
```

```
# File listing
ls -larth
ls -larth ./newdir
```

```
# grep
pip list | grep abc
pip list | grep -i abc  # Case insensitive
```

```
# Get all running processes
ps -afe | grep celery
ps -ef | less    ; e - list of process currently running; -f fewer info
ps -aux | less   ; a - all users ; u - detail information about each process; x - adds demons process

```


```
# Create virtual environment
virtualenv dqenv
```

```
# Installing and uninstalling pip
sudo python3 -m pip uninstall pip && sudo apt install python3-pip --reinstall
```

```
# Get list of all users
cat /etc/passwd
```

```
# Print in a formatted way
awk -F: '{print $1}' /etc/passwd
```

```
# Run celery:

celery worker -A webapp.sli_celery -Q SLI_COMPUTE -c 2 -Ofair  --loglevel=warning -f celery.logs --pool=solo - concurrency
celery worker -A webapp.sli_celery -Q SLI_COMPUTE -Ofair  --loglevel=warning -f celery.logs --pool=solo -  no concurrency

celery worker -A webapp.sli_celery -Q SLI_PUBLISH -Ofair  --loglevel=warning -f celery.logs --pool=solo

celery worker -A webapp.sli_celery -Q SLI_UPDATE -Ofair --loglevel=warning -f celery.logs --pool=solo
```

```
# Run Scheduler and celery
celery -A data_validation.dv_scheduler beat --loglevel=info -f /var/log/dqcheck/celery-beat.logs
celery -A data_validation.dv_scheduler worker -Q DATA_VALIDATION -c 2 -Ofair --loglevel=info -f /var/logs/dqcheck/celery-worker.logs
```

```
# Kill Celery
ps aux|grep 'celery worker'
sudo kill -9 process_id # here 29042
sudo kill -9 id1 id2 id3 ...
ps auxww | grep 'celery worker' | awk '{print $2}' | xargs kill -9
```

```
# Copy files between remote servers
scp remote_user@remote_host:/path/to/remote/file /path/to/local/file
```

```
# Copy directory between remote servers
scp -r remote_user@remote_host:/path/to/remote/file /path/to/local/file
```

```
# Remove directory
rm -r dirname
```

```
# Remove all files inside directory without removing the directory
rm -r /path/to/directory/*
```

```
# Remove files
rm filename1 filename2
rm *.pdf
```

```
# Get all environment variables
printenv | grep sli_lines
```

```
# Search process in linux
ps -ef | grep '' | grep -v grep
```

```
# Find and delete in linux
find ../ | grep *.pid | xargs rm -f
```

```
# Give permission to user
sudo chmod 777 -R _src_
```

```
# Linux command history
history
```

```
# Celery Health Check
celery inspect ping -A data_validation.dv_scheduler -d celery@$HOSTNAME
```

```
# Inspect celery worker
celery -A data_validation.dv_scheduler inspect active
```

```
# Insepct scheduler
```

```
# Connecting to redis
redis-cli -h ip_address -p 6379 -n DATABASE_NUMBER

redis-cli -h host -p port -a password
```

```
# Purge any specific Queue
celery ampq queue.purge <QueueName>
```

```
# Purge celery tasks
celery -A data_validation.dv_scheduler purge
```

```
# Get your ubuntu version
lsb_release -a
```

```
# To get linux username
whoami
```

```
# Go to the end of the vi file
shift + g
```

```
upload_cmd = [
            "/usr/bin/gsutil", "-o", "Credentials:gs_service_key_file=%s" % G_ENV_VAR_VAL, "cp",
            '/home/jenkins/backups/alphapublish/apdata_1335306_13059_2019-04-26-080419.tar.gz', 'gs://vabackups/alphapublish_dev/'
        ]

1. https://serverfault.com/questions/947726/how-to-use-json-keys-with-google-cloud-gsutil-to-manage-multiple-keys
2. https://serverfault.com/questions/612672/how-do-i-access-a-google-cloud-storage-bucket-using-a-service-account-from-the-c

```
# Activate glcound using service account json file:
gcloud auth activate-service-account --key-file /home/rupesh/VA/AlphaPublish/ap1/alphapublish/gpubsub/.config/gcloud/legacy_credentials/alerts@visiblealpha.com/alphapublish-dev.json

/home/jenkins/.config/gcloud/legacy_credentials/alerts@visiblealpha.com/adc.json
```

```
# Set project for the goole cloud
gcloud config set project va-ins-dev
```

```
# List files inside bucket
gsutil ls gs://alphapublish
```

```
# List authentications
gcloud auth list
gcloud auth revoke rupesh.mishra@visiblealpha.com
gcloud config set account rupesh.mishra@visiblealpha.com
```

```
# Alphapublish issue - use it for login
gcloud auth login
```

```
# Download file from google cloud storage
gsutl cp source destination
```

```
# Change User
su jenkins
```

```
# Change owner
sudo chown -R rupesh:rupesh source
```

```
# Get userid
echo $UID
```

```
# Give permission to a user on a folder
chown -R jenkins:jenkins /var/logs/alphapublish
```

```
# Add user
adduser jenkins
```

```
# Change password
sudo passwd username
```

```
# Add user to sudo group
sudo usermod -aG sudo username
```

```
# Remove linux users
userdel username
```

```
# To delete it's folder also
userdel -r username
```

```
# Supervisor install
sudo apt-get install supervisor
supervisord --version
supervisorctl - list all the services running
```

```
Start service
service supervisor start
```

```
# Setting environment variables
vi /ect/environment
source /etc/environment
```

```
# Connection to MySQL
mysqldump -h server -u username -pPassword databasename
```

```
# Create file in Linux
touch filename
```

```
# Get filesize
du -hs /path/to/directory
```

```
# Renaming files in ubuntu
mv filename1.txt filename2.txt
```

```
# Get CPU information
cat /proc/cpuinfo
```

```
# Get memory info
cat /proc/meminfo
```

```
# Check folder size:
du -j foldername

# Check the drive on which the folder is mounted
df -P file/goes/here | tail -1 | cut -d' ' -f 1
```

```
# Delete file inside current directory
find . -name '*.pyc' -delete

```


```
# Check RAM
free -m in MB
free -g in GB
```

```
# Get disk space
df -kh
```

```
# Search in VI
/varaibletoseach and enter

# For multiple search
press N
```

```
# To check if the service working on the port
telnet
ping  # for the ip
```

```
# Get all the pythons installed
ls -l /usr/bin/python*
```

```
# Get which all pythons available on your machine
which -a python
```

sudo python3 ./awscli-bundle/install -i /usr/local/aws -b /usr/local/bin/aws
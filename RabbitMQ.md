```shell
# Get erland version
 erl -eval 'erlang:display(erlang:system_info(otp_release)), halt().'  -noshell
 ```

```shell
 # Rabbitmq installation
 https://linoxide.com/ubuntu-how-to/install-setup-rabbitmq-ubuntu-16-04/
 ```

```shell
rabbitmq-plugins enable rabbitmq_management
rabbitmqadmin get queue=populate_data
```


```shell
# Check rabbitmq status
sudo systemctl status rabbitmq-server
```


```shell
# Start rabbitmq server
sudo systemctl start rabbitmq-server
```

```shell
# Stop rabbitmq server
sudo systemctl stop rabbitmq-server
```


```shell
# Get location of rabbitmq conf file from the rabbitmq log file
cd /var/log/rabbitmq/
```

```shell
# To get rabbitmq version
sudo rabbitmqctl status
```

```shell
# Ge the list of queue
rabbitmqctl list_queues
```

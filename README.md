# demo-mq
message queue

## Installation on Ubuntu 20.04
1. installation page https://www.rabbitmq.com/install-debian.html#installation-methods
2. Install Erlang/OTP
    1. add repository signing key: 
        ```
        curl -fsSL https://github.com/rabbitmq/signing-keys/releases/download/2.0/rabbitmq-release-signing-key.asc | sudo apt-key add -
        ```
    2. use server key
        ```
        sudo apt-key adv --keyserver "hkps://keys.openpgp.org" --recv-keys "0x0A9AF2115F4687BD29803A206B73A36E6026DFCA"
        ```
    3. enable https transport
        ```
        sudo apt-get install apt-transport-https
        ```
    4. add source list file: 
    As with all 3rd party Apt (Debian) repositories, a file describing the repository must be placed under the /etc/apt/sources.list.d/ directory. /etc/apt/sources.list.d/bintray.erlang.list is the recommended location.
    5. ```deb https://dl.bintray.com/rabbitmq-erlang/debian focal erlang-22.x```
    6. install
        ```
        sudo apt-get install -y erlang-base \
                        erlang-asn1 erlang-crypto erlang-eldap erlang-ftp erlang-inets \
                        erlang-mnesia erlang-os-mon erlang-parsetools erlang-public-key \
                        erlang-runtime-tools erlang-snmp erlang-ssl \
                        erlang-syntax-tools erlang-tftp erlang-tools erlang-xmerl
        ```
3. Install rabbitmq
    ```
    # import PackageCloud signing key
    wget -O - "https://packagecloud.io/rabbitmq/rabbitmq-server/gpgkey" | sudo apt-key add -
    ```
    ```
    sudo apt-get update -y
    ```
    ```
    sudo apt-get install rabbitmq-server -y --fix-missing
    ```

## Start the Server
```
service rabbitmq-server start
```

## Monitor and CLI
```
rabbitmqctl status
sudo rabbitmq-diagnostics ping
sudo rabbitmq-diagnostics status
sudo rabbitmq-diagnostics environment
sudo rabbitmq-diagnostics node_health_check
```

## Running as docker image:
```
docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management
```

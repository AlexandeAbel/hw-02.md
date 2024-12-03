# Домашнее задания "Система мониторинга Zabbix" <Ничипуренко А.Е>
## Задание 1.

*Установите Zabbix Server с веб-интерфейсом.*

    sudo su

    apt install postgresql

    wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest+ubuntu24.04_all.deb

    dpkg -i zabbix-release_latest+ubuntu24.04_all.deb   

    apt update

    apt install zabbix-server-pgsql zabbix-frontend-php php8.3-pgsql zabbix-apache-conf zabbix-sql-scripts zabbix-agent

    sudo -u postgres createuser --pwprompt zabbix

    sudo -u postgres createdb -O zabbix zabbix

    zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

    nano /etc/zabbix/zabbix_server.conf 
        DBPassword=password

    systemctl restart zabbix-server zabbix-agent apache2
    
    systemctl enable zabbix-server zabbix-agent apache2


## Задание 2.

*Установите Zabbix Agent на два хоста.*
    *Configuration > Hosts*
    ![Configuration>Hosts](https://github.com/AlexandeAbel/hw-02.md/blob/main/img/2.1.png)
    *Zabbix-Agent log*
    ![zabbix agent](https://github.com/AlexandeAbel/hw-02.md/blob/main/img/2.2.1.png)
    ![zabbix agent](https://github.com/AlexandeAbel/hw-02.md/blob/main/img/2.2.png)
    *Monitoring > Latest data* 
    ![Latest-data](https://github.com/AlexandeAbel/hw-02.md/blob/main/img/2.3.png)
    ![Latest-data](https://github.com/AlexandeAbel/hw-02.md/blob/main/img/2.3.1.png)
    *Использованные команды:*
    sudo cat /var/log/zabbix/zabbix_agentd.log 



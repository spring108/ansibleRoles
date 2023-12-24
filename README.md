## DevOps \ Домашнее задание №9 - Ansible Roles

Написать Ansible роли, 
которые подготавливают сборочное и продовое окружение на 2-х нодах. 
На сборочной ноде производится сборка проекта, на продовой - запуск.



## Команды на Slave1 & Slave2:
  - #### Подготовка инфраструктуры:
    - Настройка авторизации по ключам от Master
      - sudo nano /etc/ssh/sshd_config
      - sudo service sshd restart
      - sudo passwd root
    - sudo apt install python -y


## Команды на Master:
  - #### Подготовка инфраструктуры:
    - sudo apt update
    - sudo apt-get update
    - sudo apt-get install mc -y
    - sudo mc
    - Настройка авторизации по ключам до Slave1 и Slave2
      - ssh-keygen
      - ssh-copy-id /root/.ssh/id_rsa.pub root@Slave1
      - ssh-copy-id /root/.ssh/id_rsa.pub root@Slave2
    - sudo apt update
    - sudo apt install git -y
    - apt policy ansible
    - sudo apt install ansible -y
    - ansible --version #ansible 2.5.1
  - #### Запуск сервисов:
    - cd /tmp
    - git clone https://github.com/spring108/ansibleRoles.git
    - cd /tmp/ansibleRoles
    - cp ./hosts /etc/ansible
    - ansible all -m ping
    - ansible-playbook playbook.yml --ask-vault-pass
    - go to http://[Slave2_public_IP]:8080/hello/  #without docker
    - go to http://[Slave2_public_IP]:8081/hello/  #with docker

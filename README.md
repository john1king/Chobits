# Chobits

Ansible 自动化部署脚本

## 使用方法

安装 Ansible

    pip install ansible

在项目目录下添加 ansible.cfg 配置文件

    [defaults]
    inventory=./hosts
    roles_path=./etc/roles

编辑 `./hosts` 文件, 下例为连接到 vagrant 虚拟机的 host 文件配置

    foo ansible_port=2222 ansible_host=127.0.0.1 ansible_user=foo ansible_ssh_private_key_file=/path/to/private_key ansible_ssh_common_args='-o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no' ansible_python_interpreter='/usr/bin/python3'

测试服务器连接

    ansible all -m ping

编写 `playbook.yml`

    - hosts: foo
      roles:
        - chruby
        - ruby_install

执行 playbook

    ansible-playbook playbook.yml

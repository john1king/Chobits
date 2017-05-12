Ansible 自动化部署脚本


安装 Ansible

    pip install ansible

编辑 `./hosts` 文件, hosts 文件的位置可以通过 ANSIBLE_HOSTS 环境变量配置。下例为连接到 vagrant 虚拟机的 host 文件配置

    foo ansible_port=2222 ansible_host=127.0.0.1 ansible_user=foo ansible_ssh_private_key_file=/path/to/private_key ansible_ssh_common_args='-o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no' ansible_python_interpreter='/usr/bin/python3'

测试服务器连接

    ansible all -m ping -i ./hosts

编写 playbook `test.yml`

    - hosts: foo
      roles:
        - chruby
        - ruby_install

执行

    ansible-playbook -i ./hosts test.yml

    

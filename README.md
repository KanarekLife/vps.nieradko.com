# vps.nieradko.com

Repository with configuration and setup instructions for my personal VPS server.

## Ansible

Run the commands below on your local PC in order to configure the VPS server with ansible.

```bash
$ cd ansible/
$ python3 -m venv .venv/        # create python's virtual environment
$ source .venv/bin/activate     # activate it
$ pip install -r requirements.txt
$ ansible-playbook -i <ip_address>, create_user.yml -K -u rocky # setup admin user and change passwords
$ ansible-playbook -i <ip_address>, setup_vps.yml -u kanareklife -K # setup VPS
```

## Kubernetes

```bash
$ curl -s https://fluxcd.io/install.sh | sudo bash  # install fluxCD cli
$ ssh-keygen -f ~/.ssh/id_fluxcd                    # generate ssh key that will be used to fetch latest repo status from github
$ flux bootstrap git --url=ssh://git@github.com/KanarekLife/vps.nieradko.com --branch=main --private-key-file=/home/kanareklife/.ssh/id_fluxcd --path=kubernetes/cluster
```
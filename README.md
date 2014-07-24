Using Ubuntu, install ansible:

    sudo apt-get install python-pip python-dev build-essential ansible -y

Install boto:

    sudo pip install boto

Setup the AWS keys into environment variables:

    AWS_ACCESS_KEY_ID
    AWS_SECRET_ACCESS_KEY

Overwrite `/etc/ansible/hosts` with [this file](https://raw.githubusercontent.com/ansible/ansible/devel/plugins/inventory/ec2.py):

    wget https://raw.githubusercontent.com/ansible/ansible/devel/plugins/inventory/ec2.py
    wget https://raw.githubusercontent.com/ansible/ansible/devel/plugins/inventory/ec2.ini
    sudo mv /etc/ansible/hosts /etc/ansible/hosts-bak
    sudo mv ec2.py /etc/ansible/hosts
    sudo mv ec2.ini /etc/ansible/
    sudo chmod +x /etc/ansible/hosts

Provided you have EC2 instances tagged with key: class, value: web, grab this repo, then try the following:

    ansible-playbook production web.yml --list-hosts

Which returns:

    ERROR: production: No JSON object could be decoded

Chef-solo and Knife-solo
========================

Install knif-solo

    gem install knife-solo
    gem install knife-ec2
    knife configure -r . --defaults

Create repo

    knife kitchen <this_repo>

Create cookbooks

    cd <this_repo>
    knife cookbook create apt -o cookbooks
    knife cookbook create build-essential -o cookbooks
    knife cookbook create rvm -o cookbooks

Configure node

    nano nodes/192.184.200.1.json

    { "run_list": ["recipe[rvm::ruby_192]"] }

Start EC2 instance, enable ssh and get its public IP and key pair (knife.pem)

    knife prepare -i ~/.chef/knife.pem ubuntu@192.184.200.1

Setup EC2 instance

    knife cook -i ~/.chef/knife.pem ubuntu@192.184.200.1
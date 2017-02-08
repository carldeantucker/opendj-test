# Readme

To create the two machines run 

`vagrant up --provision`

This will generate one master (provisioned with ansible using shell provisioner) and one ldap server

then ssh to master server

`vagrant ssh master`

Due to some ssh host checking, just ssh to the ldap box confirming the caching of the key ( I would have simplified this if I had time)

`ssh 192.168.33.12`

You can now control + c back to the master and from there you can provision the ldap server using the following command

`ansible-playbook -i /vagrant_data/hosts /vagrant_data/opendj.yml`

Once this has been provision ( it will import test data that I needed to generate as the provided data would not import), you can query the generated data using the python script as follows

`python ldapsearch.py`



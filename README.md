This repo consists of Ansible playbooks to install splunk server

Download the latest rpm files from splunk and place them in the files directory and update the vars in vars/main.yml.


Splunk download Links
=============================================================

Splunk Enterprise 7.0.2 for Linux
*********************************************
wget -O splunk-7.0.2-03bbabbd5c0f-Linux-x86_64.tgz 'https://www.splunk.com/bin/splunk/DownloadActivityServlet?architecture=x86_64&platform=linux&version=7.0.2&product=splunk&filename=splunk-7.0.2-03bbabbd5c0f-Linux-x86_64.tgz&wget=true'

wget -O splunk-7.0.2-03bbabbd5c0f-linux-2.6-amd64.deb 'https://www.splunk.com/bin/splunk/DownloadActivityServlet?architecture=x86_64&platform=linux&version=7.0.2&product=splunk&filename=splunk-7.0.2-03bbabbd5c0f-linux-2.6-amd64.deb&wget=true'

https://download.splunk.com/products/splunk/releases/7.0.2/linux/splunk-7.0.2-03bbabbd5c0f-linux-2.6-x86_64.rpm



_________________________________________________________________________________________________________________________________________
Windows
**********************************************
wget -O splunk-7.0.2-03bbabbd5c0f-x64-release.msi 'https://www.splunk.com/bin/splunk/DownloadActivityServlet?architecture=x86_64&platform=windows&version=7.0.2&product=splunk&filename=splunk-7.0.2-03bbabbd5c0f-x64-release.msi&wget=true'

https://download.splunk.com/products/splunk/releases/7.0.2/linux/splunk-7.0.2-03bbabbd5c0f-linux-2.6-x86_64.rpm


https://download.splunk.com/products/splunk/releases/7.0.2/windows/splunk-7.0.2-03bbabbd5c0f-x64-release.msi

Ansible script to automate installation of splunk universal forwarder on multiple windows hosts
1.	---
2.	 - name: Install software
3.	   hosts: mygroup
4.	   gather_facts: false
5.	   tasks:
6.	     - name: Install Splunk Forwarder
7.	       win_chocolatey:
8.	         name: splunk-universalforwarder
9.	         state: present
Make sure in your inventory file the following is configured:
1.	 [mygroup]
2.	 192.168.0.1
3.	 192.168.0.2
4.	 192.168.0.3
5.	 192.168.0.4
6.	 [mygroup:vars]
7.	 ansible_user=<USERNAME>
8.	 ansible_password=<PASSWORD>
9.	 ansible_port=5986
10.	 ansible_connection=winrm
11.	 ansible_winrm_server_cert_validation=ignore
Run playbook
1.	 ansible-playbook install_splunk_fwdr.yml

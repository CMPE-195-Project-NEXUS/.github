# Project Nexus - A CMPE 195 Senior Project
### San Jose State University (Spring/Summer 2022)

#### By Gianine Dao, Alfonso Garibay, Aaron Rice, Yabsera Tasaw
##### Teaching Advisor: Mahima Suresh

## Mobile App - Prototype

## Gun JS Backend with React Implimentaion - Beta

## Matrix(Server)/Cinny(Client) Implimentation - Final
To deploy this on a public URL be sure to follow the guidence outlined below to configure your domain's DNS to delegate Matrix related traffic.

The Matrix API will use unique identifier like `@<username>:<your-domain>` in authermtication and establishing identities on the server.

The ~Ansible-Deployment-Script-for-Nexus-Matrix-configuration~ is a helper ansible script created by Slavi Pantaleev (https://github.com/spantaleev) and extended by Matrix contributors to automate the task of provisioning the Matrix on your Ubuntu server. This anisible playbook is a repository whcih should be cloned to an ansible supported OS that has the ability to SSH into the Ubuntu host. All the parameters and repositories used by in the Nexus project have been compiled in the ~inventory/host_vars~ folder. To modify this to work on another server domain be sure to rename the matrix.justdrake.com sub-folder to `matrix.<your-domain>` and enter your Ubuntu host information in the Hosts file. `ansible_host=<your-public-ip>` and `ansible_ssh_user=<admin-user-account-ubuntu>`. `become` and `become_useer` should be set to true if the user account deticated to hosting the server doen't have root permisions. 

Additional information can be found in the `hosts` file. If you decisde to host this locally you can skip part 1.

#### 1. Setup DNS Server to connect your domain address to your Ubuntu server. 
The following configuration settings need to be added to yoru DNS service record for your domain. 

| Type  | Host                         | Priority | Weight | Port | Target                 |
| ----- | ---------------------------- | -------- | ------ | ---- | ---------------------- |
| A     | `matrix`                     | -        | -      | -    | `matrix-server-IP`     |
| CNAME | `nexus`                      | -        | -      | -    | `matrix.<your-domain>` |
| SRV   | `_matrix-identity._tcp`      | 10       | 0      | 443  | `matrix.<your-domain>` |

#### 2. Configure the Ansible Playbook.
After cloning the playbook to a secondary host that has Ansible 2.8 or later installed, you can modify our precompiled vars.yml file for your domain.
This can be found in ~inventory/host_vars/`matrix.<your-domain>`~.
`matrix_domain: <your-doamain>` is used as avariable accross the deployment script to provision all services to your domain.
`matrix_ssl_lets_encrypt_support_email` is used to register your Let's Encrypt account with the certificate authority for SSL connections.
`matrix_postgres_connection_password` is used to set up authentication for your database connection.

#### 3. Setup your server enviroment.
You will need the latest Ubuntu installed on a computer with a Static IP or establish a Dynamic DNS which will need to be used intead of your public IP in the DNS configuration. If your computer is behind a network firewall port forwarding will need to be enabled for the following ports:
  - `80/tcp`: HTTP webserver
  - `443/tcp`: HTTPS webserver
  - `3478/tcp`: TURN over TCP (for Synapse the app service)
  - `3478/udp`: TURN over UDP (for Synapse the app service)
  - `5349/tcp`: TURN over TCP (for Synapse the app service)
  - `5349/udp`: TURN over UDP (for Synapse the app service)
  - `8448/tcp`: Matrix Federation API HTTPS webserver.
  - the range `49152-49172/udp`: TURN over UDP (for Synapse the app service)

Synapse is the service thatenables the extensability of the Matrix server accross multiple 3rd party networks. 
Federation is the Matrix API that connects other Matrix servers to your host. (Not used but Matrix documentation recommends this remain open).

Ensure that you are able to connect to your server from the secondary host that has the playbook cloned via a public key. You can find more inforamtion about enabling this type of authentication from https://www.ssh.com/academy/ssh/config

#### 4. Deploy the ansible script.
Once you point your terminal screen to the directory which the repro was cloned to you can run the following terminal command. Note this is a universal script for all Matrix built in services only the items used in the backend of the nexus project are instantiated.
```bash
ansible-playbook -i inventory/hosts setup.yml --tags=setup-all
```
#### 5. Configuring iMessage (Optional)
Configuring iMessage will require a seperate Mac host. 
The Mac host will need to be be able to connect to the Matrix server over the same network via ssh and will need to be signed into an iMessage account in the messages app. 

wsproxy is a Matrix web proxy which is able to automate the creation of identites into synapse. This is used to instatiate chat converrsations and transfer message data that from the Mac to the Matrix server you are hosting. This is run on Ubuntu server and will listen for messages on port 6001. 

Barcelona is an swift framework that taps into the sqllite database the Mac is using to parse and store incoming iMessage data from the iMessage server for the authenticated account. Because it is accessing other retricted Apple framworks it will be required that you disable System Integrety Protection (SIP) on the Mac that is being configured for this purpose. Information on how to complete this can be found on the Apple Developer website. https://developer.apple.com/documentation/security/disabling_and_enabling_system_integrity_protection

Once you clone the wsproxy on the Ubuntu hose you can run `./wsproxy` to begin listening for traffic and deliver it to synapse to interface with Nexus.

After disabling SIP on the Mac host and ensuring the Mac is sending and recicving the desired messages from the account it is signed into you can download and run the catalyst application for Mautrix found in the readme for this repository to continue. Additional work is needed to get this fully functional but at this time messages sent from an iOS device or Mac signed into iMessage is deliver to Nexus. Reciving of messages is still not working due to an issue with wsproxy not being able to create identites for the incomming messages to be delivered to.
<!--

**Here are some ideas to get you started:**

🙋‍♀️ A short introduction - what is your organization all about?
🌈 Contribution guidelines - how can the community get involved?
👩‍💻 Useful resources - where can the community find your docs? Is there anything else the community should know?
🍿 Fun facts - what does your team eat for breakfast?
🧙 Remember, you can do mighty things with the power of [Markdown](https://docs.github.com/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)
-->

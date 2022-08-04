# Project Nexus - A CMPE 195 Senior Project
### San Jose State University (Spring/Summer 2022)

#### By Gianine Dao, Alfonso Garibay, Aaron Rice, Yabsera Tasaw
##### Teaching Advisor: Mahima Suresh

## Mobile App - Prototype
#### Our Universal React Project
<p>
  <!-- iOS -->
  <a href="https://itunes.apple.com/app/apple-store/id982107779">
    <img alt="Supports Expo iOS" longdesc="Supports Expo iOS" src="https://img.shields.io/badge/iOS-4630EB.svg?style=flat-square&logo=APPLE&labelColor=999999&logoColor=fff" />
  </a>
  <!-- Android -->
  <a href="https://play.google.com/store/apps/details?id=host.exp.exponent&referrer=blankexample">
    <img alt="Supports Expo Android" longdesc="Supports Expo Android" src="https://img.shields.io/badge/Android-4630EB.svg?style=flat-square&logo=ANDROID&labelColor=A4C639&logoColor=fff" />
  </a>
  <!-- Web -->
  <a href="https://docs.expo.dev/workflow/web/">
    <img alt="Supports Expo Web" longdesc="Supports Expo Web" src="https://img.shields.io/badge/web-4630EB.svg?style=flat-square&logo=GOOGLE-CHROME&labelColor=4285F4&logoColor=fff" />
  </a>
</p>

##### 👍 Getting Started

- Clone the Repo to your local device 
- Using your terminal of choice navigate into the Nexus-Proto file
- Once in here, run this -> `npm i expo` , in your terminal. This will install expo (for simulating the app)
- Now that you hopefully have Expo installed run the following command -> `expo start`, to start expo
- You should now see a simple gui in your terminal and you can simply select the device youd like to simulate with :)

##### 🚀 How to use

- Install packages with `yarn` or `npm install`.
  - If you have native iOS code run `npx pod-install`
- Run `yarn start` to start the bundler.
- Open the project in a React runtime to try it:
  - iOS: [Client iOS](https://itunes.apple.com/app/apple-store/id982107779)
  - Android: [Client Android](https://play.google.com/store/apps/details?id=host.exp.exponent&referrer=blankexample)
  - Web: Any web browser

##### Adding Native Code

This project can be run from a web browser or the Expo client app. You may find that you want to add more native code later on. You can do this by ejecting the project and rebuilding it yourself.

- Run `yarn eject` to create the native projects.
- You can still run your project in the web browser or Expo client, you just won't be able to access any new native modules you add.

##### Publishing

- Deploy the native app to the App store and Play store using this guide: [Deployment](https://docs.expo.dev/distribution/app-stores/).
- Deploy the website using this guide: [Web deployment](https://docs.expo.dev/distribution/publishing-websites/).

##### 📝 Notes

- Learn more about [Universal React](https://docs.expo.dev/).
- See what API and components are [available in the React runtimes](https://docs.expo.dev/versions/latest/).
- Find out more about developing apps and websites: [Guides](https://docs.expo.dev/guides/).

## Gun JS Backend with React Implimentaion - Beta
#### 1. Clone and run Gun-app.
Getting Started with Create React App This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app). 
Available Scripts In the project directory, you can run: 
`npm start` Runs the app in the development mode.\ Open [http://localhost:3000](http://localhost:3000) to view it in your browser. The page will reload when you make changes.\ You may also see any lint errors in the console. ### `npm test` Launches the test runner in the interactive watch mode.\ See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information. ### `npm run build` Builds the app for production to the `build` folder.\ It correctly bundles React in production mode and optimizes the build for the best performance. The build is minified and the filenames include the hashes.\ Your app is ready to be deployed! See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information. 
`npm run eject` **Note: this is a one-way operation. Once you `eject`, you can't go back!** If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project. Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own. You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it. 

##### Learn More 
You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started). To learn React, check out the [React documentation](https://reactjs.org/). Code Splitting This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting) Analyzing the Bundle Size This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size) Making a Progressive Web App This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app) Advanced Configuration This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration) Deployment This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment) `npm run build` fails to minify This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)

#### 2. Run the Relay Server 
The relay server is an independent server that keeps records of peers and rooms for backup and indexing peers and room 
To get strarted run `npm start` 
The relay server must be running for the webapp to work URL of our webapp https://nexus-sjsu.web.app/

## Matrix(Server)/Cinny(Client) Implimentation - Final
**Self-deployment is optional. This will be hosted on https://nexus.justdrake.com until at least August 15, 2022 for evaluation.**

To deploy this on a public URL be sure to follow the guidence outlined below to configure your domain's DNS to delegate Matrix related traffic.

The Matrix API will use unique identifier like `@<username>:<your-domain>` in authermtication and establishing identities on the server.

The **Ansible-Deployment-Script-for-Nexus-Matrix-configuration** is a helper ansible script created by Slavi Pantaleev (https://github.com/spantaleev) and extended by Matrix contributors to automate the task of provisioning the Matrix on your Ubuntu server. This anisible playbook is a repository whcih should be cloned to an ansible supported OS that has the ability to SSH into the Ubuntu host. All the parameters and repositories used by in the Nexus project have been compiled in the **inventory/host_vars** folder. To modify this to work on another server domain be sure to rename the matrix.justdrake.com sub-folder to `matrix.<your-domain>` and enter your Ubuntu host information in the Hosts file. `ansible_host=<your-public-ip>` and `ansible_ssh_user=<admin-user-account-ubuntu>`. `become` and `become_useer` should be set to true if the user account deticated to hosting the server doen't have root permisions. 

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
This can be found in **inventory/host_vars/`matrix.<your-domain>`**.
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
ansible-playbook -i inventory/hosts setup.yml --tags=setup-all -K
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

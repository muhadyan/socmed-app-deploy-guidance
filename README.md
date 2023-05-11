  <h1 align="center">Social Media API Deployment Instructions</h1>

## 1. Create AWS EC2 Instance

Go check out this [documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/get-set-up-for-amazon-ec2.html) for set up the AWS Account and AWS EC2 Instance.

## 2. Connect to your Instance

- Open terminal
- Go to the directory where your key pair (.pem file) is stored.
- Run the ssh command. Example:

```bash
$ ssh -i "your-key-pair-name.pem" ubuntu@ec1-2-34-56-789.compute-1.amazonaws.com
```

## 3. Install Node, NPM & PM2 on the EC2 instance

```bash
# this line installs curl on the Ubuntu server
$ sudo apt-get install curl

# this line downloads Node.js
$ curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -

# this line installs node
$ sudo apt-get install nodejs

# install PM2
$ npm install pm2@latest -g
```

## 4. Clone the app

```bash
$ git clone git@github.com:muhadyan/social-media-nestjs.git
```

## 5. Install the dependencies

```bash
$ npm install
```

## 6. Copy the env

- Copy the env.example file and rename it to .env
- Fill all the key with your credentials value

## 7. Build the app

```bash
$ npm run build
```

## 8. Run the app

```bash
$ pm2 start dist/main.js
```

## 9. Add the app's port

- Open the list of instances
- Choose the instance where the app are running
- Go to the Security tab
- Click the security group
- Click "Edit inbound rules"
- Fill as below and then click save:
  - Type : Custom TCP
  - Port range : 3000
  - Source : Anywhere-IPv4

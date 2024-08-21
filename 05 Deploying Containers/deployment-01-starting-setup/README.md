# Directory contains?

This Directory contains a simple `nodeJS` application with a docker file. So lets try to `build` and `run` this,

```
docker build -t node-dep-example .
```
```
docker run -d --rm --name node-dep -p 5000:5000  node-dep-example
```
and this is what it looks at `localhost:5000`,

![image](https://github.com/user-attachments/assets/d18258ed-ad03-4f54-b197-889b830c9536)

## AWS EC2 Instance

Once you sucessfully create a new `free-tier` account, you can create a new instance in the management dashboard with the default settings.

> **_Note:_** Do not forget to download the `<name>.pem` file which is the key to access the cloud instance from the remote machine.

- It may take a while for the cloud instance state to change from `pending` to `running`
  
![image](https://github.com/user-attachments/assets/03ce6bcc-de3d-436e-ba93-f68360c574d8)

And then go to the project root folder( make sure to put the .pem file into the project root folder) to connect to the instance via `ssh` key.

- To connect, click on the connect in the running-instances page and something like pops out which are the instructions to set up using ssh key.

![Screenshot 2024-08-21 at 9 48 17 AM](https://github.com/user-attachments/assets/7a799bb9-14ff-462f-b75f-9e08829a1d72).

And now you should be able to see the ipaddress of the instance in your terminal, and follow the following steps:

```
sudo yum update -y
```
```
sudo yum -y install docker
```
```
sudo service docker start
```
```
sudo usermod -a -G docker ec2-user
```

Thereafter, you can check whether Docker is available by running:

```
docker version
```


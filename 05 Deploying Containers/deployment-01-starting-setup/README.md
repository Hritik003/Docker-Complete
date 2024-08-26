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
---

- Maybe you want such a more managed approach. And I would indeed recommend that you go for a more **managed approach** because then you can focus on writing your source code and building your dockerized application, and you don't have to focus on managing `servers` and `firewalls` and `networks`.

- That requires a totally different set of skills, and as a `software` and `web developer`, you might not have that set of skills. So that's why using this **EC2 instance** was a nice first example, which I mainly used to show you that you can't really just install **Docker** on a different machine and then use your container data as you used it locally,

- but for real applications, bigger applications, maybe all the applications with `multiple containers`, it might not be ideal unless you really know what you're doing. Then if you do know what you're doing, having this full control over everything could indeed be an advantage.

- But in many cases it will not be, and therefore, throughout the rest of this module, we are **not going** to use EC2, instead I'll show you other services, which we could use which are managed and we therefore then, don't have to take care about everything.


<img width="1035" alt="image" src="https://github.com/user-attachments/assets/c9f3a7d6-ab5d-4640-823e-1b64aee29582">

---

## Note on a common error:
<img width="1196" alt="Screenshot 2024-08-21 at 9 10 24 PM" src="https://github.com/user-attachments/assets/c28d026e-f7c2-48f9-9c56-ebca7f2ede7c">
The above error occurs because of CORS policy which does not allow requests to localhost(default port 80) without certain headers on our local machine. A work aound for this is to change the listening and exposed port to some other port say, 5000. It should work fine then. Note that port 80 of container can still be used. We just cannot listen to port 80 of our local machine.

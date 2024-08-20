# Final Module i.e Deploying Containers

Yeah, so we are finally here to learn about pushing containers onto **production!**. And what works on your local machine also works after deployment.

## What may sound strange?

- **Bind Mounts** shouldnt be used in production. 
- Containerized apps **might need** a build step (eg. react apps).
- Mutli-container projects might **need to be split**(or should be split) across multiple hosts/remote machines
- **Trade offs** between control and responsibility might be worth it.


## Kick-off

A  basic first example: `Standlone NodeJS App`

<img width="1067" alt="image" src="https://github.com/user-attachments/assets/a189a64e-f873-43bc-b7e0-4a95090c9ec9">

### Hosting providers

There are hundreds and thousands of Docker-supporting hosting providers out there! but we are going to trial on the popular ones:
- aws
- azure
- google cloud

### which one are we going to use?

The [AWS EC2](https://aws.amazon.com/free/?nc2=h_ql_pr_ft&all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all]) is a service that allows you to spin up and manager your own remote machines.

And for that we will be needing a dockerized file to start with. Hence we proceed with [Starter Repository](https://github.com/Hritik003/Docker-Complete/tree/main/05%20Deploying%20Containers/deployment-01-starting-setup)



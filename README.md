# create-and-mount-EFS-using-CLI

Create and connect to an EC2 Instance, create EFS volume and  attach to already running instance using CLI

aws ec2 run-instances --image-id ami-03e88be9ecff64781 --count 1 --instance-type t2.micro --key-name Session3 --security-groups my-sg

aws efs create-file-system --performance-mode generalPurpose --throughput-mode bursting --encrypted --tags Key=EFS,Value=Session10

aws efs create-mount-target --file-system-id fs-02c7d79a98d6bf661 --subnet-id subnet-0128f5b2937d6e48e --security-groups sg-071c9dacdbac50f20

Run the following command to install EFS helper on both the EC2 instance.

sudo yum install -y amazon-efs-utils

sudo yum install -y nfs-utils

copy the below command from select EFS then click attach and you will find this
sudo mount -t efs -o tls fs-02c7d79a98d6bf661:/ efs
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport fs-02c7d79a98d6bf661.efs.eu-west-2.amazonaws.com:/ efs

To test use:
sudo mount -fav

C:\>cd users

C:\Users>cd Shourya

![image](https://user-images.githubusercontent.com/109040029/195967890-cca879ad-69e4-4d2e-bcfb-07177fcea2ff.png)


![image](https://user-images.githubusercontent.com/109040029/195967895-df0a4de7-7944-4a03-b1a6-04b3e425d73d.png)


![image](https://user-images.githubusercontent.com/109040029/195967897-402726e8-dc1c-4cb6-9d6a-a6cb6424a702.png)

![image](https://user-images.githubusercontent.com/109040029/195967901-0e9c27ae-19d5-4373-90ed-540e5ac057ee.png)



To unmount the EFS run the below command:

umount -f /usr/bin/efs

aws ec2 terminate-instances --instance-ids i-0e33a5732cdc15ce4

aws efs delete-file-system --file-system-id fs-02c7d79a98d6bf661

![image](https://user-images.githubusercontent.com/109040029/195967987-627a2389-8fa3-478e-ba08-6c42436c388b.png)



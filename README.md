# Serverless-Web-Application-on-AWS
In this project, I will build a serverless web application using AWS Lambda, DynamoDB, CloudFront and S3. The application will allow users to create, read, update, and delete (CRUD) items from a DynamoDB table


![Screenshot 2024-03-07 142300](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/eef7a119-0118-4425-81f6-e0b7902cb5a4)
Steps to Build the Project:
- Create a DynamoDB table to store the items
- Build a Lambda function to handle the CRUD operations on the DynamoDB table
- Use S3 to store and host the web application's static files (HTML, CSS, and JavaScript)
- Create a CloudFront distribution to serve the S3-hosted static files with low latency

1.  Creating S3 Bucket
- First I will log into my AWS console and click on S3
![Screenshot 2024-02-24 013834](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/00986239-5a92-493a-9abe-070729c2bb56)
- I will then create a Bucket as I have no Buckets created
![Screenshot 2024-02-24 014043](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/5e7ce18f-dc41-414c-85ea-7309d3d7c756)
- With configuring the Bucket, It is important to put a name that is globally recognizable and your AWS region is close to your actual location
![Screenshot 2024-02-24 014712](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/a9b47cfb-eee8-438c-91f1-049545b4208f)
- I left the Object Ownership as default as all objects will be owned on this account
- I Blocked Public Access so outsiders don't have access to the S3 Bucket
![Screenshot 2024-02-24 014813](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/ddc1f1fc-878a-4a04-bff4-deec21932f02)
- I left versioning as disabled currently as it was not needed at that point
- I also left the Encryption Key type to Amazon S3 managed keys( SSE-S3)
- Bucket Key was left as Enabled
- After these configurations, I created the S3 Bucket (May take a few seconds to create)
![Screenshot 2024-02-24 015513](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/07443d15-ae57-45e8-b6f8-bad35ac87ee0)
![Screenshot 2024-02-24 015525](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/81b85208-17eb-4394-b9e2-b9fa25b8c2ba)
- The S3 Bucket has been successfully created
![Screenshot 2024-02-24 015625](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/c1471301-0879-4c3e-b97e-2f745b7f3e95)
- Now I will upload the HTML, CSS, and Javascript files into the bucket
- First I clicked on the S3 Bucket itself and it presented the upload button
![Screenshot 2024-02-24 132942](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/79242d9b-5020-46fb-9277-6802bc0204f0)
![Screenshot 2024-02-24 133024](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/8b2625f5-dd0e-4f52-a341-0662a46603f4)


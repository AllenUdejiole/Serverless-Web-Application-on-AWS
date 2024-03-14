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
- Next, I clicked on Add Files to bring the files from my local computer to the S3 Bucket
- I selected the 3 files “index.html”, “script.js” and “style.css”
![Screenshot 2024-02-24 133751](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/a3d54efc-4de2-4596-b506-a8789def5f65)
![Screenshot 2024-02-24 134103](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/b2d38329-420a-43bc-a0d9-d517bb2b44ca)
- The files have been dragged
![Screenshot 2024-02-24 135046](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/410321b8-9aee-4408-96de-97507d5ae645)
- Now I will upload them
![Screenshot 2024-02-24 134923](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/a5ce1396-26b6-4091-8377-5df4b89f1738)
- They were successfully uploaded
![Screenshot 2024-02-24 135229](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/59ebdc55-79a9-4c83-8481-829244361cb2)

2.  Setup AWS CloudFront
  
- To set up the Cloud Front Distribution, I will access this on the search bar on the aws console
![Screenshot 2024-02-25 233758](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/ef8593db-5ca7-405b-ba68-31a7f1bc4123)
- The purpose of using CloudFront is to allow applications stored in my S3 Bucket to have very low latency
- I clicked on the Cloud Front Distribution button
![Screenshot 2024-02-25 234112](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/c4b198a3-62bc-41c6-86e0-54eed4c8ba98)
- I then configured the Distribution page with the following:
![Screenshot 2024-02-25 234235](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/bf282741-06a4-4463-8d22-f9610f642041)
- As the Origin Domain I used the Amazon S3 Bucket I had previously made
![Screenshot 2024-02-25 234620](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/93ff7e24-0ca1-4720-acf4-1a1ed5e38263)
- I made the origin access as the recommended option as this will allow access only from the CloudFront and not publicly from the S3 Bucket. I will show an example
![Screenshot 2024-02-25 235314](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/cc3582fb-7a32-491f-a662-38dbbff71aac)
![Screenshot 2024-02-25 235350](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/ee3000bf-a2f7-451e-b2a3-5693b73bc34d)
![Screenshot 2024-02-25 235427](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/c5be1c99-1579-4cbd-b522-894e0d00953c)
- In the S3 Bucket, I clicked on the index.html file, copied the URL link, and pasted it into a web browser to show that I had no access due to not making the S3 Bucket public
- I next created an Origin Access Control setting by clicking “Create control setting”
![Screenshot 2024-02-26 000002](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/2658f77f-5e21-4e59-b401-0dcfbabffed3)
![Screenshot 2024-02-26 000211](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/8eb6c00e-8d27-4597-b8d7-b2034ea8aaa8)
- I made sure I created a name and the Origin Type was also S3. The rest of the settings can be left as default
- I then created the Control setting
- Due to the name character settings only having a max of 64 characters, I removed my name at the start of the name
![Screenshot 2024-02-26 000522](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/0f524854-d926-4a56-8af9-4e5d1d75add4)
- This is the control setting being created
![Screenshot 2024-02-26 000751](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/4270619e-49fd-4c7f-8aad-d38bbc5c484a)
- For this project, these were the important configurations to adjust
- Everything else I had left as default
![Screenshot 2024-02-26 001108](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/d7aea768-eb3f-411e-a9e6-395ce9e71c7c)
![Screenshot 2024-02-26 001010](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/f5753cf8-2133-48dc-af17-b9df05e9a713)
![Screenshot 2024-02-26 001022](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/262c7157-1b2c-4561-876c-d9be5ba58601)
![Screenshot 2024-02-26 001033](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/e0f51214-04e7-44a6-a584-30c3e46db0a7)
![Screenshot 2024-02-26 001047](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/1d818309-18be-40a6-8082-fb4e3de92bc2)
![Screenshot 2024-02-26 001058](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/938fc060-2943-43e5-b18a-b687c8f65a28)
- As I was happy with the settings configured, I clicked “Create distribution” as shown above
- Below is the outcome of creating the distribution
![Screenshot 2024-02-26 001601](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/1eec9cea-345c-4ec7-915a-4c646277e87a)
- It may take a few minutes for the status to change from Deploying
![Screenshot 2024-02-26 001742](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/2dea81b6-e2da-432f-8a49-aa4f80417a85)
![Screenshot 2024-02-26 001804](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/d26d6bf2-7bf8-4f90-a694-cb3728c1c093)
- Once the Last Modified status changes from “Deploying” to the current date it was last modified, then it has been set
![Screenshot 2024-02-26 002017](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/3904cd9a-84b1-4368-b5fd-7f91ac22b2ab)
- Now I needed to copy the S3 Bucket policy which I needed to attach to the Bucket so Cloudfront could access my AWS S3 Bucket
- To accomplish this I went into my distribution
![Screenshot 2024-02-26 002305](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/b2ba3527-034b-4d77-bb08-361fdb3ce595)
- I then clicked on the origins tab and selected the origin name I had created
![Screenshot 2024-02-26 002438](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/bff3ed57-d1c6-455d-ba6e-9b89625ada6f)
- Once I had selected them, I clicked on the edit button on the right side of the page. This brought out an edit origin page
![Screenshot 2024-02-26 002854](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/7a64c567-d163-4170-bb7b-61558764f5cf)
- I scrolled down on the page till i came across “Bucket Policy”
- I copied the policy and pasted it into my Amazon S3 Bucket
![Screenshot 2024-02-26 003039](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/7ee2adaf-ecc3-4a08-9ec1-0810b2afe06e)
- To paste it into the Bucket, I went into my Amazon S3 Buckets and selected my S3 Bucket
![Screenshot 2024-02-26 003232](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/5dcc4d1d-9ba0-4628-b2e6-a5fbd7f471e1)
- Once I clicked into the s3 bucket, i went to the permissions tab
- Under Permissions there is a section called “Bucket Policy”
- I clicked on the edit button at the “Bucket Policy” section
![Screenshot 2024-02-26 003407](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/48be578c-ed07-4c14-b8b4-b23cb878febc)
![Screenshot 2024-02-26 003610](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/e9503cef-af92-47af-90b6-a49da0877182)
- The edit button brought me to the page where I would paste the Policy I had copied
![Screenshot 2024-02-26 003739](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/fc3ca5d3-60f3-4edb-af1a-d0d18ee31865)
![Screenshot 2024-02-26 003758](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/537d9d51-4b3b-4af1-85c7-17abe90bae91)
- In the Policy it states “SID” : AllowCloudFrontServicePrincipal” which allows CloudFront Service Principal to access my S3 Bucket
- “Effect” is the action that allows the access
- The Principal is “Service”:cloudfront.amazonaws.com”
- The “Action”: “s3:GetObject” is telling it to get the object only on the “Resource”: “arn:aws:s3:::allen-serverless-web-application-on-aws/*”
- The “Condition” is only active when the Cloudfront accesses the “AWS:SourceArn”:"arn:aws:cloudfront::471112764895:distribution/E3UJOYN3GHJ9ND"
- Once they have been pasted, I clicked on “Save Changes”
![Screenshot 2024-02-26 004530](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/d0d52782-e1a1-4cf9-a9fb-2eadd5282127)
![Screenshot 2024-02-26 004506](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/8b0ff8ca-a084-478a-8684-94d1819c1bf3)
- Now I needed to go back to the Distribution page on CloudFront and adjust the settings on the General tab
- I now had to add a domain name and change the Defaul Root Object to - HTML as I had an HTML object in my s3 Bucket
- To do this I clicked the Edit button on the right
![Screenshot 2024-02-26 004825](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/ddd7c958-c3a3-4994-aab8-34515d6fb79e)
- Once in the edit page, I scrolled down to Default root object and changed the name to the index.html file name that I have in my s3 bucket. Everything else was left as Default
![Screenshot 2024-02-26 005922](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/2c71894c-f6fa-4dcd-ad13-6e28b451ed9e)
![Screenshot 2024-02-26 010020](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/ec8da1bc-1de6-4034-b42a-19b166ba8591)
![Screenshot 2024-02-26 010111](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/0fece109-5751-459e-95f3-9b801d7017d6)
![Screenshot 2024-02-26 010122](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/d814cdbd-16cc-4bd5-a0cd-526c72652f23)
- Now the distribution settings have been updated, I have to make sure the status has also been updated from “Deploying” to insure there are no errors
- To check this I clicked on the Distributions tab and refreshed the policy to see if the “Last Modified” status would change
![Screenshot 2024-02-26 010451](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/d493aea3-4fff-44cf-939a-fc8256a5dea7)
![Screenshot 2024-02-26 010513](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/9f5df431-8e28-4b7a-a97e-b68cac2a7226)
- It has successfully been created with no errors

3.  Setup Route 53

- The next procedure was to set up a Route 53 and enable it for the CloudFront Distribution
![Screenshot 2024-02-26 154234](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/f85cda9b-4408-4328-8d0d-3759bcd03107)
- Highlighted in the red circle is where I needed to create my own Domain for me to use
- I had purchased a domain online on “names.co.uk.” and the domain name I created was called “awscloudallen.co.uk”
- Now I will open Route 53 in my aws console to manage the domain as follows:
![Screenshot 2024-02-26 161454](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/ee691cfc-e924-4e74-ae35-246d14ba14e3)
![Screenshot 2024-02-26 161526](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/c048f880-40e2-48f4-adba-da2fa24898bb)
- I then clicked on the option “Create Hosted Zones” as I have a domain already, Hosted Zones tells Route 53 how to respond to DNS queries for a domain such as example.com or in my case “awscloudallen.co.uk
![Screenshot 2024-02-26 162214](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/0084ef6f-cd9b-4b3d-b33c-9361e849d583)
- Once I clicked on Get Started, it presented the configuration page for Hosted Zones
![Screenshot 2024-02-26 162532](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/d6d6000c-f2f1-4b09-94b7-dad10e2ed369)
- The domain name I will input will be the domain name that I purchased which is “awscloudallen.co.uk”
![Screenshot 2024-02-26 163258](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/0ea0912d-5a8a-4017-bc01-df6aa9136e03)
- In the Type, I clicked the Public Hosted Zone as this is my public-facing web application
- Everything else I left as default and clicked Created hosted zone at the bottom right
![Screenshot 2024-02-26 163308](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/b5ee45c2-b82e-4612-bf83-b7349deaf0cc)
![Screenshot 2024-02-26 163543](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/3d1b08d2-eb7c-4972-91cb-02678387dbc9)
- I now needed to copy the name servers/route traffic from the route 53  onto the manage dns page from the domain website which I purchased my domain
![Screenshot 2024-02-26 164100](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/71defe26-bcea-4721-8ad7-5ee722352c89)
![Screenshot 2024-02-26 164226](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/b2a30afa-e487-435c-a4a8-058e0c76f491)
- Here is where I will copy the name servers into each line as follows:
![Screenshot 2024-02-26 165645](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/e9e8a9b9-41f6-4815-acac-2e6f33f9dff0)
- I clicked the update button and allowed the nameserver to take effect between 12-24 hours
- The Next step was for me to go into the CloudFront and edit the settings to change the “Alternate Domain Names”
![Screenshot 2024-02-27 152226](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/f86cda85-74c6-4cec-9a57-75e911470102)
- In the edit page, I clicked on “Add Item” under the “Alternate domain name (CNAME) Section and pasted my domain name with “greeting.awscloudallen.co.uk”
![Screenshot 2024-02-27 152431](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/5096b946-dd3f-426d-b7e2-7ceedb7c8053)
- The purpose of the greeting is because the application is a greeting application
![Screenshot 2024-02-27 152858](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/9f1dd2b6-c6c1-4a7a-aff4-be95e8edb447)
- In the next section, I needed to request a Custom SSL certificate which is recommended as it secures the application
![Screenshot 2024-02-27 153130](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/cb0f0a1c-7953-4c8a-a6d3-152c7b52881c)
- In the next page, I clicked on next as I wanted a public SSL certificate
![Screenshot 2024-02-27 153327](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/ba7b31c0-4624-486e-aae7-55f53a877853)











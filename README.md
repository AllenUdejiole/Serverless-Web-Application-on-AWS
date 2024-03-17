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
- I now pasted my domain name with the “*.” in front of the domain as it stores all the things in the domain
![Screenshot 2024-02-27 153441](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/6cddd69c-9ff6-43fd-b0b2-91fa81fa8a7d)
- Once I made these changes, I left everything else as default and clicked on Request
![Screenshot 2024-02-27 154110](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/9d3e547e-9a33-4d8e-b4d2-8d70328eb70e)
- This is the result of the request
![Screenshot 2024-02-27 154206](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/10eeaa3a-2f9e-4545-aefe-539910cb3fe0)
- After some time I needed to refresh the page for the certificate to appear
![Screenshot 2024-02-27 154358](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/f03fb5e1-baa5-42c1-80d1-56f4a4e70b36)
- I now had to wait for the status to change from pending
- To Change the status from pending I needed to validate the certificate
- To do this I needed to click into the certificate ID and Create records in Route 53
![Screenshot 2024-02-28 141328](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/3cb8d981-7403-45cb-9404-3505f602d097)
![Screenshot 2024-02-28 141635](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/45fb7402-5f2e-4f89-bb38-581949081c7b)
- When I clicked in the Create Records in Route 53 button, It created a Cname in Route 53
- I clicked the “Create Records” button to validate the certificate as follows:
![Screenshot 2024-02-28 141903](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/d0b79adf-6407-4b9c-a944-2b38126e724a)
- Now the DNS records have been successfully created
![Screenshot 2024-02-28 142154](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/c1514b8f-2ccf-4bd4-a12f-f5d12accb6f5)
- Now I had to go to the Route 53 page on the aws console and make sure there was a third entry in the records section
![Screenshot 2024-02-28 142349](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/626878d1-a045-434a-94de-8deeab35edac)
- Now I created a new record for the sub domain which was in the CloudFront distribution settings with the “greeting” followed by the domain name
![Screenshot 2024-02-28 143533](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/d7ac0750-da32-4a23-9160-7f3f641c6896)
- To accomplish this I created a new route 53 record
- I provided the “greeting” in the record name in the next page
![Screenshot 2024-02-28 143807](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/a6d4e7de-8e7d-4488-874a-538cddd4e98f)
![Screenshot 2024-02-28 143849](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/62e691c6-335c-4b1a-9234-cc39cc9ea815)
- After inputting the “greeting”, I changed the alias to enable it followed by routing the trafficking to the Cloud Front Distribution as follows:
![Screenshot 2024-02-28 144313](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/bc56bc61-8f02-43ef-89f7-e721b767b3ef)
- In the choose distribution, No options came up for me and this was due to the certificate not being added
- To change this I needed to refresh the certificate page to make sure it was fully “issued” followed by refreshing the SSL certificate in CloudFront Distribution to get the certificate name in the drop-down
![Screenshot 2024-02-28 144712](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/cfdf55e7-dd02-4704-b9e2-4c6104158bb2)
![Screenshot 2024-02-28 144832](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/16bda490-1bb6-4778-97d6-4b78dceecc31)
- The Purpose of the “*” is a wildcard that is used to allow any subdomain in front of “awscloudallen.co.uk”
- This is sufficient as I can use this certificate again instead of creating a new one
- Once I made these changes, I saved the changes
![Screenshot 2024-02-28 145317](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/33c66b78-4c60-4de8-8cc3-4728aef3bb5c)
![Screenshot 2024-02-28 145351](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/072a4856-d084-4e8c-a601-759d6309c4ec)
- This is sufficient as I can use this certificate again instead of creating a new one
- I now copied the URL with my domain and pasted it into a browser to see if it was fully functioning
- This was the outcome:
![image](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/3ccb0274-12b2-4b5d-9dcb-a6bfb78c0dfa)
![Screenshot 2024-02-29 143334](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/50179365-297c-4d24-a998-de83f48d2ebe)
- This error message was due to an important missed step, which I will show in the next steps
- I needed to go to my Route 53 and complete the Create Record page
![Screenshot 2024-02-29 143642](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/03357e43-c3e2-42de-aaad-0207e3e30c91)
![Screenshot 2024-02-29 143737](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/c0264fdd-d357-4324-aacc-8888421ea3d4)
- The routing will now be created and the records will be created for the “greeting.awscloudallen.co.uk”
- Once again I refreshed the browser page and it presented the content that was in my S3 bucket that was routed to the Cloud Front Distribution as follows:
![Screenshot 2024-02-29 150254](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/84c69c53-1780-4c2a-87f0-505fe1dd3baa)
![Screenshot 2024-02-29 150037](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/a2ce0e82-1075-4bf1-a750-405b025312ac)
- To make the URL secure, infront of the domain I put in “https://” and this secures that URL
![Screenshot 2024-03-01 142647](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/58a78101-fc84-4871-939c-421c38fb5ebb)
![Screenshot 2024-03-01 142656](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/0b6b4854-1906-4a64-afd3-00804042b3b4)
- This is the conclusion of setting up Route 53 and the certificate for the CloudFront Distribution which enables the setup to be functioning

4.  Create Dynamo DB

- The next step was for me to create the Dynamo DB table and map it with Lambda
- For me to create the Dynamo DB table, I first needed to create an IAM role for the Lambda Function to give permissions to access the Dynamo DB
- To create the Dynamo DB I went to the AWS console page and searched Dynamo DB on the search bar
![Screenshot 2024-03-01 143543](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/8f6fbbf2-f377-43f4-92c7-ae2664197e35)
- I then will click on “Create Table” as follows:
![Screenshot 2024-03-01 144121](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/9816f615-edd6-4956-a673-addb1f60a11c)
- In the Create Table page, the only two sections I changed were the Name for the table and the Partition key
- I gave the name “allen-serverless-web-application-on-aws” and the Partition key “id”
![Screenshot 2024-03-01 144346](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/0ca69209-8b5b-4d52-a2a9-e79602b2d42b)
- Once I made these changes, I created the table
![Screenshot 2024-03-01 144611](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/4b93be33-f934-40bc-b038-fff47bcf0a2d)
![Screenshot 2024-03-01 144644](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/0d4069f3-5a4a-4584-aea5-9f6f9d7bd68b)
- It may take some time for the table to be fully created. This will be the outcome of it fully created:
![Screenshot 2024-03-01 144717](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/a8831327-9ebc-4bc0-a8d9-821ada4bbe91)
- I am going to be creating a serverless web application from this static web application
- The Views section on the static web application will be a counter to display the number of times a user has viewed the web application
![Screenshot 2024-03-01 145237](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/4b429c06-0cb5-4a87-a836-d2c73a50af08)
- To accomplish this, I needed to use the Dynamo DB table and the Lambda Function
- My Next step was creating the table
- I clicked on the table name which was fully created
![Screenshot 2024-03-01 144717](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/3924c88b-add9-4d05-bbda-7b49d8b0115a)
- I now clicked on Explore Table Items and it showed that there was no content in the table as it has not been created yet
![Screenshot 2024-03-01 145831](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/50523479-7f1f-4525-b4e0-2bf042d413c3)
- I will now create an item to input
![Screenshot 2024-03-01 145959](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/a4a835f6-8191-4870-bbae-b9c8af411c53)
![Screenshot 2024-03-01 150810](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/152abff9-0112-41b1-98a4-73dfe840a470)
- The “id” will be our partition key and I will set the Value to 0
- In the “Add new attribute” drop-down on the right I will set a new number and label it as Views”. This will represent the views counter on the web application. I will change the value for the “views” to 1 and click “create item” which will create the item as follows:
![Screenshot 2024-03-03 005459](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/9b3cb0c3-7791-4737-8a8b-69f4e66da8a8)
![Screenshot 2024-03-03 005525](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/662f486c-c3b8-413e-b6c1-e4b64630b22f)
- The next step I now proceeded to was to create an IAM Role to give access to the Lambda Function
- I have not created the Lambda Function yet but I am fulfilling the prerequisite by creating the IAM Role
- To do so, I typed in IAM in the search bar on the console page and clicked “IAM” as follows:
![Screenshot 2024-03-03 121558](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/f8b679fd-701f-4ac0-970d-3b5b6905a440)
- I now will go to “Roles” on the far left and click on “Create Role”
![Screenshot 2024-03-03 121800](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/337ad890-b65b-464c-aa57-f616c772645e)
![Screenshot 2024-03-03 121857](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/ed326833-0984-4b37-915a-32ed84b22397)
- Once I create the role, I will now select the entity type as AWS Service and choose Lambda as the service from the dropdown as we are creating a role for Lambda
- Followed by Next
![Screenshot 2024-03-03 122013](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/7bef64a9-95a5-44d6-906c-be9e5306fb61)
- In the Permissions policies, I put DynamoDB and gave it full access as follows:
![Screenshot 2024-03-03 123240](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/8a01d6ba-c9ee-4312-8d32-7f4ea101d046)
- I entered a Role name and followed it by clicking next at the bottom right
![Screenshot 2024-03-03 123415](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/108161db-7f80-41b6-a560-840446087ea6)
![Screenshot 2024-03-03 123520](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/7dc9f639-43c3-43c3-b676-cfa69e44280c)
- I viewed the role to get more details on the role
![Screenshot 2024-03-03 123520](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/baec333c-51c1-4557-92cb-784c1e3c2ad1)
![Screenshot 2024-03-03 123651](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/2771980b-83c3-4430-8574-4cc2c36160b6)
- In the trust relationships, the “sts:AssumeRole” has give access to “lambda.amazonaws.com”(Lambda)
![Screenshot 2024-03-03 123852](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/9c289891-3c34-4527-be83-3abc75a63045)
- Also, Dynamo DB has been given full access
![Screenshot 2024-03-03 124029](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/4b79d70c-deda-4211-a6bd-d3ffd5a44c83)
- This has fully set up the Dynamo DB and the IAM Role that is needed for the Lambda Function
- Next, I will create a Lambda Function by code that will then be integrated with the web application, enabling the “views” counter to be active when the web page is refreshed based on users
- First I will search Lambda in the search bar in the AWS console and open it
![Screenshot 2024-03-04 124641](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/c7ce69bf-9570-412d-8fc8-86b3b27a5497)
- The next page will require me to click on create a function to begin the steps
![Screenshot 2024-03-04 124825](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/1849df12-d8e5-4299-bf3d-8933f481cdee)
- I have set the name as “allen-serverless-web-application-on-aws”
- I also set the “Runtime”(programming language) to python 3.8
![Screenshot 2024-03-04 125042](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/baba1adf-9e42-48aa-ac94-9c38c6e4127f)
- In the advanced settings, I enabled the function URL. This will assign HTTP endpoints to the Lambda Function
- I changed the Auth Type to NONE as Lambda wont perform IAM authentication on requests to the URL Function. This will result in the URL endpoints being public unless I implement my authorization logic in the function
![Screenshot 2024-03-04 125951](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/5dadf37d-3db9-4665-997b-11655902ca5b)
- The last change I made was enabling “Configure cross-origin resource sharing (CORS)”. The purpose is to allow only the website beginning with awscloudallen.co.uk can access the particular Lambda Function
- This will then be followed by the “Create function” as follows:
![Screenshot 2024-03-04 130321](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/03bbf2c6-cc0b-46f8-8714-7ce525bfa997)
- This is the outcome of the created function
![Screenshot 2024-03-12 162140](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/bcd63a1d-9af2-4854-babe-b96943171fe1)
- It gave us a Function URL also which is located at:
![Screenshot 2024-03-04 130424](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/ab03fce7-0320-4842-bbef-e68690ad05a5)
- I will copy the function and paste it into a browser remembering that it was publicly accessible
![Screenshot 2024-03-04 130947](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/f330cfcc-b4bf-4b30-ab46-93184aa0d3ef)
- This “Hello from Lambda” is the default code that was created when creating the function as follows:
![Screenshot 2024-03-04 131038](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/5fa48f19-af79-46d0-8dc8-9b813070a983)
- Now I will remove this code and implement my own code into the editor as follows:
![Screenshot 2024-03-04 132231](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/7e1fac91-6e47-4d99-8ce0-94a2f0b380b8)
- “Import boto3” is needed as its the SDK(Software Development Kit) for interacting with AWS
- I created a variable called “dynamodb” and interacted it with the resource ‘dynamodb’ using boto3
- The table(dynamodb.Table) will be based on the “allen-serverless-web-application-on-aws”
- I created a lambda handler “def lambda_handler(event, context): which is getting the item that I created in the item in dynamo db with the partition being ‘id’:’0’
- The ‘users’ will represent users that use the application and it will be added by 1 for each user “users = users + 1”
- print(users) will print out the users
- response = table.put_item(Item={‘id’:’1’, ‘users’:users}) will update users count as users will increase and the ‘id’ will increase by ‘1’
- This will be followed by returning the ‘users’ at the end
- I will deploy the code to see if there are any errors
![Screenshot 2024-03-04 133745](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/f2da568b-7a8f-4fff-9868-240fea54da39)
- I had to change the “users” to views” as views is the counter associated on the web application
![Screenshot 2024-03-04 133842](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/d3c0420f-9564-4103-bf70-036cf353910c)
- After deploying and testing the code, I got an error
![Screenshot 2024-03-04 134702](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/5e867208-aeb1-46ad-a489-689f6de4f2d5)
- This is due to creating the IAM role previously and not attaching the IAM role to this Lambda Function
- In the Lambda function page I can adjust this by clicking on Configuration - Permissions on the left and click edit as follows:
![Screenshot 2024-03-04 134931](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/9b659cae-ef87-44b5-9fb8-d2ec4bb72eea)
![Screenshot 2024-03-04 135005](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/28667ff3-e56f-4b68-8ef3-fd67c017653f)
- At the bottom I changed the existing role to the “allen-serverless-web-application-on-aws” and clicked save
![Screenshot 2024-03-04 135106](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/044b0a78-efe9-481f-b8af-28121cdaa16a)
![Screenshot 2024-03-04 135215](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/9db0fd79-024a-418a-a2b9-b0bd9e582178)
- Now I will execute the Lambda Function again
![Screenshot 2024-03-04 135306](https://github.com/AllenUdejiole/Hosting-Static-Website-on-EC2-instance-Linux-/assets/160611100/0556bdd7-32c8-4915-a6ef-511b37ca6363)
- It has been successful as it gave a response of 2. Previously in the Dynamo DB table, it had 1 view but now it will have another item with 2 as views based on the Lambda















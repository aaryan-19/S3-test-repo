# S3-test-repo
## About the Project

In this, I have created a simple Tic-Tae-Toe game with HTML, CSS and Javascript and hosted the project on AWS S3.
## What is AWS S3?
AWS S3 (Amazon Simple Storage Service) is a cloud storage service provided by Amazon Web Services (AWS). It is designed to store and retrieve any amount of data from anywhere on the web. S3 offers highly scalable, durable, and secure storage for a wide range of use cases, including backup and restore, data archiving, content distribution, and application data storage.


### Steps to run this project host a static website on S3
1. Go to **S3** service in AWS management console after logging into your account.
2. In the **buckets** list, select the bucket that you have created.
3. Choose **Properties**. Go to **Static website hosting** and choose **Enable**.
    
    * In index document, give name of the file. In our case - **index.html**
    * (Optional) In error document, give the name of the file which should be returned when there's an error. In our case - **404.html**.
    * Click on **Save changes**.
4. Now Open the Bucket and go to **Permissions**
    
    * Under **Block Public Access**, choose Edit and clear **Block All public access** and Save the changes.
5. Add the Following code to the **Buckets Policy** under **Permissions**.

    `{

    "Version": "2012-10-17",

    "Statement": [

        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::<bucket-name>/*"
            ]
        }
    ]
}`

`Note - Change the Bucket name according to your bucket`

6. Save the changes.
Now go to your bucket and click on **Upload** and upload all the files in this repository.
7. Now test your website endpoint by going to the **Properties**:
    
    * Go to bottom of page under **Static website hosting** and choose  your **Bucket Website endpoint**.
8. Your index document will now run in a separate browser window.

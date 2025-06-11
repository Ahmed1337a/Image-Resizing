# Automated Image Resizing and Transfer System Using AWS Services
## Scenario :
This project focuses on building an automated system for image processing .The goal is to streamline the handling of images by automatically resizing them and transferring them to a destination storage location . Key AWS services, such as Lambda, S3, and SNS, are used to orchestrate this workflow.
![image](https://github.com/Ahmed1337a/Image-Resizing/blob/d22d8f84f8b5b6227952d6a918f3f5c7f8214fe9/Images/diagram-export-6-11-2025-9_06_20-PM.png)

## Steps :
### Step 1 :
### Creating Source and Designation s3 Buckets :
 Navigate to the S3 Console.
     
![image](https://github.com/Ahmed1337a/Image-Resizing/blob/0cebf31b44c1bb75aeed41b028f6159173f7467d/Images/1.png)
     
     
 ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/0cebf31b44c1bb75aeed41b028f6159173f7467d/Images/2.png)
     
     
  ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/0cebf31b44c1bb75aeed41b028f6159173f7467d/Images/3.png)
     
     
### Step 2 :
### Creating the SNS Notification :

 Navigate to the SNS console.
    
![image](https://github.com/Ahmed1337a/Image-Resizing/blob/0cebf31b44c1bb75aeed41b028f6159173f7467d/Images/11.png)

         
 ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/0cebf31b44c1bb75aeed41b028f6159173f7467d/Images/12.png)
 
 Scroll down and Click "Create subscription
 After this , you will receive some mail for Subscription Confirmation and you have to confirm that

         
 ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/0cebf31b44c1bb75aeed41b028f6159173f7467d/Images/13.png)
 
 
 ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/0cebf31b44c1bb75aeed41b028f6159173f7467d/Images/14.png)

### Step 3 :
### Creating IAM ROle :

Navigate to the IAM Console.

Create a policie and attach S3 ,SnS full access and make a role contain that policy 

 ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/ab82f8fc35c323e8fa4fc82671dbf87d66d44cd7/Images/18.png)

 
  ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/ab82f8fc35c323e8fa4fc82671dbf87d66d44cd7/Images/4.png)


 ### Step 4 :
### Creating Lambda :

Navigate to the Lambda Console.

 ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/ab82f8fc35c323e8fa4fc82671dbf87d66d44cd7/Images/5.png)
 
Use exsisting IAM Role

 
 ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/ab82f8fc35c323e8fa4fc82671dbf87d66d44cd7/Images/6.png)
 Make Resource S3 as a Trigger

 
 ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/ab82f8fc35c323e8fa4fc82671dbf87d66d44cd7/Images/7.png)

 
  ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/ab82f8fc35c323e8fa4fc82671dbf87d66d44cd7/Images/8.png)

  Now we have to go to code section , and scroll down to layers

  why we add a layer ?
  We need a python library called pillow in our code to resize the image . We can manually add Pillow library also, But it's very time consuming and you have to do lot more , Instead of manually adding pillow library we are going to use layers for Some easy action.

  you can copy the arn from below.
  
         arn:aws:lambda:ap-south-1:770693421928:layer:Klayers-p39-pillow:1



   ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/ab82f8fc35c323e8fa4fc82671dbf87d66d44cd7/Images/10.png)

   Now you can replace a code 

   ### Step 5:
### Upload Image to Resource S3 :

   ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/ab82f8fc35c323e8fa4fc82671dbf87d66d44cd7/Images/9.png)

   
   ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/361924b3d1d75b382a4f2b48ef92e03b011a3c14/Images/15.png)

   Now we can see the image is succefully resized in destination S3
   
   ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/361924b3d1d75b382a4f2b48ef92e03b011a3c14/Images/16.png)
   

   
   ![image](https://github.com/Ahmed1337a/Image-Resizing/blob/361924b3d1d75b382a4f2b48ef92e03b011a3c14/Images/17.png)

   ### It Successfully resized the Image and sends me the Notification.


   







 



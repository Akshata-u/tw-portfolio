!!! example "About this article "
    Reference links to other articles are indicated but unavailable since these are sample documents.

This article describes items that need to be set up by the customer before proceeding with other Snowflake- AWS S3 actions in Zumo AI.

## Step 1: Creating an IAM policy

* Log into the AWS Management Console.
* In the **Home dashboard**, search for and select **IAM**.
* From the left-hand navigation pane, select **Account settings**.
* Under **Security Token Service (STS)**, in the **Endpoints** list, find the _Snowflake region - US West (N. California)_. If the **STS status** is inactive, slide the toggle to **Active**.
* From the left-hand navigation pane, click **Policies**.
* Select **Create Policy**.
* For **Policy editor**, select **JSON**.
* Add a policy document that will allow Snowflake to access the S3 bucket and folder.  
      
The following policy (in JSON format) provides Snowflake with the required permissions to load data using a single bucket and folder path.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "VisualEditor0",
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::<your-bucket-name>"
    },
    {
      "Sid": "VisualEditor1",
      "Effect": "Allow",
      "Action": [
        "s3:PutObject",
        "s3:GetObject"
      ],
      "Resource": "arn:aws:s3:::<your-bucket-name>/*"
    }
  ]
}
```

* Click **Next**.
* Enter a **Policy name**, for example, _snowflake\_access_ and optionally, a **Description**.
* Click **Create policy**.

## Step 2: Create the IAM Role in AWS

To configure access permissions for Snowflake in the AWS Management Console, do the following:

* From the left-hand navigation pane in the **Identity and Access Management (IAM)** dashboard, click **Roles**.
* Select **Create role**.
* Select **AWS account** as the trusted entity type.
* In the **Account ID** field, enter your own AWS account ID temporarily. In later steps, you will modify the trust relationship and grant access to Snowflake.
* Select the **Require external ID** option. An external ID is used to grant access to your AWS resources (such as S3 buckets) to a third party such as Snowflake.     
Enter a placeholder ID such as _0000_. In later steps, you will modify the trust relationship for your IAM role and specify the external ID for your storage integration. Click **Next**. 

* Select the policy you created in **[Step 1](#step-1-creating-an-iam-policy)**.    
  Click **Next**.
* Enter a name and description for the role, then click **Create role**.

You have now created an IAM policy for a bucket, created an IAM role, and attached the policy to the role.

On the **Role summary** page, locate and record the **Role ARN** value.

!!! note "Note"
    Once the above steps are complete, share the **Role ARN** value and **bucket name** with Zumo AI.
    
    The support team will get back to you with two more details: **STORAGE\_AWS\_IAM\_USER\_ARN** and **STORAGE\_AWS\_EXTERNAL\_ID**. 
    
    Once you have received these values, proceed to complete the actions described in **Step 3** below.

## Step 3: Allowing the Zumo IAM User to assume the role

The following step-by-step instructions describe how to configure IAM access permissions for Snowflake in your AWS Management Console.

* Log in to the AWS Management Console and click **IAM**.
* From the left-hand navigation pane, click **Roles**.
* Select the role you created in **[Step 2](#step-2-create-the-iam-role-in-aws)**.
* Open the **Trust relationships** tab.
* Click **Edit trust policy**.
* Modify the policy document with the 2 values given to you by Zumo AI i.e., **STORAGE\_AWS\_IAM\_USER\_ARN** and **STORAGE\_AWS\_EXTERNAL\_ID** where,
    * **snowflake\_user\_arn** is the **STORAGE\_AWS\_IAM\_USER\_ARN** value Zumo AI shared with you.
    * **snowflake\_external\_id** is the **STORAGE\_AWS\_EXTERNAL\_ID** value Zumo AI shared with you.
    
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "",
      "Effect": "Allow",
      "Principal": {
        "AWS": "<snowflake_user_arn>"
      },
      "Action": "sts:AssumeRole",
      "Condition": {
        "StringEquals": {
          "sts:ExternalId": "<snowflake_external_id>"
        }
      }
    }
  ]
}
```

Upon receiving your confirmation, we will proceed with configuring the exports on our end. If you have any questions or encounter any issues, please reach out to your **Zumo AI** Account Executive/ Point of Contact.
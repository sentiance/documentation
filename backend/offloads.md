---
description: >-
  Sentiance provides data offloads with produced lifestyle and driver profile
  data to the clients on a daily or weekly basis, depending on the preference of
  the client.
---

# Offloads

## What are offloads

The Sentiance platform provides multiple ways to access and analyse your end-users data. The offloads are our take on a _(csv)_ file based system. Offloads will usually contain all data for all of your users for a specific timeframe _(By default this will be a 9 week sliding window.)_ More detailed descriptions of the fields and data are available [below](offloads.md#Offloads-Drivingoffloads-5).

The offloads are accessible to you via the **Amazon S3 storage service** on the Sentiance Platform.&#x20;

There are three main types of offloads: lifestyle, driving, and mapping. Click below for more info.

* **Lifestyle // Batch offloads**
  * Contain events, moments & segments. Are usually offloaded on a weekly basis.
* **Driving // Realtime offloads**&#x20;
  * Contain low level driving behaviour. Are usually offloaded on a daily basis.
* **Mapping // User linking offloads**&#x20;
  * Contain information for mapping our internal identifiers to client specific identifiers.

{% hint style="danger" %}
Note that while offloads will contain **most** of the core data we compute, it does not contain data such as predictions, coaching data, some fine grained fields, and so on.&#x20;

_Please consult with your Sentiance contact person to discuss the offloads before implementing._
{% endhint %}

## Connecting to the offloads (Amazon S3)

{% hint style="warning" %}
If you do not wish to setup an automated system (yet) please see **browsing the offloads.**
{% endhint %}

### 1) You already have an AWS account or are willing to create one

{% hint style="success" %}
This will allow you more fine grained control over your credentials and access methods.
{% endhint %}

{% hint style="info" %}
**Beginning March 2021, Amazon S3 (AWS)** is moving to its own certificate authority. This may require you to update your operating system or browser. Read more about who is affected and which steps to take [here](https://aws.amazon.com/blogs/security/how-to-prepare-for-aws-move-to-its-own-certificate-authority/).
{% endhint %}

We will give permission to your AWS account to create IAM users that can access Sentiance’s offload bucket.

As a prerequisite, share your AWS Account number with the Sentiance team to setup the required permissions. The easiest way to find your account number is to log in to the AWS console and open the ‘Support Center’. The account number is at the top of the page. (This number might start with 0, make sure to copy the full number.)

If you don’t have an AWS Account, please create one. You need a mobile phone number and credit card to register an account, see “[Create and Activate a new Amazon Web Services account](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/)”.

**Offloads will be generated in your client-specific root folder (e.g. s3://sentiance-u1-offloads/client-name).** The name of the root folder will be provided by Sentiance. You might get different root folders for different appIds (e.g. development, staging, production). Contact the team to check your configuration.&#x20;

Once Sentiance has set the permissions, [create an IAM user](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_users\_create.html) that can access the resources. You need the client-specific root folder to configure the access rules, see placeholder \{{offload\_client\_root\_directory\}} in the example below. An example of IAM user permissions:

```javascript
{
 "Version": "2012-10-17",
 "Statement": [
   {
     "Sid": "AllowListingOnDesiredBucket",
     "Action": [
       "s3:ListBucket"
     ],
     "Effect": "Allow",
     "Resource": [
       "arn:aws:s3:::sentiance-u1-offloads"
     ],
     "Condition": {
       "StringEquals": {
         "s3:prefix": ["{{offload_client_root_directory}}"],
         "s3:delimiter": ["/"]
       }
     }
   },
   {
     "Sid": "AllowListingOfOwnFolder",
     "Action": [
       "s3:ListBucket"
     ],
     "Effect": "Allow",
     "Resource": [
       "arn:aws:s3:::sentiance-u1-offloads"
     ],
     "Condition": {
       "StringLike": {
         "s3:prefix": [
           "{{offload_client_root_directory}}/*"
         ]
       }
     }
   },
   {
     "Sid": "AllowReadS3ActionsInOwnFolder",
     "Action": [
       "s3:Get*",
       "s3:List*"
     ],
     "Effect": "Allow",
     "Resource": [
       "arn:aws:s3:::sentiance-u1-offloads/{{offload_client_root_directory}}/*"
     ]
   }
 ]
}

```

If you configured the user to have AWS Management Console access, then you should be able to login with this user and see the offloads in our bucket using the AWS Console. Either way, you can now generate [access keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/id\_credentials\_access-keys.html) for the user to get programmatic access to the bucket. You can use e.g. [CyberDuck](https://cyberduck.io/) or [Forklift](https://binarynights.com/) to test the keys.

#### **Recommendations**

A couple of recommendations regarding AWS access keys:

* Treat your keys as you treat passwords and other secret information.&#x20;
  * Do not share the keys with anyone
  * Do not submit them to a version control system
  * Do not store them as plain text
* Rotate the keys regularly. By rotating the keys, you minimize the impact if a key gets compromised.&#x20;
  * If possible automate the rotation process (e.g. by using secrets-as-a-service, see [KMS](https://aws.amazon.com/kms/), [Vault](https://www.vaultproject.io/)...)
  * Disable keys if you don’t need them anymore
* Limit the permissions of the IAM user as much as possible. The less a user is allowed to do, the less can happen when keys get compromised.&#x20;

### 2) You do not have an AWS account

{% hint style="danger" %}
Credentials are controlled and distributed by Sentiance
{% endhint %}

{% hint style="info" %}
Your credentials will be sent to you via your client services contact or Sentiance support on your request.
{% endhint %}

A separate prefix has been set up for you on the Sentiance Amazon S3 account under the sentiance.offloads-bucket.&#x20;

The recommended way to retrieve your offloads is through the awscli-command line tool&#x20;

After installation, first configure your account (credentials sent separately, see above):&#x20;

`$ aws configure`&#x20;

And provide your credentials when asked for: `$ AWS Access Key ID [None]: <your personal access key>`&#x20;

`$ AWS Secret Access Key [None]: <your personal secret>`&#x20;

`$ Default region name [None]: eu-west-1`

`$ Default output format [None]: <leave empty>`&#x20;

Then you can use the tool to list and download the data, the example assumes a prefix named sample, adjust this to your own provided prefix to access your offloads:&#x20;

`$ aws s3 ls s3://sentiance.offloads/sample/`

## Browsing the offloads

While there's plenty of tools available to browse the offloads via the command line, we recommend [https://cyberduck.io/s3/](https://cyberduck.io/s3/) as a tool for non developers to interact with the offloads.

## What are offloads continued

### **Lifestyle // Batch offloads**

Generated and delivered to you on a _daily or weekly basis_

Lifestyle offloads are based on the Sentiance data pyramid. They contain a file per layer of data we compute and 2 for the events layer. **See** [**library**](../library/events.md) **&**  [**data model**](offloads.md#data-model) **for more**.

Each offload consists of single folder containing multi-part, gzipped csv files.&#x20;

Multi-part offloads will start showing up once the userbase being tracked reaches into the thousands of users.&#x20;

Every csv file in the lifestyle offloads uses a comma ‘,’ as a field separator and every part contains the header with column names.&#x20;

The complete data model for every file is described in the spreadsheet named ‘Sentiance - Offloads - Data Model - **XXXX**.xlsx’ accompanying this document.&#x20;

{% file src="../.gitbook/assets/Sentiance - Offloads - Data Model - 0.1.2 - 201801122.xlsx" %}

{% file src="../.gitbook/assets/Sentiance - Anonymized offload samples - 20190114.zip" %}

#### **Stationaries**&#x20;

Stationaries represent the period of time a user was detected to be at a specific venue. Every row represents a single Stationary of a user. Multi-part file inside the stationaries.\<appid>.csv folder.&#x20;

**Transports**&#x20;

Transports represent the period of time a user moved from one venue to another. Multiple transports might occur without intermittent stationaries, e.g. a user first walking to his car, then driving to a restaurant. Every row represents a single Transport of a user. Multi-part file inside the transports.\<appid>.csv folder.&#x20;

**Moments**&#x20;

Moments represent a period of time when the user was within a certain context, e.g. commuting, in shopping routine. Every row represents a single Moment of a user. Multi-part file inside the moments.\<appid>.csv folder.&#x20;

**Attributes - Wide**

Attributes represent a particular long-term attribute of the user, e.g. commute time, distance walked, shop visits. The wide attributes offloads contains a separate row per user with every column containing another attribute for that user. Multi-part file inside the attributes.wide.\<appid>.csv folder.&#x20;

**Attributes - Long**

The long attributes offloads contains a separate row per attribute per user. Multi-part file inside the attributes.long.\<appid>.csv folder.

**Segments**&#x20;

Segments represent a particular long-term characteristic of the user, e.g. long commuter, dog walker, brand loyalty. Every row represents a single Segment of a user. Multi-part file inside the segments.\<appid>.csv folder.

{% hint style="warning" %}
**Lifestyle // Batch offloads** will only contain data for users who have been active in the last 7 days. Our definition of an active user is based on the criteria that the user has sent at least one of the following payloads in this period:\
`- Trip event`\
`- Trip`\
`- Stationary event`
{% endhint %}

### **Driving // Realtime offloads**

Our daily realtime transport offloads contains all the transports that were processed by our backend system during the previous day. We currently consider a day between midnight UTC. The files can be in either a json or csv format.

E.g. the offload of May 7th will contain all the transports that were processed between 2019-05-06T00:00+00:00 and 2019-05-07T00:00+00:00.\


If the local timezone is ahead of UTC, transports of the local current day might be offloaded because compared to UTC, they are still in the previous day. E.g. for the offload of May 7th, a transport started at 2019-05-07T06:00+08:00 might be included if it was sent to our backend in time. Expressed in UTC, this transport was made at 2019-05-06T22:00+00:00.\


We're always using the processing time of the transport to include it in the offload file. Processing time is the time the transport arrives at Sentiance plus the actual processing of the sensor data. If a user is not connected to the network and a transport is only sent the next day it will be included in the day after it was sent. So as a developer, you should be aware of transports that arrive late.\


We guarantee that everything processed the previous day will be in the offload. There might be some transports of the current day already included in the offload of the previous day, those will not be repeated in the next offload.\


The data model for each driving offload type is available below. The document includes descriptions about offload types, document structures, and fields present.

{% file src="../.gitbook/assets/Sentiance - Driving offloads data model.md" %}


A zipped archive containing a sample of each type of driving offloads file is also available below. The four driving offloads files found in the archive are:

* `driving_events_realtime.json`
* `mapped_waypoints_realtime.json`
* `scores_realtime.csv`
* `transports_realtime.csv`

{% file src="../.gitbook/assets/Sentiance - Anonymized driving offload samples - 20220727.zip" %}

****

### **Mapping // User linking offloads**

Generated on a daily basis. These are necessary for the [user linking ](../sdk/appendix/user-linking.md)functionality.

Sentiance allows clients to make a link between their internal ID, referred to as external\_id, to the Sentiance internal ID (user\_id). This type of offloads is disabled by default.

Upon enabling them for a particular app\_id, the client receive**s** a single file containing two columns: user\_id and external\_id on a daily basis.

{% hint style="success" %}
The **Mapping // User linking offloads** are stored on Amazon S3 in the same bucket as your other offloads.
{% endhint %}

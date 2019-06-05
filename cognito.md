## Cognito (Web Identity Federation)

### Overview

**Web Identity Federation**<br>
Web Identity Federation lets you give users access to AWS resources after they have successfully authenticated with a web-based identity provider like Amazon, Facebook, or Google. Following successful authentication, the user receives an authentication code from the Web ID provider, which they can trade for temporary AWS security credentials.

**Cognito**<br>
Amazon's web identity federation solution which allows:

- Sign-up and sign-in to your apps
- Access for guest users
- Acts as an Identity Broker between your application and Web ID providers, so you don't need to write any additional code
- Synchronizes user data for multiple devices
- Recommended for all mobile application AWS services

Cognito brokers between the app and Facebook or Google to provide temporary credentials which map to an IAM role allowing access to the required resources. No need for the application to embed or store AWS crednetials locally on the device, and it gives users a seamless experience across all mobile devices.

#### User Pools and Identity Pools
**User Pools**<br>
User pools are user directories used to manage sign-up and sign-in functionality for mobile and web applications. Users can sign-in directly to the User Pool, or using Facebook, Amazon, or Google. Cognito acts as an Identity Broker between the identity provider and AWS. Successful authentication generates a JSON Web token (JWT).

**Identity Pools**<br>
Identity Pools provide temporary AWS credentials to access AWS services like S3 or DynamoDB.

#### Cognito Synchronization
Cognito tracks the association between user identity and the various different devices they sign-in from. In order to provide a seamless user experience for your application, Cognito uses Push Synchronization to push updates and synchronize user data across multiple devices. Cognito uses SNS to send a notification to all devices associated with a given user identity whenever data stored in the cloud changes.

### Key Take Aways
- Cognito is a service for Web Identity Federation
- Cognito allows users to authenticate with a Web Identity Provider (Google, Facebook, Amazon)
- The user authenticates first with the Web Identity Provider and receives an authentication token, which is exchanged for temporary AWS credentials allowing them to assume an IAM role.
- Cognito is an Identity Broker which handles the interaction between your applications and the Web Identity Provider. *You do not need to write your own code to do this*
-  Understand the difference between a user pool and identity pool.
    - **User Pool** is user based. It handles things like user registration, authentication, and account recovery
    - **Identity pools** authorize access to your AWS resources

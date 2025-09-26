# Identity and Access Management (IAM)
## Theory : 
- Administrators can apply policies that define who can do what on which resources.

- It is a way of identifying who can do what on which resource. The who can be a person, group or application. The what refers to specific privileges or actions and the resource could be any Google Cloud service.

<div align="center">
  <strong>IAM OBJECTS</strong>
  </br>
<img width="600" src="https://user-images.githubusercontent.com/59575502/194280610-00a5ce05-7672-454b-8877-5d4d1530e0ab.png">

</div>

#### Organization
**Organization roles:** ```organization admin``` (control over all resource), ```project creator``` (controls project creation and who can create it).
##### Resource manager roles
- **Organization**
    - Admin (full control over resource)
    - Viewer (view access to all resource)
- **Folder**
    - Admin (full control over folders)
    - Creator (browse hierarchy and create folders)
    - Viewer (view folders and projects)
- **Project**
    - Creator (create or migrate projects)
    - Deleter (delete projects)

### Roles
An IAM role is a collection of permissions.
There are three types of roles in Cloud IAM: 
- ```Basic roles``` (apply across all services in a project) ```owner``` ```editor``` ```viewer``` ```billing admin```
- ```Predefined roles``` (apply to a specific resource in a project) ```InstanceAdminRole``` -> ```compute.instance.(get,list,delete,start,stop,setMachineType)``` list of permission bundled together.
- ```Custom roles``` (lets you define which permission to add) Not update automatically when google updates something...

### Members
which define the who part of who can do what on which resource. There are five different types of members, Google accounts, service accounts, Google Groups, Google Workspace domains, and Cloud Identity domains. 

<img width="1200" src="https://user-images.githubusercontent.com/59575502/194287087-c5b0c858-2693-4696-b11a-208e8d84d358.png">

#### Service accounts
What if you want to give permissions to a Compute Engine virtual machine, rather than to a person?
- It's a ```resource``` so you can add it to IAM.
- Service accounts are named with an email address
- Instead of passwords they use cryptographic keys to access resources.

A service account is an account that belongs to your application instead of an individual end user. When you run code that is hosted in Google Cloud, you specify an account that that code should run as.

#### Google groups
A Google Group is a named collection of Google accounts and service accounts. Every group has a unique e-mail address that is associated with that group. Google Groups are a convenient way to apply an access policy to a collection of users.

#### Google Workspace domains
A Workspace domain represents a virtual group of all the Google accounts that have been created in an organization's workspace account. Workspace domains represent your organization's Internet domain name, such as Example.com. And when you add a user to your Workspace domain, a new Google account is created for the user inside of this virtual group, such as username@example.com.

#### Cloud Identity
- Cloud Identity lets you manage users and groups using Google Admin console.
- Give users easy access to apps with single sign-on
- Multi-factor authentication protects user and company data
- Usage of Active Directory or LDAP ( If anyone joins/leaves the org )

### IAM Policy
- A policy contains a ```list of bindings```.
- A binding binds a ```list of members to a role```.
- where the members can be ```user accounts, Google Groups, Google Domains, and service accounts```. 

#### Cloud Directory Sync
What if you already have a different corporate directory? How can you get your users and groups into Google Cloud? Using Google Cloud Directory Sync, your administrators can log in and manage Google Cloud resources using the same username and passwords that they already use. This tool synchronizes users and groups from your existing active directory or LDAP system with users and groups in your Cloud Identity domain. The synchronization is one-way only, which means that no information in your active directory or LDAP map is modified.

### Service Accounts
- A service account is an account that belongs to your ```application``` instead of to an individual end user.
- Provides an identity for carrying out ```server-to-server``` interactions in a project **without** supplying user credentials.

**Example:** ```service-account-name@project-id.iam.gserviceaccount.com``` </br>
By default, all projects come with a built-in Compute Engine default service account. Apart from the default service account, all projects come with a Google Cloud APIs service account, identifiable by the email project-number@cloudservices.gserviceaccount.com. This is an account designed specifically to run internal Google processes on your behalf and is automatically granted the ```Editor``` role on the project. 

</br>

**There are three types of service accounts:**
- user-created or custom
- built-in (Compute Engine and App Engine service account)
- Google APIs service accounts (Runs internal google processes on your behalf)


![image](https://user-images.githubusercontent.com/59575502/194293393-42af1e9a-0fe6-4ce5-87ee-0f0ff2bc3f4c.png)

![image (1)](https://user-images.githubusercontent.com/59575502/194294029-30a67e67-a5be-48bf-8f37-26cdb969e576.png)

## Practice : 
### Using gcloud

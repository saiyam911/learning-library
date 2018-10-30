![](../common/images/customer.logo.png)
---
# Deploy a Sample Shopping Cart application on Java Cloud Service instance using user interface on Oracle Cloud Infrastructure (JCS on OCI) #

## Steps Involved ##
1. Download artifacts.zip file from git repository
2. Collect Database and Java Instance IP Address, Update properties file
3. Copy scripts & Load Database with application data
4. Copy artifacts & Create application pre-requisites on JCS instance
5. Deploy sample application on JCS instance
6. Test the deployment
---
### Dowload Artifacts ###
- Download artifacts.zip from this github location 
- Unzip the artifacts.zip and keep the files handy
- The artifacts.zip will contain a deployable .war file and a folder called "setup" which has key scripts needed to setup the database and create necessary pre-requisites on JCS insance to deploy the application
---
### Prepare for running scripts needed to setup Data on DBCS instance & DataSource on JCS instance ###

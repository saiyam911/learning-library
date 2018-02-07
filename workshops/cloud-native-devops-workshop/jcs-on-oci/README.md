![](../common/images/customer.logo.png)
---
# ORACLE Cloud-Native DevOps workshop #

## Create Java Cloud Service instance using user interface on Oracle Cloud Infractructure (JCS on OCI) ##

### Introduction ###

The Oracle Java Cloud Service (JCS) provides a cloud-based application server (Oracle WebLogic Server with automated customer-controlled provisioning, backup, patching, scaling with cloud tooling) designed to support any Java application. You may use the Oracle Java Cloud Service through the Oracle Java Cloud Service console and quickly create and configure Java EE application environment.

The Oracle Cloud Infrastructure (OCI) platform can run both Oracle workloads and cloud native applications, it offer highly available infrastructure ideal for enterprise applications and provide greater control over the network. This all adds up to great price-performance for Weblogic deployment.

### About this tutorial ###
This tutorial demonstrates how to:
	
+ Create Java Cloud Service based on OCI using the user interface.

### Prerequisites ###

+ Cloud Account with Oracle PaaS and IaaS Universal Credit subscription (includes an IDCS integrated OCI-Classic account and an OCI Account)
+ Oracle Java Cloud Service uses Oracle Database Cloud Service to host the Oracle Fusion Middleware component schemas required by Oracle Java Required Files (JRF).

### Steps ###

There are three major steps in order to setup JCS on OCI:
1. Perform pre-requisites for provisioning PaaS services on OCI
2. Provision DBCS service in OCI using PSM
3. Provision JCS service in OCI using PSM

#### 1. pre-requisites for provisioning PaaS services on OCI ####


[Sign in??](../common/sign.in.to.oracle.cloud.md) to [https://cloud.oracle.com/en_US/sign-in](https://cloud.oracle.com/en_US/sign-in). 

Where I am now after sign in, on OCI Classic??
The OCI-Classic console also has OCI services provisioned. Clicking on an OCI services redirects to OCI Console of Home region (Phoenix/Ashburn/Frankfurt).

Picture PREREQ.1

Go to Compute, click the hamburger icon, Open Service Console and log in to OCI console. Depends on how your account is set up you can use SSO or OCI account to log in. 

Picture PRERQ.2

For PaaS provisioning, the OCI tenancy has an additional compartment and two policies provisioned by default. Compartment name is ManagedCompartmenForPAAS. One policy (PSM-mgd-comp-policy) is under  ManagedCompartmenForPAAS compartment. ??
And second policy (PSM-root-policy)  is under root compartment ??

Picture PREREQ.3 OCI console .149

1. Create a Compartment
You can select an existing compartment to create the Oracle Cloud Infrastructure resources required for Java Cloud Service. But for this tutorial, we'll use a new compartment.??

Click **Identity**, and then click **Compartments**.
Enter a name and description for the new compartment, and click **Create Compartment**.

PREREQ..4

2. Create a Virtual Cloud Network
In the Oracle Cloud Infrastructure web console, click **Networking** and then **Virtual Cloud Networks**.
Click **Create Virtual Cloud Network**.
Select the compartment !!important that you created earlier, enter a name for the Virtual Cloud Network, and let the service create a Virtual Cloud Network and related resources.


PREREQ.5


Scroll down, and click **Create Virtual Cloud Network**.


PREREQ.6

The service creates a Virtual Cloud Network with the CIDR 10.0.0.0/16 and one subnet per AD.
Important: Note the name of the subnet you want to use for the Java Cloud Service instance.
Click **Create Virtual Cloud Network**.


3. Permit Platform Services to Use the Virtual Cloud Network You Created

In the Oracle Cloud Infrastructure web console, click Identity and then Policies.
Select the root compartment for your tenancy.
Click Create Policy.
Enter a name and description for the policy.
In the Policy Versioning field, select Keep Policy Current to keep it current with any future changes to the definitions of policy verbs and resources. To limit access according to the definitions that were current on a specific date, select Use Version Date and enter that date in the YYYY-MM-DD format. 
Add the following policy statements, one at a time.

Remember to replace <compartment_name> with the name of the compartment you created earlier.

Allow service PSM to inspect vcns in compartment <compartment_name>
Allow service PSM to use subnets in compartment <compartment_name>
Allow service PSM to use vnics in compartment <compartment_name>
Allow service PSM to manage security-lists in compartment <compartment_name>

OCI.7

Click Create.

4. Create an Object Storage Bucket
In the Oracle Cloud Infrastructure web console, click Storage and then Object Storage.
In the navigation pane on the left, select the compartment that you created earlier.
Click Create Bucket.
Enter a name for the bucket, and click Create Bucket. (Important: Note this name. You'll need it later while creating the Java Cloud Service instance.)

OCI.8

5. Generate a Swift password
In the Oracle Cloud Infrastructure web console, click your user name near the upper-right corner and click User Settings.
In the navigation pane on the left, click Swift Passwords.
Click Generate Password.
Enter a description for the password, and click Generate Password.

OCI.9

Important: Copy and store the generated password. You'll need it later while creating the Java Cloud Service instance.











.-.-.-.-.-.-..--.
On the dashboard click the hamburger icon on the Java tile. Select **Open Service Console**.

![](images/01.png)

This is the Java Cloud Service Console page. If this is the first time opening Java console then Welcome page will appear. In this case click **Go to Console** button.

![](images/02.png)

To create new instance click **Create Service** button.

![](images/03.png)

Select subscription type. Select the fully managed Oracle Java Cloud Service and the desired billing format. For more details about subscription types see the [documentation](https://docs.oracle.com/cloud/latest/jcs_gs/JSCUG/GUID-31F00F2C-221F-4069-8E8A-EE48BFEC53A2.htm#JSCUG-GUID-98DD6CE1-480F-4AA9-8131-A1D3D274440F).
![](images/create.jcs.03.png)

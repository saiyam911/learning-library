### New Developer Cloud Service Setup ###

Oracle Developer Cloud Service now supports integration with Oracle Cloud Infrastructure Compute Classic and Oracle Cloud Infrastructure Object Storage Classic.

You can create virtual machines (VMs) on Oracle Cloud Infrastructure Compute Classic and use them to run builds of your projects. The archived build artifacts and Maven artifacts are stored on the containers of Oracle Cloud Infrastructure Object Storage Classic.


After sign in, if Oracle Developer Cloud Service isn't listed on the dashboard, click **Customize Dashboard.** Under **Platform,** find **developer _id_,** click **Show,** and then close the **Customize Dashboard** window.

picture 1 - noDevCS

picture 2 - custDashboard

if you see 2 DevCS , choose 2nd

and then you can close Dialog window.

Now go tto DevCS instance, on the My Services Dashboard page, in the **developer _id_** tile, click **Action**![the Action menu icon](./Linking Oracle Cloud Infrastructure Object Storage Classic with Oracle Developer Cloud Service_files/dashboard_actions_menu.png), and select **View Details**

DevCS-details

C:\Users\DVUKMANO\Documents\A_openProjects\Lisabon-PartnerEvent\pictures\DevCS-open-console.png

If this is first time you access DevCS than you will have to create instance, click on create instance button:

C:\Users\DVUKMANO\Documents\A_openProjects\Lisabon-PartnerEvent\pictures\DevCS-create-inst.png

C:\Users\DVUKMANO\Documents\A_openProjects\Lisabon-PartnerEvent\pictures\DevCS-inst-name.png

Click next and confirm, after few minutes instance will be ready.

C:\Users\DVUKMANO\Documents\A_openProjects\Lisabon-PartnerEvent\pictures\DevCS-access.png

In order to projects becomes fully functional, you have to configure Compute, Storage and create Build VM. Here are four steps for DevCS setup:

1. [Configure a connection to Oracle Cloud Infrastructure Storage Classic](http://www.oracle.com/webfolder/technetwork/tutorials/obe/cloud/developer/config_compute_storage/devcs_config_storage.html)

In order to collect information needed for Storage setup go to Storage Classic instance and View Details

C:\Users\DVUKMANO\Documents\A_openProjects\Lisabon-PartnerEvent\pictures\SrorageClassic-view-details.png

C:\Users\DVUKMANO\Documents\A_openProjects\Lisabon-PartnerEvent\pictures\DevCS-StorageClassic-connect.png

C:\Users\DVUKMANO\Documents\A_openProjects\Lisabon-PartnerEvent\pictures\DevCS-StorageClassic-config.png


2. [Configure a connection to Oracle Cloud Infrastructure Compute Classic](http://www.oracle.com/webfolder/technetwork/tutorials/obe/cloud/developer/config_compute_storage/devcs_config_compute.html)

In order to collect compute information, go to Compute Classic oinstance and View Details
C:\Users\DVUKMANO\Documents\A_openProjects\Lisabon-PartnerEvent\pictures\DevCS-ComputeClassic-view-details.png

C:\Users\DVUKMANO\Documents\A_openProjects\Lisabon-PartnerEvent\pictures\DevcCS-ComputeClassic-config.png




3. [Create a Build VM template](http://www.oracle.com/webfolder/technetwork/tutorials/obe/cloud/developer/config_buildvm/devcs_create_buildvmtemplate.html)

Software??

Name: myLabTemplate
Platform: Oracle Linux 7

Already included: Required Build VM Components
Includes Git, Java, JUnit, Maven, Ruby and Ant. 

Include: SQLcl 4
SQL command line interface 

Scroll up and click Done.

C:\Users\DVUKMANO\Documents\A_openProjects\Lisabon-PartnerEvent\pictures\DevCS-Build-software.png





4. [Add Build VMs](http://www.oracle.com/webfolder/technetwork/tutorials/obe/cloud/developer/config_buildvm/devcs_create_buildvm.html)

Quantity: 1
VM Template: myLabTempate


You are ready to create new project and start your DevOps process.




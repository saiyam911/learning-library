### New Developer Cloud Service Setup ###

Oracle Developer Cloud Service now supports integration with Oracle Cloud Infrastructure Compute Classic and Oracle Cloud Infrastructure Object Storage Classic.

You can create virtual machines (VMs) on Oracle Cloud Infrastructure Compute Classic and use them to run builds of your projects. The archived build artifacts and Maven artifacts are stored on the containers of Oracle Cloud Infrastructure Object Storage Classic.

Before you start creating projects in Oracle Developer Cloud Service, configure Oracle Cloud Infrastructure Compute Classic and Oracle Cloud Infrastructure Object Storage Classic services of your identity domain with Oracle Developer Cloud Service, then create Build VM template with selecting software for your build and create Build VM.

Configure a connection to Oracle Cloud Infrastructure Storage Classic!(http://www.oracle.com/webfolder/technetwork/tutorials/obe/cloud/developer/config_compute_storage/devcs_config_storage.html)

Configure a connection to Oracle Cloud Infrastructure Compute Classic()

Create a Build VM template()

Add Build VMs()



old
If DevCS environment that you have has already some projects and you are not able to create a new one then here are steps to delete existing projects:

- on the dashboard open you DevCS console
![](common/DevCS-delete/images/01.png)

- in this example we will delete **SampleProject**, click on SampleProject
![](common/DevCS-delete/images/02.png)

- you can always see your current project in the top of the page
![](common/DevCS-delete/images/03.png)

- on the left hand side menu click on administration
![](common/DevCS-delete/images/04.png)

- then click on properties
![](common/DevCS-delete/images/05.png)

- and then button Delete project
![](common/DevCS-delete/images/06.png)


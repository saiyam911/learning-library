![](common/images/Lisbon-SummerCamp-header.jpg)

# ORACLE Java and Cloud Native Application Development with the Oracle Cloud #

## Introduction ##

Oracle Cloud is the industry’s broadest and most integrated public cloud. It offers best-in-class services across software as a service (SaaS), platform as a service (PaaS), and infrastructure as a service (IaaS), and even lets you put Oracle Cloud in your own data center. Oracle Cloud helps organizations drive innovation and business transformation by increasing business agility, lowering costs, and reducing IT complexity. The workshop content shows different aspects of Application Development in the cloud with different set of Oracle Cloud Services.

### Prerequisites ###

#### Oracle Public Cloud PaaS  account

The workshop is intended to work with an Oracle GSE account. You should receive email with access details prior to this event. Get the following account details ready to complete the tutorial and replace to your values when it is required:

+ Oracle Cloud account **username** and **password**
+ Oracle Cloud **identity domain**
+ **Data center/region**

[DevCS setup](DevCS-setup.md)

Before you start creating projects in Oracle Developer Cloud Service, configure Oracle Cloud Infrastructure Compute Classic and Oracle Cloud Infrastructure Object Storage Classic services of your identity domain with Oracle Developer Cloud Service, then create Build VM template with selecting software for your build and create Build VM. Detailed steps are [here](DevCS-setup.md).

Client tools

To complete certain labs you must have installed:

- [Git client](https://git-scm.com/downloads)
- [Java runtime environment](https://www.java.com/en/download/)
- [Maven](https://maven.apache.org/download.cgi)
- [Kubernetes command line tool (kubectl)](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [cURL](https://curl.haxx.se/)

or [download the prepared VirtualBox appliance](https://drive.google.com/open?id=1DDVwiZ6Pd885LinbnDkcpjMGXN5AeQ48) which contains all the necessary tools. To install VirtualBox follow this [link](https://www.virtualbox.org/wiki/Downloads).

### Important ###

During the execution you will create several public cloud service instances what will be available on the world wide web. Even if these instances are for demo purposes keep in mind it is not a best practice to use weak or known (stored here in the tutorial) passwords especially in such open environment. Thus this workshop content does not recommend any password so you need to define those. You will be asked to provide password at certain points and please remember them for later usage.

The content contains several independent modules that cover different aspects of the application development in the Oracle Cloud. These modules could be executed independently unless you find in the Prerequisites that they are dependent on each other.

----
| **Wednesday** |  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 9:00-9:15 | Introduction to workshop |
| 9:15-9:45 |  Oracle Developer Cloud Service |
| 9:45-10:30 |  WebLogic on Oracle Cloud Services<br>- Java Cloud <br>- WebLogic on Oracle Managed Kubernetes|
| **10:30-10:45** | **Coffee break** |
| 10:45-13:00 | Cloud Native Applications<br>- Application Container Cloud Service<br>- Oracle Microservices Cloud Service<br>- Helidon |
| **13:00-14:00** | **Lunch** |
| 14:00-14:45 | [Creating DB Schema, Loading Application Data and Creating WebLogic DataSource](AppDataLoad-DevCS-DBCS/README.md) |
| 14:45-15:15 | [Deploy Java EE Application on Java Cloud Service using Developer Cloud Service](AppDeploy-JCS-DevCS-DBCS/README.md) |
| **15:15-15:30** | **Coffee break** |
| 15:30-16:15 | [Cloning a Java Cloud Service Instance Using a Snapshot](jcs-clone/README.md) |
| 16:15-17:00 | [Java Cloud Service Policy Based Auto Scaling](jcs-autoscale/README.md) |

| **Thursday** |  |
|-------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 9:00-10:30 | [Deploy WebLogic on Kubernetes using WebLogic Operator](https://github.com/nagypeter/weblogic-kubernetes-operator-on-OKE) |
| **10:30-10:45** | **Coffee break** |
| 10:45-12:00 | [Build a Tweet analysis service using Application Container Cloud Service and Data Hub Cloud Service (Cassandra)](accs-dhcs-twitter/README.md) |
| 12:00-12:30 | [Deploy Tomcat based application to Application Container Cloud Service](accs-tomcat/README.md) |
| 12:30-13:00| [Deploy Application directly from Github to Application Container Cloud Service](https://github.com/nagypeter/angular-java-creditscore/blob/master/github.deploy.accs.md)|
| **13:00-14:00** | **Lunch** |

---

## [Contributing](../../CONTRIBUTING.md)

## [License](../../LICENSE.md)

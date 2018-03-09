![](../common/images/customer.logo.png)
---
# ORACLE Cloud-Native DevOps workshop #

## Managing Oracle Java Cloud Service Instances Using the PSM CLI ##

### Introduction ###

This tutorial shows how to use an Oracle Java Cloud Service instance using a command shell as an alternative to using the web-based user interface. PSM CLI is a command line tool for managing PaaS services in Oracle Cloud.

### Scenario ###

We will first connect to our identity domain and check for available JCS instances. Then we will show number of PSM CLI command to manage JCS instance. Usage of PSM CLI will be shown on two examples, works with security access lists and backup.
Full list of available PSM CLI jcs command you can find here: https://docs.oracle.com/en/cloud/paas/java-cloud/pscli/psm-jcs-commands1.html
If you get feedback of some command with job ID like “Job ID:    22598785”, then you can check status of command with “psm jcs operation-status -j 22598785”.

### Prerequisites ###
To complete this tutorial, you need:
•	Have the appropriate credentials for working with Oracle Java Cloud Service.
•	Provisioned JCS
•	Python 3.3 or later. For more information about downloading and using Python, go to python.org. You will also have to use the PIP tool pip3 to install the CLI Python package. Note: While installing Python, make sure to select the check box Add Python to PATH.
You can check in this [lab how to setup PSM CLI tool](../jcs-on-oci-psm/README.md). 

### Connect to Identity Domain ###
Be aware that you can get help for any command by adding “h” in command line, for example, help for psm command “psm h”, help for jcs command “psm jcs h”, help for creating jcs instance with payload example “psm jcs create-service h”.
Before we run any command, we have to connect to our Identity Domain. 
There is a command:
```
>psm setup
```
When you issue this command, PSM prompts you to enter values for each of the parameters, username, password, identity domain, and region and output format.
We will use this command with payload json file where you can specify all details and quickly connect to your identity domain.
```
>psm setup – c gse00012345-classic-json.json
```
Here is how payload file looks like:
```
{ 
    "username":"required", 
    "password":"required",
    "identityDomain":"required", // Traditional Cloud Account: Enter the identity domain ID.
Account with Identity Cloud Service:  Enter the identity service ID. This ID is in the format, idcs-<32-character-GUID>. Example: idcs-6666bbbb11114becad9e649bfa144444
To find out your identity domain ID or identity service ID, sign in to Oracle Cloud My Services, and click any Service Type (such as Java or Application Container). On the resulting Service Overview page, look for the “Identity Domain Id” or "Identity Service Id" field, depending on your account type.
    "region":"us", // Valid values are [us, emea, aucom]. Default is 'us'.
    "outputFormat":"short", // Desired output format. Valid values are [short, json, html]. Default is 'short'.
```

Create your setup payload or use this example (scrips??) and just change your data and connect to your environment:
```
>psm setup –c gse00012345-classic-short.json
```
You will get response with message of successful setup:
```
----------------------------------------------------
'psm setup' was successful. Available services are:
  o ADWC : Oracle Autonomous Data Warehouse Cloud
  o ADWCP : Oracle Autonomous Data Warehouse Cloud Platform
  o ANALYTICS : Oracle Analytics Cloud
…
```
Notice that in this example we are connecting to OCI-C region and that output of command will be short for all command afterword, but you can charge this with adding switch “–of json” on command where you want to change output format.


### Security access rules management ###

List of all jcs services
```
>psm jcs services
```

```
 Service       Status
 Alpha01A-JCS  Ready
```

Try the same command with json output format and check what kind of details you can get:
```
>psm jcs services –of json
```

Details of particular service:
```

> psm jcs service -s Alpha01A-JCS
```

Check access rules for Oracle Java Cloud Service instance
```
>psm jcs access-rules -s Alpha01A-JCS
```
```
Rule                       Type     Description                     Status
 ora_p2otd_ssh              DEFAULT  Permit ssh access to nodes      enabled
 ora_p2otd_ahttps           DEFAULT  Permit public access to htt...  enabled
 ora_p2otd_chttps           DEFAULT  Permit public access to htt...  enabled
 ora_p2otd_chttp            DEFAULT  Permit public access to htt...  enabled
 sys_infra2otd_admin_ssh    SYSTEM   DO NOT MODIFY: Permit PSM t...  enabled
 ora_otd2ms_chttp           SYSTEM   Permit http connection to m...  enabled
 ora_otd2ms_chttps          SYSTEM   Permit https connection to ...  enabled
 sys_wls2otd_ssh            SYSTEM   DO NOT MODIFY: Permit WLS a...  enabled
 ora_p2admin_ssh            DEFAULT  Permit ssh access to nodes      enabled
 ora_p2admin_ahttps         DEFAULT  Permit public access to htt...  enabled
 ora_wls2db_dbport          DEFAULT  Permit connection to Databa...  enabled
 ora_wls2appDB1_appDBPort1  DEFAULT  Permit connection to Databa...  enabled
 ora_sys_ms2db_ssh          DEFAULT  Permit ssh access to nodes      enabled
 ora_sys_ms2appDB1_ssh      DEFAULT  Permit ssh access to nodes      enabled
 sys_infra2wls_admin_ssh    SYSTEM   DO NOT MODIFY: Permit PSM t...  enabled
```

Access rule “ora_p2admin_ahttps” is used to access WebLogic console. 

If you run command with “-of json” you can find details:
```
{
            "ruleName":"ora_p2admin_ahttps",
            "description":"Permit public access to https administration port",
            "status":"enabled",
            "source":"PUBLIC-INTERNET",
            "destination":"WLS_ADMIN",
            "ports":"7002",
            "protocol":"tcp",
            "ruleType":"DEFAULT"
        },
```
Try to access console to be sure that it works. Now, let’u disable this access rule and test access to WL console.
```
>psm jcs disable-access-rule -s Alpha01A-JCS -r ora_p2admin_ahttps
```
If you want to enable access rule back then use this command:
```
>psm jcs enable-access-rule -s Alpha01A-JCS -r ora_p2admin_ahttps
```

### Backup management ###

Check backup configurations of Oracle Java Cloud Service instances
```
>psm jcs view-backup-config –s Alpha01A-JCS
```
Lists all backups of an Oracle Java Cloud Service instance
```
>psm jcs view-backups -s Alpha01A-JCS
```
Check specific backup
```
>psm jcs view-backup -s Alpha01A-JCS –b d16b092e-c41a-4c82-b242-8d2379d8c306
```
Delete backup
```
>psm jcs delete-backup -s Alpha01A–JCS -b d16b092e-c41a-4c82-b242-8d2379d8c306
```

Update backup configuration
Again, let’s see configuration:
```
> psm jcs view-backup-config –s Alpha01A-JCS -of json
```
```
{
    "state":"ENABLED",
    "defaultRetention":"30 days",
    "fullBackupSchedule":{
        "second":"0",
        "minute":"10",
        "hour":"13",
        "dayOfMonth":"*",
        "month":"*",
        "dayOfWeek":"Sat",
        "year":"*"
    },
    "incrementalBackupSchedule":{
        "second":"0",
        "minute":"10",
        "hour":"13",
        "dayOfMonth":"*",
        "month":"*",
        "dayOfWeek":"Sun,Mon,Tue,Wed,Thu,Fri",
        "year":"*"
    },
    "scheduledBackups":"ALL",
    "extendedRestoreTypes":"recover",
    "lastBackupDate":"2018-03-07T13:10:38.273+0000",
    "lastSuccessfulCleanupDate":"2018-03-08T13:25:04.859+0000",
    "restoreByBackupId":true,
    "deleteByBackupId":true,
    "nextFullBackupDate":"2018-03-10T13:10:00.000+0000",
    "nextIncrementalBackupDate":"2018-03-09T13:10:00.000+0000",
    "backupDestination":"BOTH",
    "cloudStorageContainer":"https://gse00012270.storage.oraclecloud.com/v1/Storage-gse00012270/Alpha01A_JCS_SC",
    "cloudStorageUser":"cloud.admin",
    "totalCloudStorageContainerUsed":"577.7MB",
    "totalCloudStorageContainerUsedInBytes":605790328,
    "totalBackupVolumeUsed":"560.4MB",
    "totalBackupVolumeUsedInBytes":587653328,
    "percentBackupVolumeUsed":2.73647403717041
}
```

What we can read from output is that full backups are performed on Saturday at 13:10, incremental backups are performed at 13:10 but not on Saturday and retention time for backups is 30 days.
By default, full backups are initiated weekly starting 12 hours after an instance was created, rounded to the nearest five-minute interval.
Let’s change backup configuration, full back up on Friday evening and incremental should skip Friday, Saturday and Sunday.
```
>psm jcs update-backup-config -s Alpha01A-JCS –c jcs-update-backup-config.json
```

payload??


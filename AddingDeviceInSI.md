# Adding storage systems

Before you begin, ensure that you have the Administrator role in IBM Storage Insights. 

## Adding a user

To add a single user, complete the following steps:

1.  In the menu bar, hover over your user name and click **Manage Users**.
2.  On the My IBM website, click **Manage** for IBM Storage Insights.
3.  Click **Manage users**.
4.  Click **Add new user**.
5.  Provide a first name, last name, and email address or IBM ID. Typically, the email address and IBM ID are identical.
6.  Assign the **Subscription administrator** or **License user** role to determine their level of access in IBM Storage Insights.

##   

## Adding multiple users

To add multiple users at the same time, complete the following steps:

1.  In the menu bar, hover over your user name and click **Manage Users**.
2.  On the My IBM website, click **Manage** for IBM Storage Insights.
3.  Click **Manage users**.
4.  Click **Add multiple users**.
5.  Download the CSV (comma-separated values) sample file.
6.  In the CSV file, include information about the users that you want to add. For each user, you must provide a first name, last name, and email address or IBM ID. Typically, the email address and IBM ID are identical. You must also assign the Subscription administrator or License user role to determine their level of access in IBM Storage Insights.

*   If you're viewing the CSV file as a spreadsheet, enter information about each user in the appropriate columns. To assign the Subscription administrator role, type x in the **Admin** column for the user; to assign the License user role, type x in the **User** column.
*   If you're viewing the CSV as a text file, include information about each user on separate lines. Use the following format: "First\_name","Last\_name","Email or IBMid", User, Admin, Status
*   Where:
*   `User` represents a License user.
*   `Admin` represents a Subscription administrator.
*   `Status` is set to Active or Inactive.

For example, to add Jane Doe with the Subscription administrator role and John Doe with the License user role, include the following information:

*   "Jane","Doe","username@example.com",,x,Active
*   "John","Doe","username2@example.com",x,,Active

7.  To upload the updated CSV file, click **Select file** and follow the prompts.
8.  Click **Submit**.

## Removing users and assigning roles

*   To remove a user, expand the user information and select the remove action. When users are removed, they will no longer have access to IBM Storage Insights.
*   To change the role of a user, you must first remove the user. Then, re-add the user and assign the new role. You can also open a support case at [https://www.ibm.com/mysupport/](https://www.ibm.com/mysupport/) to request a role change.
*   **Roles and access rights**
*   Users in IBM Storage Insights are assigned roles. Roles determine the level of access that users have to product features. There are two roles in IBM Storage Insights: Administrator (Subscription administrator) and Monitor (License user)

About this task[](https://www.ibm.com/docs/en/storage-insights?topic=started-adding-storage-systems#tasktpch_saas_t_container_adding_ssystems__context__1 "Copy to clipboard")
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

You can add multiple storage systems at the same time, or add them one by one. To add multiple storage systems, the storage systems must be of the same type and share authentication credentials.

When you add block storage systems for monitoring, their status, capacity, configuration, and performance metadata is automatically collected and analyzed. When you add storage systems that manage both block and file storage, their status, capacity, and configuration metadata for file storage is also automatically collected and analyzed.

## Before you begin

Ensure that you have the Administrator role in IBM Storage Insights. For more information about roles, see Adding and removing users. Restriction:
* You must enter a user name and password that is used to connect to that storage system. These credentials must not include any blank spaces. In rare cases, special characters might also not be allowed by IBM Storage Insights. If you can't add a storage system for monitoring because of restricted characters, it's recommended that you change the credentials for the storage system and try adding it again. Then, open a ticket for the character limitation so that we can address it in a future update.
* If you add non-IBM storage systems, and the data collector is installed on a Windows system, any directory names must not start with any of the Windows reserved words such as these: CON, PRN, AUX, NUL, COM1, COM2, COM3, COM4, COM5, COM6, COM7, COM8, COM9, LPT1, LPT2, LPT3, LPT4, LPT5, LPT6, LPT7, LPT8, LPT9

As your email address or IBMid is used by internally by the data collector when you add storage systems, you must ensure that they do not start with any of the Windows reserved words.

## About this task
You can add multiple storage systems at the same time, or add them one by one. To add multiple storage systems, the storage systems must be of the same type and share authentication credentials.

When you add block storage systems for monitoring, their status, capacity, configuration, and performance metadata is automatically collected and analyzed. When you add storage systems that manage both block and file storage, their status, capacity, and configuration metadata for file storage is also automatically collected and analyzed.

Multiple ways to add and monitor IBM Storage Virtualize storage systems: You can add an IBM Storage Virtualize storage system for monitoring by using its management GUI or the IBM Storage Insights GUI.
* Using the management GUI: If you add a storage system by using its management GUI, you must enable Call Home with cloud services. A data collector is not required when you use Call Home with cloud services to monitor an IBM Storage Virtualize storage system. For more information, see Enabling Call Home with cloud services.
* Using the IBM Storage Insights GUI: If you add a storage system by using the IBM Storage Insights GUI, you must deploy or assign a data collector. For steps on how to add the storage system, see Procedure.

Metadata collection schedule and required roles:

* Status, configuration, and capacity metadata are collected by probes and aggregated once every 24 hours.
   * For DS8000® storage systems and their pools, the value for used capacity is collected once every hour. To customize that interval, contact IBM Support.
   * For some devices, additional probes are automatically run when specific events occur on those devices, or when many events are detected in a short time period. To avoid performance bottlenecks in those cases, probes are not run more than once every 20 minutes.
 
* Performance metadata is collected by performance monitors at the following intervals:
   * Every 5 minutes for IBM block storage systems
   * Every 5 minutes for Dell EMC Unity storage systems.
   * Every 5 minutes for Hitachi VSP storage systems.
   * Every 5 minutes for NetApp storage systems that are running ONTAP 9. Every 5 minutes for Pure storage systems.
   * Every 15 minutes for other Dell EMC block storage systems.
* The user name that IBM Storage Insights Pro uses to connect to a storage system must have the required privileges (or role) on that storage system to collect different types of metadata. For more information about the requirements for each type of storage system, see User roles for collecting metadata.
* When storage systems are added that manage only file storage or object storage, you schedule the collection of asset, capacity, and configuration metadata.

## Procedure
1. Choose one of the following options:
   * **IBM Storage Insights Pro** - Click Resources, and then click Block Storage Systems, or File Storage Systems, or Object Storage Systems or Unified Storage Systems. Click Add Storage Systems or Add Storage System.
   * **IBM Storage Insights** - On the NOC dashboard, click the Add Storage Systems tile.
2. Add the information to connect to and monitor the storage system.

## Results  
After you specify the information for adding storage systems, a task is added to the list of running tasks on the page banner. If a task fails for adding a storage system, it's added to the list of failed tasks on the page banner. You can retry the tasks that failed or clear them from the list. When you retry a task, the task is added to the list of running tasks.

After a storage system is successfully connected to IBM Storage Insights, a probe is automatically run to collect status and asset information. Additionally, the storage system is added to the default alert policy for the storage system type. For example, if you add a DS8000 storage system, it's automatically added to the alert policy called Default DS8000 policy. At any time, you can change which alert policy manages a storage system, or set a storage system to not be managed by any policy.
* DS8000 - Add DS8000 storage systems to get performance and asset, capacity, and configuration metadata analyzed so that you can detect performance issues, changes in storage usage, and plan for future storage needs.
* IBM Storage Ceph - Add IBM Storage Ceph version 7 or later systems to monitor information, such as cluster ID, IP address, version, status, probe data collection, and many more. You can have a holistic view of IBM Storage Ceph environment in your IBM Storage Insights.
* IBM Storage FlashSystem family - Add IBM Storage FlashSystem storage systems to get performance and asset, capacity, and configuration metadata analyzed so that you can detect performance issues, changes in storage usage, and plan for future storage needs.
* IBM Storage Accelerate - Add IBM Storage Accelerate storage systems to get performance and asset, capacity, and configuration metadata analyzed so that you can detect performance issues, changes in storage usage, and plan for future storage needs.
* SAN Volume Controller or IBM Storage Virtualize - Add IBM Storage Virtualize storage systems to get performance and asset, capacity, and configuration metadata analyzed so that you can detect performance issues, changes in storage usage, and plan for future storage needs.
* Storwize family - Add Storwize V3500, Storwize V3700, Storwize V5000, Storwize V5000E, Storwize V7000, or IBMStorwize Flex System V7000 - Storage Node storage systems to get performance and asset, capacity, and configuration metadata analyzed so that you can detect performance issues, changes in storage usage, and plan for future storage needs.
* Storwize V7000 Unified - Add Storwize V7000 Unified storage systems to collect capacity, configuration, status, and performance metadata for block storage and capacity, configuration, and status metadata for file storage. Use the metadata to help detect performance issues, see changes in storage usage, and plan for future storage needs.
* XIV - Add XIV storage systems to get performance and asset, capacity, and configuration metadata analyzed so that you can detect performance issues, changes in storage usage, and plan for future storage needs.
* IBM Storage Scale - Add IBM Storage Scale storage systems to get asset, capacity, and configuration metadata analyzed so that you can detect changes in file and cloud storage usage and plan for future storage needs.
* IBM Cloud Object Storage - Add IBM Cloud Object Storage to get asset, capacity, and configuration metadata analyzed so that you can detect changes in storage usage and plan for future storage needs.
* Dell EMC
* Hitachi - Add Hitachi Virtual Storage Platform (VSP) F and G Series storage systems to get performance, asset, capacity, and configuration metadata analyzed for block storage so that you can detect performance issues, changes in storage usage, and plan for future storage needs.
* NetApp - Add NetApp storage systems to get performance, asset, capacity, and configuration metadata analyzed for block and file storage so that you can detect performance issues, changes in storage usage, and plan for future storage needs. The information that you can view depends on the model of storage system.
* Pure Storage - Add Pure FlashArray//M and FlashArray//X storage systems to get performance, asset, capacity, and configuration metadata analyzed for block storage so that you can detect performance issues, changes in storage usage, and plan for future storage needs.

## DS8000

Add DS8000® storage systems to get performance and asset, capacity, and configuration metadata analyzed so that you can detect performance issues, changes in storage usage, and plan for future storage needs.

Use the following information to add storage systems so that they can be monitored and that metadata can be collected, analyzed, and presented in the GUI.

**Host names or IP addresses** - The hostnames or IP addresses of the Hardware Management Console (HMC). Use hostnames if your IP addresses change regularly. For high availability, connect to both HMCs for each DS8000. Depending on what is supported in your environment, you can enter an Internet Protocol version 4 (IPv4) or IPv6 address. If you enter an IPv6 address, the preferred    representation is written as eight groups of four hexadecimal digits. Example: 2001:DB95:0000:1234:0000:0000:5678:ABCD.

**User name and Password** - The user name, which is the same as the user name for the enterprise storage server network interface (ESSNI), and password for logging in to the storage system. The user must   have Monitor privileges for the storage system so that the metadata that is analyzed and presented in the GUI can be collected.

**User Name and PassTicket key** - The user name and RACF PassTicket for logging in to the storage system. This user name is the same as the user name for the enterprise storage server network interface (ESSNI). The user must have Monitor privileges for the storage system so that the metadata that is analyzed and presented in the GUI can be collected. For more information about RACF authentication, see The RACF PassTicket.
   * Tip: Why not create a dedicated user account to manage the monitoring of your storage systems more efficiently? So, instead of using an existing user account, create a new user account to connect to and collect metadata from your storage resources. Important:
   * Status, configuration, and capacity metadata are collected by probes and aggregated once every 24 hours.
   * For more detailed monitoring, the value for used capacity is collected once every hour at the storage system and pool levels. With this turbo boost to metadata collection, you can better monitor how fast pools are changing and take more timely action

---

## Adding DS8000 storage systems that use SSLv3 and MD5 signed certificates

Due to security vulnerabilities, you cannot add DS8000® storage systems that utilize SSLv3 or MD5 certificates to IBM® Storage Insights without first disabling the security settings preventing their addition.

### Procedure

To add DS8000 storage systems that are at a firmware level using the SSLv3 protocol or MD5-signed certificates, follow these steps:

1. Log on to the server where the data collector service is installed.
2. Open the `setup.properties` file located in the data collector `conf` directory:
   - Default paths:
     - Windows: `DataCollector_windows\conf`
     - AIX®: `DataCollector_aix/conf`
     - Linux®: `DataCollector_linux_ix86/conf`
3. To disable the security settings, add one or both of the following lines to the `setup.properties` file:
   - To disable SSLv3 security setting:
     ```
     EnableSSLv3=true
     ```
   - To disable MD5 security setting:
     ```
     EnableMD5=true
     ```
   Add each setting on a separate line.
   
4. Stop and start the data collector service:
   - **Windows:**
     - Ensure you have Administrator rights.
     - Click the Start menu, type `services.msc`, and press Enter.
     - Locate the service name starting with "IBM Spectrum Control Storage Insights data collector", stop and start it.
     - Alternatively, run `dataCollector.bat` script with `stop` and `start` parameters.
   - **AIX or Linux:**
     - Ensure you have root privileges.
     - Run `dataCollector.sh` script with `stop` and `start` parameters.

For the latest firmware level recommendations and security updates for DS8000 storage systems, refer to the [IBM security bulletin](http://www.ibm.com/support/docview.wss?uid=ssg1S1005137).

---
## IBM Storage Ceph

# Adding IBM® Storage Ceph® Systems to IBM Storage Insights

Add IBM® Storage Ceph® version 7 or later systems to monitor information such as cluster ID, IP address, version, status, probe data collection, and more. IBM Storage Insights provides a holistic view of your IBM Storage Ceph environment.

IBM Storage Insights communicates directly with IBM Storage Ceph systems through Call Home with cloud services. Data collectors are not needed for monitoring IBM Storage Ceph systems.

## Planning for IBM Storage Ceph Systems

IBM® Storage Ceph® system is a software-defined storage solution that unifies file, block, and object data into one system, providing unified file-block-object management, multi-platform support, scalability, and built-in fault tolerance.

### Tips:

- **Enabling Call Home with Cloud Services:**
  To integrate an IBM Storage Ceph system with IBM Storage Insights, Call Home with cloud services must be enabled. For details on enabling this feature, refer to:
  - [Enabling IBM Storage Insights support](#)
  - [Enabling call home and IBM Storage Insights](#)

## Benefits

IBM Storage Insights helps predict and prevent storage problems before they impact your business. Key benefits include:

- Viewing information about cluster ID, IP address, version, status, probe data collection, and more.
- Monitoring capacity information: used capacity, available capacity, total capacity.
- Administering components: hosts, object storage demons, monitors, managers.

## What's Next

Once Call Home with cloud services is enabled in your IBM Storage Ceph system, proceed to add your systems to IBM Storage Insights.

For detailed instructions on adding IBM Storage Ceph systems for monitoring, refer to [Adding IBM Storage Ceph systems](#).

### Before You Begin

Before adding IBM® Storage Ceph® systems for monitoring, ensure the following prerequisites are met:

- Enable Call Home with cloud services in IBM Storage Ceph system. For instructions, see [Enabling Call Home with cloud services](#).

---

# Adding IBM Storage Ceph Systems

## Before You Begin

Before adding the IBM® Storage Ceph® systems for monitoring, ensure you meet the following prerequisites:

- Enable Call Home with cloud services in IBM Storage Ceph system. For more information, see [Enabling Call Home with cloud services](#).
- Ensure that you are assigned the Administrator role in IBM Storage Insights. For details about roles, see [Adding and removing users](#).

## About This Task

Configure Call Home with cloud services for the IBM Storage Ceph system. For more details, refer to [Enabling Call Home with cloud services](#). Once configured, you can add the IBM Storage Ceph system for monitoring through the IBM Storage Insights GUI.

**Note:** IBM Storage Insights supports monitoring IBM Storage Ceph systems of version 7 or later.

## Procedure

To add IBM Storage Ceph systems to IBM Storage Insights, follow these steps:

1. Log in to the IBM Storage Insights GUI.
2. Click **More details** in the notification titled **Add Call Home with cloud services device**. Alternatively, go to **Configuration > Call Home Storage Systems** page.
3. Select the device you want to add for monitoring and click **Approve**. The device will be added to IBM Storage Insights for monitoring.

## Results

The device is successfully added to IBM Storage Insights. To view information about a monitored IBM Storage Ceph system, navigate to **Resources > Unified Storage Systems**.

---

# IBM Storage FlashSystem Family

Add IBM FlashSystem® storage systems to monitor performance and analyze asset, capacity, and configuration metadata. This allows you to detect performance issues, changes in storage usage, and plan for future storage needs.

Use the following information to add storage systems for monitoring and collect, analyze, and present metadata in the GUI.

## Host Names or IP Addresses

Provide the host names or IP addresses used to connect to the storage systems. Use host names if your IP addresses change regularly. You can enter an IPv4 or IPv6 address (preferably in eight groups of four hexadecimal digits format for IPv6).

## Authentication Type

Choose one of the following authentication methods:

- **User Name and Password:** Provide the credentials for logging in to the storage system.
  
- **Authenticate with SSH Key:** Upload the SSH private key associated with the SSH user. Ensure the key is in PEM or PuTTY format. PuTTY Private Key version 3 files are not supported.

### User Roles

User roles required for metadata collection depend on the device type and firmware version:

- **IBM Storage FlashSystem 900, IBM FlashSystem A9000, and IBM FlashSystem A9000R:** Requires a Monitor role or equivalent.
  
- **IBM Storage FlashSystem devices running IBM Storage Virtualize 8.3.1.2 or later:** Requires a Monitor role or equivalent.
  
- **Earlier versions of IBM Storage Virtualize:** Requires Administrator or SecurityAdmin role.

If performance metadata collection is stopped, the user's role determines whether it can be automatically restarted.

## SSH Key Details

When uploading an SSH private key:

- Specify the SSH user associated with the key during its creation.
- Provide the passphrase if applicable (leave blank if none).
- For PuTTY format, ensure keys are version 2 (generated in PuTTYgen 0.75 or later).

For more information about PuTTYgen, refer to [PuTTYgen documentation](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).

## Performance Monitoring

To monitor IBM FlashSystem 900 storage systems:

1. Enable the SNMP agent on each system. 
2. IBM Storage Insights communicates with the SNMP agent on port 161 (UDP) for collecting performance metadata.

To enable SNMP agent:

- Navigate to the Block Storage Systems page.
- Right-click on the storage system and select Launch Storage System GUI.
- In the management GUI of FlashSystem 840 or 900, go to Settings > Notifications > SNMP, click Agent, and enter a community name.

---


# IBM Storage Accelerate

Add IBM Storage Accelerate storage systems to monitor performance and analyze asset, capacity, and configuration metadata. This allows you to detect performance issues, changes in storage usage, and plan for future storage needs.

IBM Storage Accelerate, part of the IBM Spectrum StorageTM family, is a software-defined storage solution based on the XIV® storage system.

Use the following information to add storage systems for monitoring and collect, analyze, and present metadata in the GUI.

## Host Names or IP Addresses

Provide the host names or IP addresses used to connect to the storage systems. Use host names if your IP addresses change regularly. You can enter an IPv4 or IPv6 address (preferably in eight groups of four hexadecimal digits format for IPv6).

## User Name and Password

The user account used for adding the storage system must have a Monitor role or equivalent monitoring privileges.

**Tip:** Consider creating a dedicated user account specifically for monitoring your storage systems. This approach helps in efficiently managing and securing access to metadata from your storage resources.

---

# IBM Storage Virtualize (SAN Volume Controller and IBM Storwize Family)

Add IBM Storage Virtualize storage systems to monitor performance and analyze asset, capacity, and configuration metadata. This allows you to detect performance issues, changes in storage usage, and plan for future storage needs.

IBM Storage Virtualize encompasses IBM® SAN Volume Controller, IBM Storage Virtualize for Public Cloud, IBM Storage Virtualize as Software Only, and IBM Storwize® storage systems, including IBM FlashSystem® devices running IBM Storage Virtualize.

Before adding IBM Storage Virtualize for Public Cloud systems, ensure they are configured for communication with IBM Storage Insights. For details, see [Configuring IBM Storage Virtualize for Public Cloud](#).

Use the following information to add storage systems for monitoring and collect, analyze, and present metadata in the GUI.

## Host Names or IP Addresses

Provide the host names or IP addresses used to connect to the storage systems. Use host names if your IP addresses change regularly. Enter IPv4 or IPv6 addresses (preferably in eight groups of four hexadecimal digits format for IPv6).

## Authentication Type

Choose one of the following authentication methods:

- **User Name and Password:** Provide the credentials for logging in to the storage system.
  
- **Authenticate with SSH Key:** Upload the SSH private key associated with the SSH user. Ensure the key is in PEM or PuTTY format. PuTTY Private Key version 3 files are not supported.

### User Roles

User roles required for metadata collection depend on the device type and firmware version:

- **For IBM Storage Virtualize 8.3.1.2 or later:** Requires a Monitor role or equivalent.
  
- **Earlier versions:** Requires Administrator or SecurityAdmin role for metadata collection.

**Tip:** Consider creating a dedicated user account for monitoring your storage systems to manage access efficiently.

## SSH Key Details

When uploading an SSH private key:

- Specify the SSH user associated with the key during its creation.
- Provide the passphrase if applicable (leave blank if none).
- For PuTTY format, ensure keys are version 2 (generated in PuTTYgen 0.75 or later).

For more information about PuTTYgen, refer to [PuTTYgen documentation](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).

## Setting the Device Statistics Collection Interval

IBM Storage Virtualize systems use a firmware-defined statistics collection interval, controlling how frequently per-node statistics for volumes, managed disks, and nodes are collected.

## Planning for IBM Storage Virtualize for Public Cloud

IBM Storage Virtualize extends SAN Volume Controller and IBM Storwize capabilities to a hybrid-cloud or cloud-based model, suitable for IBM® Cloud or Amazon Web Services (AWS).

## Handling SAN Volume Controller Cluster ID Changes

After a SAN Volume Controller cluster ID changes, the initial probe may fail. Subsequent probes will succeed.

## User Roles for Performance Metadata Collection

When adding IBM Storage Virtualize storage systems, use credentials of a user capable of logging in to collect performance metadata.

---

# Setting the Device Statistics Collection Interval

IBM Storage Virtualize storage systems utilize a statistics collection interval managed within the firmware. This interval determines how often the system collects per-node statistics for volumes, managed disks, and nodes.

**Key Points:**
- The statistics collection interval is distinct from the performance monitoring interval set in IBM® Storage Insights, which defaults to 5 minutes.
- Generally, IBM Storage Insights configures the statistics collection interval automatically. Adjustments are typically unnecessary.
- If adjustment is required, follow these guidelines:
  - Set the statistics collection interval on the IBM Storage Virtualize system to a value equal to or less than the current performance monitoring interval in IBM Storage Insights.
  - Ensure the interval set on the storage system is a divisor of the current performance monitoring interval in IBM Storage Insights to avoid missed samples.
  - For instance, with a default performance monitoring interval of 5 minutes in IBM Storage Insights, set the storage system's statistics collection interval to either 1 minute or 5 minutes using the `startstats` command. Using other intervals may lead to missed data points.

**Determining the Current Statistics Collection Interval:**
- Log in to the IBM Storage Virtualize storage system with Administrator or SecurityAdmin privileges.
- Execute the command: `lsdumps -prefix /dumps/iostats`
- Examine the file names returned, each indicating the timestamp of creation, to deduce the current interval.

**Adjusting the Statistics Collection Interval:**
- If necessary, use the `startstats` command on the IBM Storage Virtualize storage system to modify the collection interval. Example:
  ```bash
  startstats -interval 5
  ```

## Planning for IBM Storage Virtualize for Public Cloud

IBM Storage Virtualize is a proven software-defined storage solution used in SAN Volume Controller and IBM® Storwize® family environments. IBM Storage Virtualize for Public Cloud extends this capability to hybrid-cloud or cloud-based deployments on IBM® Cloud or Amazon Web Services (AWS).

**Monitoring with IBM Storage Insights:**
- IBM Storage Insights provides visibility into capacity, space usage, and performance metrics of IBM Storage Virtualize for Public Cloud systems.
- Additional monitoring features include alerting, health checks, advanced analytics, and reporting capabilities.

**Benefits:**
- Predict and prevent storage issues.
- Detailed insights into capacity, usage, and performance.
- Monitoring of health, status, and availability.
- Alert notifications and advanced analytics for storage optimization.

**How to Monitor:**
- Ensure IBM Storage Insights can connect to IBM Storage Virtualize for Public Cloud through methods like site-to-site VPN IPSec tunnels or deploying a data collector on AWS Bastion hosts.

**Tips:**
- Review supported features in IBM Storage Insights for monitoring IBM Storage Virtualize for Public Cloud.
- For detailed configuration methods, refer to specific topics on monitoring with on-premises or off-premises data collection setups.

**Ports Used by IBM Storage Insights:**
- Outbound: Port 22 for SSH
- Outbound: Port 5989 (optional, used for SSH key upload during setup)

---


## Monitoring IBM Storage Virtualize for Public Cloud with On-Premises Data Collection (Site to Site VPN IPsec)

You can connect and monitor IBM Storage Virtualize for Public Cloud storage using IBM® Storage Insights through a site-to-site virtual private network (VPN) IPSec tunnel established between your on-premises environment and the IBM Storage Virtualize for Public Cloud instances.

### About this Task

The VPN IPSec site-to-site tunnel provides a secure communication network between your on-premises infrastructure and the cloud environment. Communication between private subnets is managed by access control lists (ACLs) configured during the VPN IPSec tunnel setup.

Typically, a bi-directional IPsec site-to-site tunnel is configured to include subnets containing the following IP addresses:

- On-premises IBM Storage Virtualize cluster and replication target
- Cloud-based IBM Storage Virtualize for Public Cloud cluster and replication target

To enable communication between IBM Storage Insights and IBM Storage Virtualize for Public Cloud using the IPsec site-to-site tunnel, ensure that the IP address of the server or virtual machine hosting the data collector is included in the tunnel configuration as one of the on-premises endpoints.

For example, in the AWS Management Console, define:

- External (internet-routable) IP address of the on-premises IPsec tunnel endpoint
- Subnets/IP addresses for:
  - On-premises server or virtual machine with the data collector
  - IBM Storage Virtualize cluster and replication target
  - IBM Storage Virtualize for Public Cloud cluster and replication target in AWS

Consult your network and firewall administrators for assistance in configuring this communication setup between IBM Storage Insights and IBM Storage Virtualize for Public Cloud.

### Procedure

After configuring the connection between IBM Storage Virtualize for Public Cloud and IBM Storage Insights, follow these steps to add the storage system for monitoring:

1. Navigate to **Resources > Block Storage Systems** in IBM Storage Insights.
2. Click **Add Storage Systems**.
3. Select the SVC or Storage Virtualize icon.
4. Enter the IP address and authentication credentials for the IBM Storage Virtualize for Public Cloud instance you want to monitor.
5. Click **Connect**.

### Results

The storage system is added for monitoring and automatically included in the default alert policy for its type. Data collection initiates automatically to gather status, configuration, capacity, and performance metadata about the storage system.

### What to Do Next

- By default, asset, capacity, and configuration metadata are aggregated and collected daily.
- Performance metadata is collected every 5 minutes.
- Schedule daily capacity and inventory reports through IBM Storage Insights to gain insights into your IBM Storage Virtualize for Public Cloud storage systems.

---
### Steps to Monitor IBM Storage Virtualize for Public Cloud with Off-Premises Data Collection

You can monitor your IBM Storage Virtualize for Public Cloud storage systems in AWS by using IBM Storage Insights and installing a data collector on a bastion host in AWS.

#### Before You Begin
Ensure that:
1. The IBM Storage Virtualize for Public Cloud storage systems are deployed in AWS.
2. If used as a replication target from an on-premises environment, a VPN or dedicated link is in place.

#### Procedure
1. **Identify the External IP Address of the Bastion Host**
   - The bastion host is provisioned by default in the AWS CloudFormation template.

2. **Connect to the Bastion Host**
   - Use the private key to SSH into the bastion host:
     ```bash
     ssh -i path_to_key/privateKey.pem centos@external_ip_of_bastion
     ```

3. **Activate the GUI Proxy**
   - Run the following command on the bastion host:
     ```bash
     enable-sv-cloud-management-gui
     ```

4. **Complete Postinstallation Configuration**
   - On the Storage Insights page, register for IBM Storage Insights.

5. **Create a New Public and Private Key Pair**
   - Use the PEM file format for the key pair.

6. **Create an IBM Storage Insights User**
   - Assign the security administrator (secadmin) role to the user in the IBM Storage Virtualize for Public Cloud storage system.

7. **Associate the Public Key with the User**
   - Associate the public key created in step 5 with the IBM Storage Insights user.

8. **Download the Linux Data Collector**
   - After the IBM Storage Insights instance is created, download the Linux data collector.

9. **Copy the Data Collector to the Bastion Host**
   - Use the Linux `scp` command to securely copy the data collector to the bastion host using the key pair from step 2.

10. **Install the Data Collector**
    - Install the data collector on the bastion host.

11. **Log in to IBM Storage Insights**
    - Use your IBM ID to log in. Navigate to `Configuration > Data Collectors` and confirm that the data collector is communicating.

12. **Add Storage Systems in IBM Storage Insights**
    - Go to `Resources > Block Storage Systems`.
    - Click `Add Storage Systems`.
    - Click the SVC or Storage Virtualize icon.
    - Enter the IP address for the IBM Storage Virtualize for Public Cloud storage system cluster. This IP can be found in:
      - IBM Storage Virtualize GUI: `Settings > Network > Management IP Addresses`
      - Bastion host: `/etc/ssh/ssh_config`
      - AWS CloudFormation postinstallation output

13. **Select SSH as the Authentication Type**
    - Select the private key from step 5 as the SSH key.
    - Enter the IBM Storage Insights user ID from step 6 as the SSH user.
    - Click `Connect`.

#### Results
The storage system is added for monitoring and is automatically added to the default alert policy for the storage system type. Data collection is automatically run to collect status, configuration, capacity, and performance metadata about the storage system.

#### What to Do Next
- By default, asset, capacity, and configuration metadata is aggregated and collected daily.
- Performance metadata is collected every 5 minutes.
- Schedule daily capacity and inventory reports to gain insights about your IBM Storage Virtualize for Public Cloud storage systems.
### Troubleshooting Probing Issues and User Roles for IBM Storage Virtualize

#### Issue: Probing a SAN Volume Controller Cluster Fails When Cluster ID Changes

When a SAN Volume Controller (SVC) cluster ID changes, the initial probe after the change fails, but subsequent probes complete successfully. This commonly occurs when a cluster is rebuilt or recovered, generating a new cluster ID.

**Steps to Ensure Successful Probing After a Cluster ID Change:**
1. **Remove the Cluster from IBM Storage Insights:**
   - Before rebuilding or recovering the cluster, remove it from IBM Storage Insights.
   
2. **Rebuild or Recover the Cluster:**
   - Proceed with the rebuilding or recovery of the cluster.

3. **Add the Cluster to IBM Storage Insights:**
   - After the cluster is rebuilt or recovered, add it back to IBM Storage Insights.

#### User Roles for Collecting Performance Metadata from IBM Storage Virtualize

When adding IBM Storage Virtualize storage systems, ensure that the user credentials provided can collect performance metadata. The role required depends on the version of IBM Storage Virtualize.

**Versions Earlier than 8.3.1.2:**
- The user must have either the **Administrator** or **SecurityAdmin** role.

**Version 8.3.1.2 or Later:**
- The user can have any role, including the **Monitor** role.

**Important Notes for Version 8.3.1.2 or Later:**
- If performance metadata collection is stopped, the user's role determines whether collection can be automatically restarted.

**User Has Privileges to Start Collections:**
- If the user has the **Administrator** or **SecurityAdmin** role, the collection is automatically restarted and performance metadata is collected.

**User Does Not Have Privileges to Start Collections:**
- If the user has the **Monitor** role, IBM Storage Insights cannot automatically restart the collection. Manual intervention is required to restart the collection.

**Steps to Manually Start the Collection of Performance Metadata:**
1. **Log On to the Storage System:**
   - Use credentials of a user with the **Administrator** or **SecurityAdmin** role.

2. **Run the Command to Start Collection:**
   ```bash
   svctask startstats -interval 5
   ```
   - This command starts the collection of performance metadata with a 5-minute interval.

By following these steps, you can ensure that your SVC cluster is correctly probed after a cluster ID change and that performance metadata is collected appropriately based on user roles.

### Adding Storwize Family Storage Systems for Monitoring in IBM Storage Insights

To monitor performance and collect asset, capacity, and configuration metadata for Storwize storage systems, you can add the systems to IBM Storage Insights. This guide will help you through the process.

#### Supported Storwize Models
- Storwize V3500
- Storwize V3700
- Storwize V5000
- Storwize V5000E
- Storwize V7000
- IBM Storwize Flex System V7000 Storage Node

#### Monitoring Restriction
- **SAS Ports:** IBM Storage Insights cannot monitor SAS ports on a Storwize storage system. Use the management GUI for the storage system to monitor these ports.

#### Prerequisites
- **Host Names or IP Addresses:** Use host names if IP addresses change regularly. IPv4 and IPv6 addresses are supported. For IPv6, use the preferred format: eight groups of four hexadecimal digits (e.g., 2001:DB95:0000:1234:0000:0000:5678:ABCD).

#### Authentication Methods
1. **User Name and Password:**
   - For versions **8.3.1.2 or later:** The user must have the Monitor role or a role that includes monitoring privileges.
   - For versions **earlier than 8.3.1.2:** The user must have the Administrator or SecurityAdmin role.

   **Tip:** Consider creating a dedicated user account for managing monitoring tasks.

2. **SSH Key:**
   - **SSH Private Key:** Upload the SSH private key used for authentication.
   - **Valid Formats:** PEM and PuTTY. If in another format (e.g., OpenSSH), convert it to PEM or PuTTY.
     - **Note:** PuTTY Private Key version 3 files are not supported. For PuTTYgen 0.75 or later, choose the option to generate version 2 keys.
   - **Passphrase:** Enter the passphrase if created for the SSH key pair; otherwise, leave it blank.
   - **SSH User:** The user associated with the SSH key must have the Administrator role.
   - **SSH Password:** Enter the password if it was created; otherwise, leave it blank.

#### Adding the Storage System to IBM Storage Insights

1. **Log in to IBM Storage Insights:**
   - Navigate to `Configuration > Data Collectors`.

2. **Add a New Storage System:**
   - Go to `Resources > Block Storage Systems`.
   - Click `Add Storage Systems`.

3. **Select the Storwize Model:**
   - Click the appropriate Storwize icon.

4. **Enter Connection Details:**
   - Provide the host name or IP address of the storage system.

5. **Authenticate:**
   - **Using Username and Password:**
     - Enter the user name and password.
   - **Using SSH Key:**
     - Upload the SSH private key.
     - Enter the passphrase if required.
     - Provide the SSH user and password if required.

6. **Complete the Process:**
   - Click `Connect` to add the storage system.

#### Post-Setup
- **Monitor Health, Status, Capacity, and Performance:** IBM Storage Insights will start collecting and analyzing metadata.
- **Performance Metadata Collection:**
  - If stopped, users with the Monitor role need an administrator to manually restart the collection using:
    ```bash
    svctask startstats -interval 5
    ```

By following these steps, you can effectively add and monitor Storwize family storage systems in IBM Storage Insights, ensuring comprehensive performance analysis and metadata collection.

### Adding Storwize V7000 Unified Storage Systems to IBM Storage Insights

To monitor and collect metadata for Storwize V7000 Unified storage systems, follow these steps. You can collect capacity, configuration, status, and performance metadata for block storage, and capacity, configuration, and status metadata for file storage.

#### Important Tip
To monitor the performance of a Storwize V7000 Unified storage system, it must be added as a block storage system.

### Steps to Add Storwize V7000 Unified Storage System

#### Prerequisites
- **Host Names or IP Addresses:** 
  - Use host names if IP addresses change regularly. 
  - IPv4 and IPv6 addresses are supported. 
  - For IPv6, use the preferred format: eight groups of four hexadecimal digits (e.g., 2001:DB95:0000:1234:0000:0000:5678:ABCD).

#### Authentication Methods
1. **User Name and Password:**
   - The user must have Administrator privileges to collect and analyze metadata.

2. **SSH Key:**
   - **Upload SSH Key:** 
     - The valid file formats for SSH keys are PEM and PuTTY. If in another format (e.g., OpenSSH), convert it to PEM or PuTTY.
     - **Note:** PuTTY Private Key version 3 files are not supported. For PuTTYgen 0.75 or later, choose the option to generate version 2 keys.
     - In PuTTYgen, select "2" for PPK file version on the Private Key File Parameters window before generating the key.
   - **Passphrase:** Enter the passphrase if created; otherwise, leave it blank.
   - **SSH User:** The user associated with the SSH key must have Administrator role to collect and analyze metadata.

**Tip:** If different credentials are used for file and block storage, the user must have Administrator role for block metadata and Monitor role for file metadata.

### Adding the Storage System

1. **Log in to IBM Storage Insights:**
   - Navigate to `Configuration > Data Collectors`.

2. **Add a New Storage System:**
   - Go to `Resources > Block Storage Systems`.
   - Click `Add Storage Systems`.

3. **Select the Storwize Model:**
   - Click the appropriate Storwize V7000 Unified icon.

4. **Enter Connection Details:**
   - Provide the host name or IP address of the storage system.

5. **Authenticate:**
   - **Using Username and Password:**
     - Enter the user name and password.
   - **Using SSH Key:**
     - Upload the SSH private key.
     - Enter the passphrase if required.
     - Provide the SSH user and password if required.

6. **Complete the Process:**
   - Click `Connect` to add the storage system.

### Monitoring and Metadata Collection

- Once added, IBM Storage Insights will start collecting asset, capacity, and configuration metadata for block storage and file storage.
- Performance metadata is collected for block storage only.

### Fixing Authentication Errors

#### Problem
Authentication errors can occur if the IP address for IBM Storwize V7000 Unified is not correctly configured on SAN Volume Controller.

#### Solution

1. **Get the IP Address from Management GUI:**
   - Obtain the IP address of the IBM Storwize V7000 Unified storage system from its Management GUI.

2. **Get the Registered IP Address on SAN Volume Controller:**
   - Run the following command on the SAN Volume Controller:
     ```bash
     svcinfo lscluster -devicename
     ```

3. **Update the IP Address on SAN Volume Controller:**
   - Update the IP address using:
     ```bash
     chsystemip -clusterip <IP address>
     ```

4. **Retry the Connection:**
   - Retry the connection on IBM Storage Insights.

By following these steps, you can ensure proper monitoring and metadata collection for your Storwize V7000 Unified storage systems in IBM Storage Insights, helping you detect performance issues, see changes in storage usage, and plan for future storage needs.

### Adding XIV Storage Systems to IBM Storage Insights

To monitor XIV storage systems and collect performance, asset, capacity, and configuration metadata, follow these steps. This data helps detect performance issues, observe changes in storage usage, and plan for future storage needs.

#### Prerequisites
- **Host Names or IP Addresses:**
  - Use host names if IP addresses change regularly.
  - Both IPv4 and IPv6 addresses are supported.
  - For IPv6, use the preferred format: eight groups of four hexadecimal digits (e.g., 2001:DB95:0000:1234:0000:0000:5678:ABCD).

#### Authentication
1. **User Name and Password:**
   - The user must have the **Monitor** role or a role that includes monitoring privileges.

   **Tip:** Create a dedicated user account for managing monitoring tasks efficiently, rather than using an existing user account.

### Steps to Add XIV Storage System

1. **Log in to IBM Storage Insights:**
   - Navigate to `Configuration > Data Collectors`.

2. **Add a New Storage System:**
   - Go to `Resources > Block Storage Systems`.
   - Click `Add Storage Systems`.

3. **Select the XIV Model:**
   - Click the XIV storage system icon.

4. **Enter Connection Details:**
   - Provide the host name or IP address of the storage system.

5. **Authenticate:**
   - Enter the user name and password with the necessary monitoring privileges.

6. **Complete the Process:**
   - Click `Connect` to add the storage system.

### Post-Setup
- Once added, IBM Storage Insights will begin collecting and analyzing performance, asset, capacity, and configuration metadata for the XIV storage system.
- Monitor health, status, capacity, and performance through the IBM Storage Insights GUI.

By following these steps, you can effectively add and monitor XIV storage systems in IBM Storage Insights, ensuring comprehensive performance analysis and metadata collection.
### Adding IBM Storage Scale to IBM Storage Insights

To monitor IBM Storage Scale storage systems and collect asset, capacity, and configuration metadata, follow these steps. This data helps detect changes in file and cloud storage usage and plan for future storage needs.

#### Prerequisites
- **Host Name or IP Address:**
  - Use the host name or IP address of the cluster node for authentication.
  - Both IPv4 and IPv6 addresses are supported.
  - For IPv6, use the preferred format: eight groups of four hexadecimal digits (e.g., 2001:DB95:0000:1234:0000:0000:5678:ABCD).

#### Authentication for File Storage
1. **User Name:**
   - The user must have root privileges or privileges to run specified administration commands using the `sudo` command on the cluster node.
   - The user must have permission to log on from the specified node without entering a password to the other nodes in the cluster.
   - **Tip:** Create a dedicated user account for managing monitoring tasks efficiently.

2. **Password:**
   - The password used to log on to the cluster node.

#### Authentication for Object Storage
- To monitor object storage, specify the following credentials:
  
  1. **User Name:**
     - The user must be assigned the `admin` role in Keystone (OpenStack identity service).
     - To monitor all accounts and containers, the user must also be assigned the `ResellerAdmin` role.

  2. **Domain:**
     - The Keystone domain of the user (default setting is `Default`).

### Steps to Add IBM Storage Scale Storage System

1. **Log in to IBM Storage Insights:**
   - Navigate to `Configuration > Data Collectors`.

2. **Add a New Storage System:**
   - Go to `Resources > File Storage Systems`.
   - Click `Add Storage Systems`.

3. **Select the IBM Storage Scale Model:**
   - Click the IBM Storage Scale storage system icon.

4. **Enter Connection Details:**
   - Provide the host name or IP address of the cluster node.

5. **Authenticate:**
   - Enter the user name and password with the necessary privileges.
   - For object storage, provide the OpenStack Swift credentials (user name and domain).

6. **Configure Probes and Performance Monitoring:**
   - **Probe:**
     - Schedule the collection of status, asset, and storage information.
     - Ensure the server hosting the data collector can connect to OpenStack Swift and Keystone endpoints.
   - **Performance Monitor:**
     - Enable or disable performance monitoring.
     - Configure the IBM Storage Scale performance monitoring tool on the cluster.

### Monitoring IBM Storage Scale without Root Privileges

You can enable a non-root user on an IBM Storage Scale cluster node to monitor the storage systems by providing necessary `sudo` privileges.

### Verifying Metadata Collection for Object Storage

Ensure the server hosting the data collector can connect to OpenStack Swift and Keystone endpoints to collect asset, capacity, and configuration metadata for object storage.

### Configuring OpenStack Access for Object Storage Monitoring

Configure OpenStack access for the user name used to monitor the IBM Storage Scale object storage system.

By following these steps, you can effectively add and monitor IBM Storage Scale storage systems in IBM Storage Insights, ensuring comprehensive performance analysis and metadata collection.

### Enabling Non-Root User Monitoring on IBM Storage Scale

To monitor IBM Storage Scale storage systems without requiring root privileges, follow the steps below to configure a non-root user with the necessary permissions.

#### Prerequisites
- Ensure you can log in to the cluster node that will be used for authentication with a user account that has root privileges.
- Ensure IBM Storage Scale cluster nodes are configured for SSH login without requiring a password.
- This setup does not support clusters configured with a sudo wrapper environment due to the requirement for `mmdsh` commands.

#### Procedure

1. **Log In with Root Privileges:**
   - Log on to the cluster node used for authentication using a root user account.

2. **Edit the sudoers File:**
   - Open the sudoers file by running:
     ```sh
     visudo -f /etc/sudoers
     ```

3. **Add Command Aliases:**
   - Add the following command aliases to the sudoers file. Each command alias must be on a single line without line breaks.

     ```sh
     Cmnd_Alias TPC_GPFS_MMCMD = /usr/lpp/mmfs/bin/mmsdrquery, /usr/lpp/mmfs/bin/mmlsconfig, \
     /usr/lpp/mmfs/bin/mmgetstate, /usr/lpp/mmfs/bin/mmlsnodeclass, /usr/lpp/mmfs/bin/mmlsfs, \
     /usr/lpp/mmfs/bin/mmdf, /usr/lpp/mmfs/bin/mmlsnsd, /usr/lpp/mmfs/bin/mmlsfileset, \
     /usr/lpp/mmfs/bin/mmcloudgateway, /usr/lpp/mmfs/bin/mmlsmount, /usr/lpp/mmfs/bin/mmlssnapshot, \
     /usr/lpp/mmfs/bin/mmrepquota, /usr/lpp/mmfs/bin/mmlspolicy, /usr/lpp/mmfs/bin/mmapplypolicy
     
     Cmnd_Alias TPC_GPFS_MMDSH = /usr/lpp/mmfs/bin/mmdsh -N * /usr/lpp/mmfs/bin/mmdiag --version, \
     /usr/lpp/mmfs/bin/mmdsh -N * /lib/udev/scsi_id --whitelisted *, \
     /usr/lpp/mmfs/bin/mmdsh -N * /sbin/blockdev --getsize64 *, \
     /usr/lpp/mmfs/bin/mmdsh -N * /usr/bin/getconf DISK_SIZE *, \
     /usr/lpp/mmfs/bin/mmdsh -f 20000 -N linuxNodes 'cat /sys/class/fc_host/*', \
     /usr/lpp/mmfs/bin/mmdsh -N * /usr/lpp/mmfs/bin/mmces node list, \
     /usr/lpp/mmfs/bin/mmdsh -N * /usr/lpp/mmfs/bin/mmces service list -a, \
     /usr/lpp/mmfs/bin/mmdsh -N * /usr/lpp/mmfs/bin/mmces address list|grep object_database_node, \
     /usr/lpp/mmfs/bin/mmdsh -N * /usr/lpp/mmfs/bin/mmces address list --by-node|grep object_database_node, \
     /usr/lpp/mmfs/bin/mmdsh -v -N cesNodes /usr/lpp/mmfs/bin/mmobj config list --ccrfile object-server.conf --section DEFAULT --property devices, \
     /usr/lpp/mmfs/bin/mmdsh -f 20000 -v -N * "test -e /opt/IBM/zimon/ZIMonSensors.cfg && (grep -w collectors -A 4 /opt/IBM/zimon/ZIMonSensors.cfg | grep -w host) || true", \
     /usr/lpp/mmfs/bin/mmdsh -f 20000 -v -N nonWindowsNodes hostname
     
     Cmnd_Alias TPC_GPFS_MMDSH2 = /usr/lpp/mmfs/bin/mmdsh -f 20000 -v -N localhost test -e \
     /opt/IBM/zimon/ZIMonSensors.cfg && (grep\ -w 'collectors' -A 4 /opt/IBM/zimon/ZIMonSensors.cfg\ \ | grep -w 'host') || true
     
     Cmnd_Alias TPC_GPFS_MMDSH3 = /usr/lpp/mmfs/bin/mmdsh -f 20000 -v -N linuxNodes test -e \
     /opt/IBM/zimon/ZIMonSensors.cfg && (grep\ -w 'collectors' -A 4 /opt/IBM/zimon/ZIMonSensors.cfg\ \ | grep -w 'host') || true
     
     Cmnd_Alias TPC_GPFS_OTHER = /bin/cat *release, /usr/bin/lsb_release -a, /bin/date, /usr/bin/date, \
     /bin/grep, /bin/true, /usr/bin/test
     
     Cmnd_Alias TPC_GPFS_CMDS = TPC_GPFS_MMCMD, TPC_GPFS_MMDSH, TPC_GPFS_OTHER, TPC_GPFS_MMDSH2, TPC_GPFS_MMDSH3
     ```

4. **Grant Command Permissions:**
   - Add the following lines after the command aliases to enable the user to issue the commands:
     ```sh
     Defaults:user_name !requiretty
     user_name ALL=(ALL) TPC_GPFS_CMDS
     ```
   - Replace `user_name` with the actual user name that you will use for monitoring.

### Results

The non-root user added to the sudoers file can now monitor the IBM Storage Scale storage system using the specified commands. This setup allows for efficient monitoring without granting full root privileges.

### Verifying Asset, Capacity, and Configuration Metadata Collection for Object Storage

To verify that the server hosting the data collector can access the object services, follow these steps:

1. **List URLs for Keystone and Swift Services:**
   - On an IBM Storage Scale cluster node configured for object storage, run the following commands with a user account that has root privileges to list the URLs for the Keystone and Swift services:
     ```sh
     # Command to list Keystone service URL
     openstack endpoint list --service identity

     # Command to list Swift service URL
     openstack endpoint list --service object-store
     ```

2. **Check Connectivity:**
   - Ensure that the server hosting the data collector can connect to the IP addresses and host names included in the Keystone and Swift service URLs.
   - For example, if the URL for the Keystone service is `http://keystone.example.com:5000/v3`, ensure that the server can connect to `keystone.example.com`.

### Configuring the Collection of Performance Data for IBM Storage Scale

To configure performance data collection, follow these steps:

1. **Configure the IBM Storage Scale Performance Monitoring Tool:**
   - Run the `mmperfmon config` command on the IBM Storage Scale cluster. Refer to the [IBM Documentation](https://www.ibm.com/docs/en/STXKQY_5.1.1/com.ibm.spectrum.scale.v5r10.doc/bl1adm_mmperfmon.htm) for detailed configuration options.
   - Set the `--collector` property to the IBM Storage Scale cluster node where the collector component will run. The `--collectors` property must be set to either an IP address or a host name reachable by the server hosting the data collector.

2. **Ensure Collector Node Reachability:**
   - If the `--collectors` property is set to an internal host name, ensure it can be resolved to a public IP address accessible by the data collector server. Update the hosts file on the data collector server if necessary.

3. **Configure the Collector Component:**
   - Edit the `/opt/IBM/zimon/ZIMonCollector.cfg` file on the IBM Storage Scale cluster node where the collector component will run.

   **For IBM Spectrum Scale 5.1.0 or Earlier:**
   - Ensure the `queryinterface` property is set to `0.0.0.0`:
     ```sh
     queryinterface = "0.0.0.0"
     ```

   **For IBM Spectrum Scale 5.1.1 or Later:**
   - Ensure the following properties are set in the `ZIMonCollector.cfg` file:
     ```sh
     fallbackqueryinterface = "0.0.0.0"  # Use "::0" for IPv6
     fallbackqueryport = "9084"
     ```

4. **Restart the Collector Component:**
   - Restart the collector component to apply the changes.

5. **Assign Perfmon Designation:**
   - Use the `mmperfmon` command to designate nodes for performance data collection. Refer to the [IBM Documentation](https://www.ibm.com/docs/en/spectrum-scale/5.1.1?topic=reference-mmchnode-command) for detailed command usage.

6. **Schedule Performance Data Collection:**
   - In the IBM Storage Insights Pro GUI, schedule the performance data collection. This can be done either when adding resources for monitoring or later by creating performance monitors.

### Results and Next Steps

- A performance monitor will be created for the IBM Storage Scale storage system.
- After a successful probe run, the performance monitor will operate according to the defined interval.
- To check the progress of a performance monitor, view the Performance Monitor Status column on the File Storage Systems page. You can also open Performance Monitor Logs by right-clicking a row on the File Storage Systems page and selecting Data Collection > Open Performance Monitor Logs.

### Configuring OpenStack Access to Monitor IBM Storage Scale Object Storage

To monitor IBM Storage Scale object storage systems using OpenStack, follow these steps to ensure the user has the necessary access:

#### Procedure

1. **Set the Object Storage Account and Domain for the User:**

   The domain is set to `Default` by default and cannot be modified after the user account is created. 

   - **To set the account and domain when creating a user account:**
     ```sh
     openstack user create --domain Default --project <projectname> --password <password> <username>
     ```

   - **To set the account and domain for an existing user:**
     ```sh
     openstack user set --project <projectname> <username>
     ```

2. **Assign the Admin Role for an Object Storage Account to the User:**

   - Use the following command to assign the `admin` role:
     ```sh
     openstack role add --user <username> --project <projectname> admin
     ```

3. **Assign the ResellerAdmin Role to Monitor All Accounts:**

   To monitor all accounts on the object storage system, assign the user the role defined in the `reseller_admin_role` configuration option in the Swift proxy server. By default, this role is `ResellerAdmin`.

   - Use the following command to assign the `ResellerAdmin` role:
     ```sh
     openstack role add --user <username> --project <projectname> ResellerAdmin
     ```

   **Restriction:** If the `ResellerAdmin` role is not assigned, information will only be collected for the object storage accounts that the user has admin access to.

#### Example Commands

- **Create a user with project and domain:**
  ```sh
  openstack user create --domain Default --project my_project --password my_password my_user
  ```

- **Set the account and domain for an existing user:**
  ```sh
  openstack user set --project my_project my_user
  ```

- **Assign the admin role:**
  ```sh
  openstack role add --user my_user --project my_project admin
  ```

- **Assign the ResellerAdmin role:**
  ```sh
  openstack role add --user my_user --project my_project ResellerAdmin
  ```

By following these steps, the user will have the necessary permissions to monitor the IBM Storage Scale object storage system, ensuring comprehensive data collection and monitoring capabilities.

### Adding IBM Cloud Object Storage for Monitoring

IBM Cloud Object Storage can be monitored to collect asset, capacity, and configuration metadata. This guide provides the steps to add IBM Cloud Object Storage to your monitoring system to analyze storage usage and plan for future needs.

#### Discover Page Configuration

1. **Host Name or IP Address:**
   - Enter the host name or IP address of the manager device for IBM Cloud Object Storage.
   - The manager device is typically referred to as the Cloud Object Storage Manager or dsnet manager.
   - You can use an IPv4 or IPv6 address. For IPv6, use the preferred representation written as eight groups of four hexadecimal digits (e.g., 2001:DB95:0000:1234:0000:0000:5678:ABCD).

2. **User Name and Password:**
   - Enter the user name and password of an account with Operator, System Administrator, or Super User privileges.
   - It is recommended to create a dedicated user account for monitoring purposes to manage the monitoring of your storage systems more efficiently.

#### Configure Page

1. **Probe:**
   - The probe collects asset, capacity, and configuration metadata about IBM Cloud Object Storage.
   - The time zone displayed is determined by the location of the browser used to access the GUI.

#### Additional Tips

- **Outbound Communication:**
  - Ensure that outbound communication on port 443 is enabled in your data center. This is necessary for the data collector to stream metadata to IBM Storage Insights.
- **Performance Monitoring:**
  - Performance monitoring is not available for IBM Cloud Object Storage.

By following these steps, you can add IBM Cloud Object Storage to your monitoring system and collect necessary metadata to analyze storage usage effectively.

### Adding Dell EMC Storage Systems to IBM Storage Insights

IBM Storage Insights supports monitoring Dell EMC storage systems such as Unity, VMAX, VNX, and VNXe. Here's how you can add these systems for monitoring:

#### Add Dell EMC Unity Storage Systems

1. **Connection Details:**
   - Enter the IP addresses or host names of the Dell EMC Unity storage systems. You can separate multiple entries by commas or spaces.
   - Use IPv4 or IPv6 addresses. For IPv6, use the preferred representation (e.g., 2001:DB95:0000:1234:0000:0000:5678:ABCD).

2. **User Name and Password:**
   - Provide the credentials of an account with Operator, System Administrator, or Super User privileges.
   - Ensure the account has sufficient privileges to monitor data and adjust data collection schedules if needed.

#### Add Other Dell EMC Storage Systems (VMAX, VNX, VNXe)

1. **Step 1: Set Up SMI-S Provider or Solutions Enabler**
   - Download and configure Dell EMC SMI-S Provider or Solutions Enabler for your specific Dell EMC storage systems (VMAX, VNX, VNXe).
   - Refer to Dell EMC documentation for the versions of SMI-S Provider and Solutions Enabler that are compatible and supported.

2. **Step 2: Enter Connection Information**
   - **SMI-S Provider Host Name or IP Address:**
     - Provide the IP address or host name where the SMI-S Provider or Solutions Enabler is installed.
     - Use IPv4 or IPv6 addresses. Format IPv6 as eight groups of four hexadecimal digits.

   - **User Name and Password:**
     - Enter credentials with appropriate privileges to monitor and manage data collection schedules.
     - Ensure the account has necessary permissions defined by Dell EMC.

   - **Advanced Options:**
     - Expand to configure optional settings such as protocol (http or https), port (default 5989 for secure, 5988 for unsecured), and namespace.
     - Verify with Dell EMC documentation for the correct namespace and protocol settings.

#### Planning and Considerations

- **Monitoring Scope:**
  - Asset, capacity, and configuration metadata are collected for block and file storage.
  - Performance metadata for block storage systems is also collected.

- **Antivirus Software Considerations:**
  - Adjust antivirus settings to allow proper communication with Dell EMC Unity systems, especially if in maximum security mode.

- **Redundancy and Scalability:**
  - Adding multiple instances of SMI-S Provider or Solutions Enabler can enhance redundancy and scalability in data collection.

By following these steps, you can integrate Dell EMC storage systems into IBM Storage Insights for comprehensive monitoring and management of storage resources.

### Planning for Dell EMC Storage Systems with IBM Storage Insights

IBM Storage Insights provides robust monitoring capabilities for Dell EMC storage systems, including Unity, VMAX, VNX, and VNXe. Here’s what you need to know and plan for when integrating these systems with IBM Storage Insights:

#### Supported Dell EMC Storage Systems

1. **Unity Storage System:**
   - IBM Storage Insights connects directly to Unity devices for monitoring.
   - Supports both block storage and file storage configurations.

2. **Other Dell EMC Storage Systems (VMAX, VNX, VNXe):**
   - Monitored through Dell EMC SMI-S Provider or Solutions Enabler compliant with SMI-S 1.6.
   - These systems provide block and unified storage for NAS and SAN environments.

#### Integration and Setup

1. **Adding Dell EMC Storage Systems:**
   - Unity: Direct connection using device credentials (IP address or hostname).
   - VMAX, VNX, VNXe: Connect via Dell EMC SMI-S Provider or Solutions Enabler.
     - Configure with appropriate IP address, credentials, and optional settings like protocol and port.

2. **Antivirus Software Considerations:**
   - Adjust antivirus settings to allow communication with Dell EMC Unity systems if set to maximum security mode.

#### Benefits of IBM Storage Insights

- **Detailed Insights:**
  - View capacity, storage usage, and performance metrics.
  - Monitor health, status, and availability of storage systems.

- **Alerts and Notifications:**
  - Set up alerts and alert policies to proactively manage storage conditions.

- **Advanced Analytics and Reporting:**
  - Utilize advanced analytics to optimize storage usage and reclaim storage.
  - Create customized reports on inventory, capacity, performance, and more.

#### Metadata Collection Schedule

- **Asset, Capacity, and Configuration Metadata:**
  - Collected daily by default to provide comprehensive insights into storage systems.

- **Performance Metadata:**
  - Unity Storage Systems:
    - Collection intervals: 5 minutes (default), optionally up to 60 minutes.
  - VMAX, VNX, VNXe Block Storage Systems:
    - Collection intervals: Every 15 minutes by default.

#### Next Steps

Before fully utilizing IBM Storage Insights for monitoring, alerting, and reporting on Dell EMC storage systems, ensure you add them to the platform using the appropriate connection methods outlined above. This integration enables proactive management and optimization of storage resources to meet business needs effectively.

# Create an instance by using the wizard {#task_vwq_5g4_r2b .task}

This article describes how to create an instance using the console wizard.

-   Before creating an ECS instance, you must complete the [preparation work](../../../../reseller.en-US/Quick Start for Entry-Level Users/Preparations.md#).
-   To bind an SSH key pair when creating a Linux instance, you must [create an SSH key pair](reseller.en-US/User Guide/Key pairs/Create an SSH key pair.md#) in the target region.
-   To set the user-defined data, you must prepare the [user data](reseller.en-US/User Guide/Instances/User-defined data and metadata/User data.md#).
-   To authorize an instance to play a role, you must [create an instance RAM role and grant it permissions](reseller.en-US/User Guide/Instances/Instance RAM roles/Use the instance RAM role in the console.md#).

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs). 
2.  In the left-side navigation pane, click **Instances**. 
3.  Click **Create Instance**. 
4.  Complete the Basic Configurations as follows: 
    1.  Select a **Billing Method**: **Subscription** or **Pay-As-You-Go**. 
    2.  Select a region and zone. By default, a zone is assigned randomly. You can also select an applicable one. For more information about regions and zones, see [regions and zones](../../../../reseller.en-US/General Reference/Regions and zones.md#). 

        **Note:** 

        -   After an instance is created, you cannot change its region and zone.
        -   Some instance type families are not supported in all regions. For more information, see [Create a compute optimized instance with GPUs](reseller.en-US/User Guide/Instances/Create an instance/Create a compute optimized instance with GPUs.md#), [Create an f1 instance](reseller.en-US/User Guide/Instances/Create an instance/Create an f1 instance.md#), [Create an f2 instance](reseller.en-US/User Guide/Instances/Create an instance/Create an f2 instance.md#), [Create an SCC server instance](reseller.en-US/User Guide/Instances/Create an instance/Create an SCC server instance.md#), and [Create an EBM instance](reseller.en-US/User Guide/Instances/Create an instance/Create an EBM instance.md#).
    3.  Select an instance type and specify the quantity of instances. The availability of an instance type family is determined by the selected region. For the application scenarios of each instance type, see [instance type families](../../../../reseller.en-US/Product Introduction/Instance type families.md#). 

        **Note:** 

        -   The quota of Pay-As-You-Go or preemptible instances for your account is shown on the page.
        -   To use Elastic Network Interfaces \(ENIs\), select an enterprise-level instance type with no less than two vCPU cores or an entry-level instance type with no less than four vCPU cores. For more information about the maximum number of ENIs that can be attached to one instance, see [instance type families](../../../../reseller.en-US/Product Introduction/Instance type families.md#).
        -   To use an SSD Cloud Disk, select an I/O-optimized instance.
    4.  Select an image. You can select a system image, custom image, shared image, or marketplace image. 

        **Note:** 

        -   To use an SSH key pair, select a Linux image.
        -   To use user-defined data, select an image as instructed in [user data](reseller.en-US/User Guide/Instances/User-defined data and metadata/User data.md#).
    5.  Select storage devices: 
        -   **System Disk**: Required. A system disk is required for the image. Specify the cloud disk category and size for the system disk:

            -   Cloud disk category: The available categories are determined by the selected region.
            -   Size: The default size range is \[40, 500\] GiB. If the selected image file is greater than 40 GiB, the size is defaulted to the image file size. The available size range varies with the selected image, as shown in the following table.

                |Image|Available size range|
                |:----|:-------------------|
                |Linux \(excluding CoreOS\) FreeBSD|\[max\{20, ImageSize\}, 500\] GiB. Where, the public image size is 40 GiB for Ubuntu 14.04 32-bit, Ubuntu 16.04 32-bit, and CentOS 6.8 32-bit.|
                |CoreOS|\[max\{30, ImageSize\}, 500\] GiB|
                |Windows|\[max\{40, ImageSize\}, 500\] GiB|

        -   **Data Disk**: Optional. If you create a cloud disk as a data disk at this time, you must select the disk type, capacity, and quantity, and set whether to [encrypt](../../../../reseller.en-US/Product Introduction/Block storage/ECS disk encryption.md#). You can create an empty data disk or create a data disk from a snapshot. Up to 16 data disks can be added.

            **Note:** 

            The data disks added here have the following features:

            -   The billing method is the same as that of the instance.
            -   A Subscription data disk has to be released along with the instance, but a Pay-As-You-Go data disk can be set to being released along with the instance.
        -   If you have selected an instance type family that has local disks \(such as i1, d1, or d1ne\), the local disk information is displayed. You cannot specify the quantity or category of local disks, which is determined by the selected instance type. For information about the local disks corresponding to various instance types with local disk, see [instance type families](../../../../reseller.en-US/Product Introduction/Instance type families.md#).

5.  Click **Next: Networking** to finish the network and security group configuration: 
    1.  Select a network: 
        -   **VPC**: Must select a VPC and a VSwitch. If you do not have a VPC and a VSwitch, you can use the default ones.
        -   **Classic network**: If you purchased the ECS instance for the first time after June 16, 2016, 12:00 \(UTC + 8\), you can no longer select a classic network.
    2.  Configure the **Network Billing Method**: 
        -   To assign a public IP address to the instance, select **Assign public IP**. Then, select **PayByTraffic** as the network billing method and specify the bandwidth. For public IP addresses assigned in this way, you cannot unbind them from the instance. For more information about network billing, see [billing of network bandwidth](../../../../reseller.en-US/Pricing/Billing of network bandwidth.md#).
        -   If your instances do not need to access the Internet or your VPC instances [use an Elastic IP \(EIP\) address to access the Internet](../../../../reseller.en-US/Quick Start/Create a VPC.md#), you do not need to assign a public IP. You can unbind an EIP address from an instance.
    3.  Select a security group. You can use the default security group if you do not create one. For the rules of the default security group, see [default security group rules](reseller.en-US/User Guide/Security groups/Default security group rules.md#). 
    4.  Add an Elastic Network Interface \(ENI\). If your selected instance type supports ENI, you can add one and specify a VSwitch for it. 

        **Note:** By default, the ENI is released along with the instance. You can detach it from the instance in the [ECS console](reseller.en-US/User Guide/Elastic Network Interfaces/Detach an ENI from an instance.md#) or by using the [DetachNetworkInterface](../../../../reseller.en-US/API Reference/Elastic network interfaces/DetachNetworkInterface.md#) interface.

6.  \(Optional.\) Click **Next: System Configurations** to finish the following configuration: 
    -   Select and set logon credentials. You can choose to [set the credentials after creating an instance](reseller.en-US/User Guide/Instances/Reset an instance password.md#) or do it now. Select a credential based on the image:

        -   Linux: You can select a password or SSH key pair as a logon credential.
        -   Windows: You can only select a password as a logon credential.
    -   Specify the instance name, which is displayed in the ECS console, and the host name, which is displayed inside the guest operating system.

    -   Set the advanced options:

        -   Instance RAM role: Assign a RAM role to the instance.
        -   UserData: Customize the startup behaviors of an instance or pass data into an instance.
7.  \(Optional\) Click **Next: Grouping** to manage instances by group. You can add tags to instances to simplify future management. 
8.  Confirm the order: 
    -   In the **Configurations Selected** area, confirm all the configurations. You can click the edit icon to re-edit the configuration.
        -   \(Optional\) Click **Save as launch template** to record your configuration as a launch template for further reference and a quick launch. For more information, see [instance launch template](../../../../reseller.en-US/Product Introduction/Instances/Launch templates.md#).
        -   \(Optional\) Click **View Open API** to acquire the best API practice about how to create instances. At the left side, **API Workflow** explains the related API and request parameter values for the current operation. At the right side, the programing language-specifc sample are given for you to use, currently, **Java** and **Python** samples are provided. For more information about ECS API, see ECS API Reference [Overview](../../../../reseller.en-US/API Reference/Introduction.md#).
    -   \(Optional\) If the billing method is **Pay-As-You-Go**, you can set **Automatic Release**.
    -   \(Optional\) If the billing method is **Subscription**, you can set the duration and select whether to enable **Auto Renewal**.
    -   Confirm the configuration costs. The billing methods for an instance and Internet bandwidth determine the displayed cost information, as shown in the following table.

        |Instance billing method|Fees estimated|
        |:----------------------|:-------------|
        |Pay-As-You-Go or preemptible instance|Internet traffic fee + configuration fee. Configuration fees include: the instance type \(vCPU and memory\), the system disk, data disks \(if any\), and local disks \(if any\).|
        |Subscription|Internet traffic fee + configuration fee. Configuration fees include: the instance type \(vCPU and memory\), the system disk, data disks \(if any\), and local disks \(if any\).|

    -   Read and confirm **Terms of Service**.
9.  Click **Create Instance**. 

When the instance is activated, click **ECS console** to view the instance details on the console. In the **Instances** list of the relevant region, you can view the information of the new instance, including the instance name, the Internet IP address, and the private IP address.

-   You can create an FTP site on the instance for transferring files. For more information, see [build an FTP site on an ECS instance](https://partners-intl.aliyun.com/help/doc-detail/51998.htm).
-   To secure your instance after creation, we recommend that you perform security compliance inspection and configuration:
    -   Linux instances: See [harden operating system security for Linux](https://partners-intl.aliyun.com/help/faq-detail/49809.htm) in Security Advisories.
    -   Windows instances: See [harden operating system security for Windows](https://partners-intl.aliyun.com/help/faq-detail/49781.htm) in Security Advisories.
-   If a data disk is created along with the instance, you must partition and format the disk before use. For more information, see [format a data disk for Windows instances](../../../../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk for Windows instances.md#) or [format and mount data disks for Linux instances](../../../../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk for Linux instance.md#).


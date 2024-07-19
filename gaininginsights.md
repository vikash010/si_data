# Gaining Insights [Pro]

## Insight Charts

### Overview
The Insight Charts in IBM Storage Insights Pro provide a visual representation of recommended actions, performance metrics, and reclaimable volumes. These charts help users quickly identify areas for improvement and take action to optimize their storage environment.

### Key Features
- **Recommended Actions:** Displays actionable insights to address potential issues.
- **Performance Metrics:** Shows key performance indicators for volumes, disks, and ports.
- **Reclaimable Volumes:** Identifies volumes that can be reclaimed to free up capacity.

## Capacity Planning

### Overview
Capacity Planning in IBM Storage Insights Pro helps users forecast future capacity needs based on historical data. This feature is essential for making informed purchasing decisions and avoiding capacity shortages.

### Key Features
- **Historical Data Analysis:** Utilizes past usage metrics to project future capacity needs.
- **Forecasting:** Provides accurate forecasts for block storage systems, file storage systems, and pools.
- **Decision Support:** Aids in making informed decisions about when to purchase additional capacity.

## Performance Views

### Overview
Performance Views in IBM Storage Insights Pro offer detailed insights into the performance of storage systems. Users can monitor the performance of volumes, disks, and ports to identify bottlenecks and performance issues.

### Key Features
- **Volume Performance:** Tracks I/O rates, response times, and throughput for volumes.
- **Disk Performance:** Provides metrics for individual disks to identify potential issues.
- **Port Performance:** Monitors port performance to ensure efficient data flow.

## Reclamation Views

### Overview
Reclamation Views in IBM Storage Insights Pro provide recommendations for reclaiming unused or underutilized storage capacity. This feature helps optimize storage usage and delay the need for new capacity purchases.

### Key Features
- **Reclaimable Capacity:** Identifies volumes that can be reclaimed.
- **Optimization:** Offers recommendations to optimize storage usage.
- **Cost Savings:** Helps reduce costs by reclaiming unused capacity before purchasing more.

## Advisor Page

### Overview
The Advisor page in IBM Storage Insights Pro is a central hub for viewing, evaluating, and managing recommended actions. This page helps users understand and address potential problems in their storage environment.

### Key Features
- **Event Management:** Allows users to view and manage events with recommended actions.
- **Problem Resolution:** Helps address potential issues proactively.
- **Centralized Insights:** Provides a single view of all recommended actions and events.

## Advanced Insights

### Overview
IBM Storage Insights Pro provides advanced insights that go beyond basic monitoring. These insights help users achieve better storage utilization, intelligent capacity planning, and effective storage reclamation.

### Key Features
- **Comprehensive Views:** Offers detailed performance, capacity, and health views.
- **Advanced Analytics:** Utilizes historical data and advanced formulas for accurate forecasting.
- **Actionable Insights:** Provides specific recommendations to improve storage efficiency.

## Conclusion

IBM Storage Insights Pro is a powerful tool for managing and optimizing storage environments. With its advanced features for performance monitoring, capacity planning, and storage reclamation, users can achieve better storage utilization, reduce costs, and ensure high availability and performance.

# Viewing the Performance of Storage Systems

*Atualizado pela última vez: 2023-12-07*

View information that is collected about the performance of storage systems in your environment. You can view trends in performance over a period for storage resources to help you identify performance issues. To view performance trends, you can select metrics for volumes, disks, or ports and specify a time range.

## Before you begin
Before you view performance information about storage systems, ensure that you added a storage system for monitoring so that information is collected about it.

## Procedure
1. From the **Insights** menu, click **Performance**. The 10 storage systems with the highest overall total I/O rate over a 12-hour period are displayed in the chart and selected in the performance chart legend.
2. Hover the mouse pointer over points on a line in the chart to view a snapshot of performance information at a specific time. For example, to view the overall total I/O rate for a selected storage system for a specific time during the default 12-hour period, hover over the corresponding data collection point on the line that represents the storage system.
   
   **Tip:** To change the performance view, you can use various controls, for example:
   - To change the default period, click the relevant option, such as **1 hour**, **1 month**, or **1 year**. Alternatively, to modify the time range, click the start time field or end time field at the bottom of the chart.
   - To change the performance metrics that are displayed, click the **Metrics** ![Add metrics icon](path_to_icon). On the **Volume Metrics** tab, the **Disk Metrics** tab, or the **Port Metrics** tab, click the metric or metrics you want to display and click **OK**.
   - To display the chart information in table format, click the **Table** ![Table icon](path_to_icon).

## Results
The chart shows performance information for the selected storage systems for the metrics and time range that you specified. The performance chart legend shows detailed information about the storage systems.


# Reclamation Views

Use the recommendations to reclaim capacity before you plan new capacity purchases.

Got an alert that your storage system is running out of capacity? Or, did you click **Resources > Pools**, had a look at the values in the **Zero Capacity** column and saw that you were running out of capacity?

Instead of purchasing more capacity, click **Insights > Reclamation** to see how much capacity you can reclaim.

## Prerequisites for Running the Reclamation Analysis
To determine which volumes can be reclaimed, capacity and performance data must be available for the reclamation analysis. To run the reclamation analysis, capacity data is collected for the previous day, and a daily aggregation of the performance data is collected for the previous 14 days.

## How It Works
The reclamation analysis is run daily and if sufficient data is collected, recommendations are generated to reclaim the volumes that meet either one of the following criteria:
- The volume isn't assigned to a server.
- I/O activity was not detected in the data that was collected for the volume.

For example, the reclamation analysis is run, and it is determined that a volume isn't assigned to a server. The volume is identified as reclaimable even if I/O activity is detected for the volume. Alternatively, the reclamation analysis is run, and no I/O activity is detected for the volume. The volume is identified as reclaimable even if the volume is assigned to a server.

The reclamation analysis also detects if volumes are replica volumes, VDisk mirrored volumes, or FlashCopy® volumes. The same criteria are used to identify whether the volumes are reclaimable, but the process varies depending on the type of copy volume:

### Replica Volumes
The source volumes of volumes with replicas, such as volumes that use Metro Mirror or Global Mirror copy services, are analyzed to determine whether the volumes are reclaimable.

### VDisk Mirrored Volumes
Both copies of the VDisk mirrored volume are analyzed to determine whether the volumes are reclaimable.

### FlashCopy Volumes
The target volumes of volumes in FlashCopy relationships are analyzed if the source volumes are identified as reclaimable.

After the analysis is run, you see the total capacity that can be reclaimed, which is broken down by tier, and by volume. (The reclaimable capacity for volumes in storage systems that use data reduction technologies isn't shown. See the restrictions below.) In the table, you get a list of the volumes, the volume's capacity, and the information that you need to decide whether you want to decommission the volumes.

**Tip:** See volumes that are identified as reclaimable, such as volumes that are used to back up data or volumes that you recently assigned to a new application? If you don’t want to include these volumes in the reclamation analysis, right-click the volumes and click **Exclude from Analysis**.

## Before You Reclaim Space
It's a good practice to verify that the identified volumes are available for reclamation. Before you delete or reclaim space that was identified by IBM® Storage Insights, keep in mind the following additional considerations:

- For volumes on IBM Storage Accelerate and CKD volumes on DS8000®, the volumes are identified as reclaimable based on I/O activity, because information about the assignment of volumes to servers is not available.
- For non-IBM storage systems, volumes are identified as reclaimable based on I/O activity because information about their existing server assignments, replication relationships, and snapshot targets might not be available for the storage system. Check with your storage administrators to ensure that the identified volumes are available for reclamation and are not part of these other configurations.
- Volumes in storage systems that use data reduction technologies are identified as reclaimable, but the actual physical capacity of the volumes can’t be determined. For example, when data is deduplicated, multiple volumes can share identical blocks of data so we don't know the actual capacity of each volume. Because we can’t determine the capacity of the individual volumes, the total reclaimable capacity for each volume is displayed as zero. This applies to:
  - Volumes in IBM storage systems that support data reduction pools or volumes in storage systems that run IBM Storage Virtualize.
  - Volumes in IBM FlashSystem® A9000 storage systems.
  - Private volumes in Dell EMC storage systems are excluded from the reclamation analysis.

## Reclamation Storage Overview
Use the reclamation overview to see information about reclaimable capacity in your data center. You can see the savings that can be made by reclaiming capacity for tiered and non-tiered storage and a list of the reclaimable volumes. You can also exclude volumes from the analysis for reclamation recommendations.

## Reclamation Views of Storage Systems
Use the reclamation view of storage systems for detailed information about the reclaimable storage in your environment. You can view the storage savings that can be made by reclaiming storage, including information about the volumes that can be reclaimed.

# Reclamation Storage Overview

Use the reclamation overview to see information about reclaimable capacity in your data center. You can see the savings that can be made by reclaiming capacity for tiered and non-tiered storage and a list of the reclaimable volumes. You can also exclude volumes from the analysis for reclamation recommendations.

To identify the volumes that are not being used, the storage resources that you add for monitoring are regularly analyzed. A list of the volumes that are not being used is generated. You can decide in accordance with the internal procedures of your organization which of the volumes in the list can be decommissioned.

On the **Reclamation > View by Reclaimable Capacity** page, the overview information for reclamation is shown in the following format:

## Reclamation Donut Chart

- **Blue area of the donut chart**: Represents the amount of storage space that is used.
- **Green area of the donut chart**: Represents the amount of storage space that can be reclaimed.
- **Center of the donut chart**: Provides a rounded estimate of the storage space that can be saved when the volumes that are listed in the table are reclaimed.

## Reclamation by Tier Bar Charts
Shows the amount of storage space that can be reclaimed on each tier of storage that is defined in your data center. If you did not define tiers or if some of the storage in your data center is not tiered, a separate column shows the amount of storage space that can be reclaimed for the non-tiered storage in your data center.
- **Show the data**: To see the amount of storage that can be saved, hover the mouse pointer over the column for the tier.

## Recommendations Tab
View the volumes that are identified as potential candidates for reclamation.

**Tip**: You can select a volume or multiple volumes for exclusion from the analysis for reclamation recommendations. To exclude a volume from the analysis, right-click the volume and select **Exclude from Analysis**. The volume is removed from the Recommendations table and added to the Excluded table, and the charts are refreshed.

## Information About Reclaimable Volumes
The following information is provided about each volume that is identified as a potential candidate for reclamation:
- **Restriction**: Definitions are provided only for column headings that might require more information to understand the values that are shown in the table.
  - **Applications**: If the volume is added to an application, the name of the application is shown. If the volume is added to an application and its subcomponent, a number is shown. You can click the name or the number to view detailed information about the application.
  - **Available Capacity (GiB)**: (Previously known as Unallocated Space) The total amount of remaining space that can be used by the volume. That is, the capacity that is not used by thin-provisioned volumes. This value is determined by the formula, Capacity - Used Capacity. For IBM FlashSystem A9000, IBM FlashSystem A9000R, and Volumes from SpecV Data Reduction Pools, this value is not available.
  - **Capacity (GiB)**: The total amount of storage space that is committed to a volume. For thin-provisioned volumes, this value represents the provisioned capacity of the volume.
  - **Availability**: All storage systems.
  - **Hosts**: The name of the host to which a volume is assigned.
  - **Tier**: The tier level of the pool in which the volume is located. If the tier level was not defined for the pool in the data center, no value is shown.
  - **Time of Last IO**: The number of days, weeks, or months when the value for the I/O rate of the volume was detected. The I/O rate is one of the determining factors for identifying the volumes that are candidates for reclamation.
  - **Used Capacity (GiB)**: (Previously known as Used Pool Space) The amount of usable capacity that is taken up by data in a storage system, after data reduction techniques have been applied.

## Excluded Tab
View the volumes that are excluded from the analysis for reclamation recommendations.

**Tip**: You can select a volume or multiple volumes for inclusion in the analysis for reclamation recommendations. To include a volume in the analysis, right-click the volume and select **Include in Analysis**. The volume is removed from the Excluded table and added to the Recommendations table, and the charts are refreshed.


# Reclamation Views of Storage Systems

Use the reclamation view of storage systems for detailed information about the reclaimable storage in your environment. You can view the storage savings that can be made by reclaiming storage, including information about the volumes that can be reclaimed.

When you add a storage system for monitoring and schedule a storage systems probe, a reclamation analysis determines the volumes that can be reclaimed.

On the **Reclamation > View by Storage Systems** page, the reclamation information is displayed in the following format:

## Reclamation Donut Chart

- **Blue area of the donut chart**: Represents the amount of non-reclaimable used capacity.
- **Green area of the donut chart**: Represents the amount of reclaimable space.
- **Show the data**: If you defined storage tiers for the data center, to view the amount of storage that can be saved for each tier, hover the mouse pointer over the green area.
- **Center of the donut chart**: Provides a rounded estimate of the storage capacity that can be saved when the volumes of the storage systems that are listed in the table are reclaimed.

## Reclamation Bar Chart

Shows the amount of storage space that can be reclaimed on each storage system in your data center.

## Reclamation Chart Legend

The bottom section of the reclamation view is a table that shows more information about the storage systems. Each row represents a storage system, and each column provides reclamation information about the storage system.

## Information About Storage Systems

Use the following information for a detailed description of the columns in the table:

- **Used Capacity (GiB)**: (Previously known as Used Pool Space) The amount of usable capacity that is taken up by data in a storage system, after data reduction techniques have been applied.
- **Inactive Capacity (GiB)**: The amount of storage system space that did not have any I/O activity in the last 14 days.
- **Potentially Orphaned Capacity (GiB)**: The amount of storage system space that is not attached to any host and that is not the target in FlashCopy® relationships or remote copy relationships.
- **Reclaimable Percentage (%)**: The percentage of the total capacity of the storage system that can be reclaimed. This value is the Total Reclaimable Capacity divided by the Used Capacity.
- **Storage System**: The display name of the storage system.
- **Total Reclaimable Capacity (GiB)**: The total amount of storage system space that can be reclaimed. This is the sum of the Inactive Capacity amount and the Potentially Orphaned Capacity amount for the storage system.
- **Volumes**: The number of volumes on the storage system that can be reclaimed. Click the number to view which volumes can be reclaimed.

# Acknowledging Recommended Actions

Some recommended actions are caused by conditions that occur regularly and can be ignored. You can acknowledge those recommended actions to indicate that they were reviewed and don't require immediate attention.

## Procedure

Choose how to acknowledge a recommended action:

### Option: Acknowledge Recommended Actions in the Advisor Page

1. Click **Insights > Advisor**.
2. Select the recommended actions and click **Acknowledge**.

### Option: Acknowledge Recommended Actions for a Specific Monitored Device

1. From the **Resources** menu, click **Block Storage Systems**, **File Storage Systems**, or **Object Storage Systems**.
2. Right-click a storage system in the list and click **View Details**.
3. Click **Advisor** in the General section.
4. Select the recommended actions and click **Acknowledge**.

If some of the recommended actions that you selected are already acknowledged, those recommended actions remain acknowledged.

**Optional**: To unacknowledge a recommended action, right-click the recommended action then click **Unacknowledge**.

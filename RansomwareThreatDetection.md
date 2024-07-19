# Ransomware Threat Detection

## Overview
IBM Storage Insights Ransomware Alerting is a feature designed to enhance the security of your storage environment by detecting and responding to ransomware threats. This capability leverages advanced analytics and machine learning to identify suspicious activities that may indicate a ransomware attack, allowing organizations to take prompt action to mitigate potential damage.

Ransomware Threat Detection was introduced as a Tech-Preview feature in the 2Q23 release of Storage Insights and has been enabled by default starting from the 1Q2024 release. This feature is available only for Storage Insights Pro and not with the free version. It requires IBM Flash System with the 8.6.0 release and active data collection.

## Key Features
- **Real-time Alerts:** Provides notifications of potential threats within the dashboard and via email.
- **Comprehensive Reporting:** Offers detailed threat Alert Info with affected hosts and volumes and security status indicators for volumes and snapshots.
- **Automatic Threat Detection:** Enabled by default on supported IBM Flash Systems with the necessary firmware.

IBM® Storage Insights Pro can alert about potential ransomware attacks across various IBM Storage Virtualize and IBM FlashSystem® products. In IBM Storage Insights Pro, these potential attacks are turned into alerts that the users can act upon, or pass to other tools for further processing.
Regardless of the IBM Storage Virtualize product, you can turn on the alerts for ransomware threat detection in IBM Storage Insights Pro.


After ransomware alerts are enabled and configured in IBM Storage Insights Pro, an email is sent to the predetermined email addresses when a ransomware threat alert is triggered. The email shows details of the potential ransomware attack, including a link to the alert that is registered in IBM Storage Insights Pro > Resources > Block Storage Systems > [specific device] > General > Alerts.

For threats detected by using IBM FlashCore Module 4 technology, these alerts contain the text “Ransomware Threat Detected”. In alerts related to the other technology types, they contain the text “Workload Anomaly”. In all cases, the presence of a threat is highlighted in the GUI, and the volume or volumes associated with that threat are marked as Compromised, along with any safeguarded copies that are subsequently taken.

The users can acknowledge the alert to indicate that they have started to deal with the threat. For the users to clear the alert completely, they must clear the volumes that were associated with the threat. This means that future safeguarded copies taken of that cleared volume will be considered clear of any threats and not marked as compromised.

## Detection Types
Storage Insights Pro offers different types of ransomware detection:
1. **Detection using Volume Statistics:** Works with IBM Storage Virtualize and FlashSystem (8.6.0+), on any volume type, using compression variations to detect anomalies.
2. **Detection using FCM Drive Statistics**
3. **Detection using Signals generated by FCM4:** Uses ML and IO stats for threat detection and can detect threat vectors in minutes.

## Supported Devices
Ransomware Threat Detection is supported only for IBM Storage Virtualize and IBM FlashSystem, and not for DS8K devices, IBM File and Object Storage, or third-party storage devices.

## Alerting and Notifications
When an alert is raised, users are notified with a toast notification in the Storage Insights dashboard and receive an email notification. Email addresses are not added to the threat notification list by default and need to be updated in the settings.

## Inline Threat Detection
Inline threat detection is possible only if the mdisk is created using FCM4 drives. All volumes created using this mdisk can have inline threat detection alerts.

## Managing Threat Detection
To disable Ransomware Threat Detection on a storage system, go to Resources > Block Storage Systems, right-click the device, select Ransomware Threat Detection, disable it, and save changes.

## Handling False Positives
Ransomware alerts can be false positives if the workload mimics ransomware. Validate by performing IO operations. If data is accessible, it is a false positive. Admins should confirm at the system/application level. Once categorized as false positive, users can acknowledge the alert, and the next probe will clear the Ransomware status on the resources.

## Snapshot Handling
Snapshots created after an alert are considered compromised. Users can check the L3 page > Copy Data > Volume Snapshot table for the compromised status. Only the volumes with alerts are affected.

## Customization
Customization of additional ransomware alerting conditions is not possible for individual tenants. For changes, users need to raise an RFE request.

# Creating a webhook in IBM Storage Insights

Webhook helps you to integrate IBM® Storage Insights with third-party applications or collaboration tools such as ServiceNow.

## procedure

1. Login to your IBM Storage Insights instance and go to Configurations > Integrations. If you are in the new modern view of IBM Storage Insights, then go to Settings.
2. Click Add Integration.
3. Enter appropriate information for each field, including the webhook URL, HTTP headers, and authentication type.
4. You can test a webhook connection to third-party application by clicking Test Webhook.
5. Click Add.

# Alerts integration with Defender

IBM® Storage Defender sends integration and deregister requests to storage systems monitored in an IBM Storage Insights instance. Users with administrator role in IBM Storage Insights can approve or deny the integration requests. IBM Storage Insights sends ransomware threat alerts that are detected on storage systems to IBM Storage Defender for immediate action.

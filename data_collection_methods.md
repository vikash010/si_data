# IBM® Storage Insights - Monitoring Strategy

In IBM® Storage Insights, you can use both Call Home with cloud services and data collectors as part of your overall monitoring strategy. However, you need to keep the following considerations in mind:

## Key Considerations

1. **Single Method for Metadata Collection**
   - You can use only one method to collect metadata for each storage system.
   - If you use a data collector to collect metadata for a storage system, you cannot use Call Home with cloud services for that storage system.

2. **Multiple IBM Storage Insights Services**
   - If you have more than one IBM Storage Insights service, each service can monitor the same storage system by using different collection methods.
   - You can use Call Home with cloud services to collect metadata on one of those services.
   - If you have three services monitoring a storage system and one service uses Call Home with cloud services, you must use data collectors in the other two services.

## Example Scenario

- Suppose you have three IBM Storage Insights services (Service A, Service B, and Service C) monitoring the same storage system.
- If Service A uses Call Home with cloud services to collect metadata:
  - Service B and Service C must use data collectors to collect metadata for the same storage system.

By adhering to these guidelines, you can effectively utilize both Call Home with cloud services and data collectors within your IBM Storage Insights monitoring strategy.

# IBM Cloud Call Home and Data Collectors - Monitoring Strategy and Security

## IBM Cloud Call Home

IBM Cloud Call Home utilizes RESTful API to provide the most reliable call home method available today. These are industry standards for transmitting data through web services. The cloud call home adoption of this standard provides a better delivery mechanism of messages to the IBM call home servers, unaffected by spam filters or other technologies preventing IBM from receiving the call home messages.

### Call Home with Email Notifications

- A communication link between IBM storage systems, IBM Support, and IBM® Storage Insights that monitors the health and status of your storage.

### Call Home with Cloud Services

- Integrates IBM Storage Virtualize storage systems with IBM Storage Insights to collect detailed configuration, capacity, and performance metadata.

### Key Security Characteristics

- **ISO/IEC 27001/27017/27018/27701 ISM certified.**
- **One-way, encrypted and compressed communication.**
- **Metadata at rest is AES 256-bit encrypted.**
- **Metadata streamed to IBM Cloud is 128-bit encrypted.**
- **No access to personal, identity, and application data.**
- **Compatible with IBM Enhanced Secure Support (Blue Diamond) framework for HIPAA compliance.**
- **Dedicated vulnerability tracking and threat response team (IBM PSIRT).**
- **EU–US Privacy Shield and Swiss-US Privacy Shield Framework certification.**
- **Integrated Security and Privacy by Design (SPbD).**
- **Meets GDPR requirements.**

## Data Collectors

The data collector is a light-weight application installed on a server in your data center. It sends metadata collected about your storage systems, such as asset, configuration, capacity, and performance metadata, to your instance of IBM® Storage Insights Pro or IBM Storage Insights in an IBM Cloud data center. The installation and setup process is quick and provides immediate capacity and performance insights.

### Key Security Characteristics

#### Built-in Security

- **Communication initiated by the data collector only.**
- **No remote APIs for external interaction.**
- **Prepackaged commands and code from IBM Storage Insights.**
- **No remote code loading possible.**

#### One-way Communication

- **Outbound communication only.**
- **Data collector sends out a request for work.**
- **IBM Storage Insights responds with a data collection request.**
- **Data collector communicates with the storage resource or starts a log collection.**

#### Secure Transmission

- **All communication uses HTTPS encryption.**
- **HTTPS connections use certificates issued by Cloudflare, Inc. (issuer common name "Cloudflare Inc ECC CA-3").**
- **TLS 1.2 and TLS 1.3 with 256-byte keys for HTTPS connections.**

### Metadata Collection, Delivery, and Storage

- **Metadata is encrypted and compressed before transmission.**
- **HTTPS used for secure transmission to the IBM Cloud data center.**
- **Metadata package is decrypted, analyzed, and stored upon delivery.**
- **Firewall rules updated for outbound communication on HTTPS port 443.**

### At the IBM Cloud Data Center

- **IBM Storage Insights hosted in IBM Cloud data centers with high security standards.**
- **Each instance uses a local keystore with a unique, encrypted password.**
- **Public key certified by DigiCert used for external customer communication.**
- **End-to-end privacy and encryption ensured for each instance.**

#### Physical Protection

- **Controlled and secured data centers with restricted access.**
- **Third-party auditors vet security controls.**

#### Technical Security

- **Multi-tenant SaaS architecture with containerization technology.**
- **Kubernetes used for container management, ensuring scalability, high-availability, and disaster tolerance.**
- **Enterprise class IBM Cloud security for both front-end and back-end communication.**

#### Day-to-Day Security Measures

- **Crowdstrike EDR and Prevent for malware protection.**
- **IBM SOS® for security and regulatory compliance.**
- **IBM Security QRadar® SIEM for system and application log monitoring.**

### Database Security

- **IBM Cloud databases built on Apache Cassandra.**
- **High availability, massive scalability, and native security integration.**
- **Compliance with SOC/ISO standards, GDPR, HIPAA, and PCI DSS.**

### Organizational Security

- **Restricted access to infrastructure and instances for qualified DevOps and infrastructure team members.**
- **Regular system health and vulnerability scans.**
- **Regular penetration tests by external companies.**

## Conclusion

By adhering to these guidelines and security practices, you can effectively utilize both Call Home with cloud services and data collectors within your IBM Storage Insights monitoring strategy, ensuring robust security and compliance.


# Types of Metadata Collected by IBM® Storage Insights

Metadata is the information that IBM® Storage Insights collects about your storage devices and environment. This metadata can include, but is not limited to, the following information:

## Inventory and Configuration Metadata

- **Device Details**: Name, model, firmware, type, and more.
- **Internal Components**: Volumes, pools, disks, ports, and more.

## Capacity Metrics

- **General Capacity**: Capacity, usable capacity, used capacity.
- **Efficiency Metrics**: Compression ratios, and more.

## Performance Metrics

- **Data Rates**: Read and write data rates.
- **I/O Metrics**: I/O rates, response times, and more.

## Diagnostic Data

- **Support Information**: System failure logs, maintenance levels, and more.

## Analysis and Insights

IBM Storage Insights analyzes this metadata to help you identify problems with your storage before they impact your business. The following are some of the issues that metadata can highlight:

- Performance bottlenecks.
- Capacity usage and shortages.
- Loss of connectivity or access to devices.
- Configuration issues.

## Collection and Storage

To gather metadata, IBM Storage Insights collects and stores the information used to connect to devices. This information is stored in the database created for your IBM Storage Insights service. Passwords are encrypted before being stored in the database. Information is provided about the retention periods for the metadata that is collected to provide storage services and to improve storage services.

## Aggregation Levels

As metadata about monitored devices is collected, the aggregation level of that metadata changes over time:

### Configuration, Status, and Capacity Metadata

- **Two-Year Period**:
  - **Initial Collection**: Sample granularity.
  - **After Aging**: Hourly aggregation, then daily aggregation.

### Performance Metadata

- **One-Year Period**:
  - **Initial Collection**: Sample granularity.
  - **After Aging**: Hourly aggregation, then daily aggregation.

This process provides a more granular view of new metadata and a less granular view of aged metadata.

## Capacity Data Collection

Capacity data is collected via device probes:

- **Full Probe**: Runs typically once every 24 hours.
- **Advanced Mini Probes** (for DS8000 systems): Run every hour.
- **Mini Probes**: Event-based, for example, triggered by changes in a volume's capacity.

### Aggregation Details

- **Sample**: Data collected directly from the device and stored at sample granularity.
- **Hourly**: Sample data collected within the hour is aggregated as an hourly data value. If no sample data is collected in an hour, there is no hourly data value for that hour.
- **Daily**: Sample and hourly data points of the day are aggregated into the daily data value.


By understanding the types of metadata collected and how it is processed, you can better utilize IBM Storage Insights to monitor and manage your storage environment efficiently.


# Metadata Access in IBM® Storage Insights

Information is provided about access to the metadata that is collected and stored. Access to metadata is carefully controlled and governed by the IBM Cloud® Service Agreement and the IBM® Storage Insights Service Description.

## Key Teams with Metadata Access

- **IBM Support, Development, DevOps, and Cloud Infrastructure Teams**: These teams have the necessary access to help ensure that your day-to-day storage operations run smoothly.
- **Wider IBM Storage Insights Team**: Limited access to improve your product experience and help resolve any issues that you might encounter.

## Secure Access

- **Secure VPN Connection**: DevOps and cloud service infrastructure teams use a secure virtual private network (VPN) connection to access metadata in the IBM Cloud network.
- **Privileged User Workstations**: Access to instances is only permitted from workstations that meet the strict security controls of IBM Security policies for production servers.

## Metadata Access Controls and Authorization

- **Access Controls and Authorization Checks**: Enforced for SaaS infrastructure components and services to ensure secure access.

## Metadata Access for Resolving Issues

- **Investigating and Resolving Issues**: Access to metadata and the related IBM Storage Insights service is required to investigate and resolve issues.

## IBM Support Access for Troubleshooting

- **Read-only Access**: IBM Support has read-only access to the asset, configuration, capacity, and performance metadata collected for IBM storage systems and their internal storage resources to investigate hardware and software tickets.

## Metadata Access for Quality Improvements

- **Anonymized Metadata**: Used to improve the quality of service and to enhance the product offering.

## Data Backup and Restore

- **Automatic Backups**: Regular backups of the data are made automatically to restore instances if necessary.

## Requesting the Deletion of Personal Information

- **Deleting Personal Information**: To delete the minimal personal information stored to provide monitoring and support services for your storage systems, you can submit a request to IBM Support.


By understanding who can access the metadata and how access is controlled, you can ensure that your data remains secure while benefiting from the comprehensive monitoring and support services provided by IBM Storage Insights.

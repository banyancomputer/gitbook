# 🏭 Storage Providers

## Overview

Banyan utilizes independent data centers, known as Storage Providers (SPs) to store your data and make it accessible at all times. Each Storage Provider is meticulously chosen based on stringent criteria to guarantee the safety and accessibility of your data. These criteria include:

1. **Operational Excellence**: Providers with an excellent operations team and proven track record.
2. **Advanced Security Measures**: Essential security measures include physical security (e.g., biometric access controls), cybersecurity protocols, regular security audits, and compliance with industry standards.
3. **High Availability Infrastructure**: Providers that offer a minimum of 99.9% uptime, supported by redundant power supplies, HVAC systems, and network connectivity.
4. **Disaster Recovery and Data Redundancy**: Providers with robust disaster recovery plans in place, including the ability to quickly restore operations when there is a failure. Erasure coding is required to enhance data durability and prevent loss in the face of hardware failures.
5. **Network Connectivity and Peering**: Opt for providers with excellent network connectivity and peering arrangements to ensure low latency and high-speed access to your data from anywhere in the world.
6. **Sustainability Practices**: Although not a hard requirement, many of our Providers are operating in data centers that use primarily renewable energy.
7. **Regulatory Compliance**: Every Provider is in a top-tier data center with relevant industry regulations and adherence to compliance standards.

Providers are required to commit to a 99.9% data uptime and a 100% storage guarantee through direct Service Level Agreements (SLAs).

Our system maintains two synchronized copies of your data with different SPs at all times. These copies are stored in physically air-gapped locations, adding an extra layer of security. In the unlikely event that one SP becomes inaccessible, we promptly replicate your data with a new SP, ensuring no interruption in service.

Banyan's network of Storage Providers spans numerous regions worldwide, offering you the flexibility to choose the ideal location for your data storage needs. While not all locations are immediately available, expanding our global footprint is a key priority on our roadmap.

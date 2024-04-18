# Cloud Networking Project

## Project Overview

This project establishes a robust connection between an on-premises network and an Amazon Virtual Private Cloud (VPC) using an AWS Site-to-Site VPN connection facilitated by an AWS Transit Gateway. The objective is to ensure seamless and secure communication between resources residing on the on-premises network and those within the AWS VPC.

## Key Components

1. **AWS Site-to-Site VPN Connection**: A secure link is established between the on-premises network and the AWS VPC through an AWS Transit Gateway, providing a reliable pathway for data exchange.

2. **Transit Gateway Configuration**: Serving as a central hub, the Transit Gateway orchestrates the connectivity between the on-premises network and the VPC, facilitating efficient routing of network traffic.

3. **Route Configuration**:
   - Subnet route tables are meticulously configured to enable optimal routing between the connected networks, ensuring that data packets reach their intended destinations efficiently.
   - A static route is added to the transit gateway route table to direct traffic between the on-premises network and the VPC through the established VPN tunnel.

4. **Redundancy Mechanism**: The setup incorporates built-in redundancy within the site-to-site VPN configuration. In the event of a primary tunnel failure, a secondary tunnel with its unique IP address seamlessly takes over, ensuring continuous connectivity without disruption.

## Project Workflow

1. **On-Premises VPN Router Configuration**:
   - The provided script sets pre-shared keys and IP addresses for VPN tunnels on the on-premises VPN router.
   - The StrongSwan VPN service is enabled and initiated to establish the VPN tunnels.

2. **Tunnel Management**:
   - The primary VPN tunnel is activated using the command `sudo strongswan up tunnel1`.
   - If necessary, the primary tunnel can be gracefully terminated with `sudo strongswan down tunnel1`, and the secondary tunnel can be brought online using `sudo strongswan up tunnel2`.

3. **Testing Connectivity**:
   - A dedicated network testing instance within the VPC is employed to verify the integrity of the VPN connection by pinging the on-premises file server.
   - Network traffic is intelligently routed through the transit gateway and VPN tunnel, validating seamless communication between the VPC and the on-premises network.


## Diagram

Refer to the visual representation of the project architecture available in the [diagram](link-to-diagram) provided within the GitHub repository.

## Additional Resources

For more information on AWS Transit Gateway VPN connectivity options, refer to the [AWS documentation](https://docs.aws.amazon.com/whitepapers/latest/aws-vpc-connectivity-options/aws-transit-gateway-vpn.html).

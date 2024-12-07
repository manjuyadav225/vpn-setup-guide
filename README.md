# Client VPN Setup Using OpenVPN Access Server on AWS

This guide provides step-by-step instructions to set up Client VPN in AWS which is a managed service that allows you to create a VPN endpoint (VPN server) that users can connect to from their devices using an OpenVPN-based client. 
---

## Prerequisites

1. **AWS Account**: Ensure you have access to an AWS account.
2. **OpenVPN Access Server**: We'll use the AWS Marketplace AMI for OpenVPN Access Server.
3. **Key Pair**: Prepare to create and download an AWS EC2 key pair.

---

## Setup Instructions

### 1. Launch an EC2 Instance
1. Log in to your AWS account.
2. Select a region different from your current one (e.g., **N. Virginia**) to reroute traffic.
3. Navigate to the **EC2 Dashboard** and click **Launch **.
4. Name your instance (e.g., `my-openvpn-server`).

### 2. Choose an AMI
1. Go to the **AWS Marketplace AMIs**.
2. Search for `access server`.
3. Select the **OpenVPN Access Server** AMI.
   - Choose the **Free Tier (BYOL)** option.
   - Use the `t2.micro` instance type (free tier eligible).

### 3. Configure Key Pair and Launch the Instance
1. Create a new key pair, name it, and download it.
2. The security group is pre-configured for the community version; you can use the default settings.
3. Click **Launch Instance** and wait for the instance to initialize.

---

## Connect to the Instance

### Option 1: EC2 Instance Connect (Preferred for Windows Users)
1. Click **Connect** on the instance page.
2. Choose the **EC2 Instance Connect** tab.
3. Change the username to `openvpnas`.
4. Follow the on-screen instructions to connect.

### Option 2: SSH Client (For Advanced Users)
1. Follow the steps in the **SSH Client** tab.
2. Replace `root` with `openvpnas` when connecting. If you fail to do so, the connection will close.

For more details, refer to the [official documentation](https://openvpn.net/as-docs/aws-ec2.html#connect-to-your-new-ami-76631).

---

## Initialize OpenVPN Access Server
1. Follow the terminal prompts to configure OpenVPN:
   - Specify a username (default: `openvpn` or any preferred username).
   - Set a password.
2. The terminal will provide Admin and Client UI URLs for browser access.

---

## Access the Admin and Client Interfaces
1. Open the **Admin UI URL** in your browser:
   - If you encounter a security warning (due to a self-signed certificate), proceed anyway.
2. Log in using the username and password you set during initialization.
3. Similarly, open the **Client UI URL** and log in.

---

## Configure and Use the VPN
1. Download the OpenVPN client portal for your operating system:
   - Refer to the [official documentation](https://openvpn.net/connect-docs/operating-systems.html) for instructions.
2. Turn on the VPN connection and monitor its statistics.
3. Verify your connection:
   - Check your public IP and location by visiting [WhatIsMyIP](https://whatismyipaddress.com).
   - The IP and region should match your VPN server's location.

---

## Test with Multiple Clients
1. OpenVPN Access Server supports up to two clients for free.
2. Log in from a second device using the same credentials.

---

## Cleanup
1. If no longer needed, terminate the EC2 instance to avoid incurring charges.

---

## Additional Resources
- [OpenVPN AWS Documentation](https://openvpn.net/as-docs/aws-ec2.html#connect-to-your-new-ami-76631)
- [OpenVPN Client Installation Guide](https://openvpn.net/connect-docs/operating-systems.html)

---


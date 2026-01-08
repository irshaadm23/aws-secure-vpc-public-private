#Verification
This document verifies the behaviour described in the README.

#Phase 1 -Public EC2 Reachability
'''bash
curl http://publicip

Expected Result
 • NGINX default page is returned
 • Confirms:
 • EC2 has a public IP
 • Subnet route table points to an Internet Gateway
 • Inbound internet access works


#Phase 2 — Private EC2 (Outbound-Only Access)
Access Method
Connected to the private EC2 using AWS Systems Manager Session Manager
No SSH used
No inbound ports opened
Instance has no public IP
Local Service Check
curl http://localhost

Confirm Outbound Internet Access via NAT
curl ifconfig.me
Expected Result
Returned IP matches the NAT Gateway Elastic IP
Confirms:
Traffic exits through NAT Gateway
Instance has outbound-only internet access
No inbound connectivity exists

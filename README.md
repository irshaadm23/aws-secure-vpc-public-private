# AWS VPC: Public & Private Subnets with NAT and SSM (No SSH)

## Overview
This project demonstrates a **core AWS networking pattern** used in production environments:

> Public-facing resources are isolated from private workloads, which have outbound-only internet access and are managed securely without SSH.

The focus is on **network boundaries, routing behaviour, and secure access**, not application complexity.

## What Was Built
- An AWS VPC (`10.0.0.0/16`) with **public and private subnets**
- A **public EC2** instance exposed via an Internet Gateway
- A **private EC2** instance with:
  - no public IP
  - no inbound access
  - outbound-only internet access via a NAT Gateway
- Secure access to the private EC2 using **IAM + AWS Systems Manager (Session Manager)**


## Key Design Decisions
- **NAT Gateway** is used instead of public IPs to allow outbound internet access
- **Private subnets** reduce attack surface
- **Systems Manager** replaces SSH for secure, auditable access
- **Route tables**, not subnet names, determine public vs private access

---

## Verification
All verification steps and command outputs are documented in:

 `docs/verification.md`


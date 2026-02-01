# Risk Analysis – Legacy System

## Overview
The current production setup consists of a single EC2 instance hosting a web application.
This architecture represents a legacy deployment model with limited resilience and scalability.

## Current Architecture
- Single EC2 instance
- Apache web server
- Public IP access
- No load balancer
- No auto-scaling

## Identified Risks

### 1. Single Point of Failure (SPOF)
The application runs on a single server. Any failure (instance crash, OS issue, or network outage)
results in complete service downtime.

### 2. No Scalability
The system cannot automatically scale based on traffic demand, increasing the risk of
performance degradation during peak usage.

### 3. Manual Recovery
In case of failure, recovery requires manual intervention.

### 4. Deployment Risk
Any update or maintenance activity causes service interruption, leading to downtime during releases.

## Risk Impact
- High availability risk
- Increased downtime probability
- Poor user experience during failures or updates

## Mitigation Strategy
To reduce these risks, the system will be migrated to a high-availability architecture using:
- Application Load Balancer (ALB)
- Auto Scaling Group (ASG)
- Health checks and automated instance replacement
- Post-release monitoring using CloudWatch

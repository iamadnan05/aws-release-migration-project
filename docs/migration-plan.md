# Migration Plan – Lift and Shift Release

## Overview
This document describes the release plan used to migrate a legacy web application
from a single EC2 instance to a high-availability AWS architecture using an
Application Load Balancer (ALB) and Auto Scaling Group (ASG).

The migration follows a lift-and-shift approach, where the existing application
is moved without code changes to minimize functional risk.

---

## Migration Approach
- Migration Type: Lift and Shift
- Release Strategy: Infrastructure-level cutover
- Downtime Strategy: Minimal downtime through parallel environments
- Rollback Readiness: Legacy instance retained during initial validation

---

## Pre-Migration Checks
The following checks were completed before initiating the cutover:

1. **Legacy System Stability**
   - Legacy EC2 instance running without errors
   - Application accessible via public IP

2. **Target Environment Readiness**
   - Auto Scaling Group running with desired capacity
   - Application Load Balancer configured and reachable
   - Target group health checks reporting healthy instances

3. **Networking & Security Validation**
   - Security groups allow HTTP traffic on port 80
   - Instances reachable through the load balancer

4. **Monitoring Preparedness**
   - CloudWatch metrics available for EC2 and ALB
   - Baseline performance metrics observed

---

## Cutover Execution Steps
The cutover was executed in a controlled manner as follows:

1. Verified application accessibility through the ALB DNS endpoint
2. Confirmed all target instances were healthy in the target group
3. Stopped the legacy EC2 instance to redirect traffic exclusively to the new architecture
4. Monitored load balancer health checks during and after cutover

---

## Post-Cutover Validation
After the cutover, the following validation steps were performed:

1. **Application Availability**
   - Website remained accessible via the ALB endpoint
   - No service interruption observed during the cutover

2. **Health Check Validation**
   - All target instances remained in healthy state
   - No increase in unhealthy host count

3. **Performance Observation**
   - Response times remained within acceptable range
   - CPU utilization remained stable across instances

---

## Release Outcome
The migration was completed successfully with:
- No observed downtime
- Improved availability through multi-instance deployment
- Automated recovery enabled via Auto Scaling

The system was deemed stable for continued operation in the new architecture.

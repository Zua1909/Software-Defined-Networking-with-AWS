---
title : "Verify Dynamic Routing and Policy Automation"
date : "`r Sys.Date()`"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Overview of the Verification Section

This section is dedicated to the critical phase of verifying the functionality of our SDN solution. You will put the entire system to the test, from the initial setup to the automated failover mechanism. The primary objective is to confirm that the policy you've automated—to re-route traffic upon a server failure—works as intended. You will first validate that the primary web service is running, then simulate a failure by stopping the primary EC2 instance. Finally, you will observe and confirm that the Elastic IP has been successfully re-associated with the backup server, proving that our SDN control plane has successfully executed its policy.

#### Key Concepts

* **Dynamic Routing:** The ability of a network to automatically adjust its traffic paths in response to changes in the network topology or state, without manual intervention.
* **Policy Automation:** The use of scripts or code to automatically enforce predefined network policies, such as failover rules, security policies, or traffic shaping.
* **Failover Testing:** The process of intentionally simulating a system failure to verify that the redundant or backup system takes over successfully and without data loss.

#### Contents:

* [6.1-Initial-Verification](/6-Verify-Dynamic-Routing-and-Policy-Automation/1-Initial-Verification)
* [6.2-Simulate-Web-Primary-Failure](/6-Verify-Dynamic-Routing-and-Policy-Automation/2-Simulate-Web-Primary-Failure)
* [6.3-Verify-Failover-and-Dynamic-Routing](/6-Verify-Dynamic-Routing-and-Policy-Automation/3-Verify-Failover-and-Dynamic-Routing)
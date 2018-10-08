## AWS Region, AZs, Edge locations

* Each
  region
  is a separate geographic area, completely independent, isolated from the other regions 
  &
   helps achieve the greatest possible fault tolerance and stability
* Communication
  **between regions is across the public Internet**
* Each region has
  **multiple Availability Zones**
* Each AZ is physically isolated, geographically separated from each other and designed as an independent failure zone
* **AZs are connected with low-latency private links \(not public internet\)**
* Edge locations are locations maintained by AWS through a worldwide network of data centers for the distribution of content to reduce latency.



## AWS Organizations

* AWS Organizations offers policy-based management for multiple AWS accounts
* Organizations allows creation of groups of accounts and then apply policies to those groups
* Organizations enables you to centrally manage policies across multiple accounts, without requiring custom scripts and manual processes.
* Organizations helps simplify the billing for multiple accounts by enabling the setup of a single payment method for all the accounts in the organization through consolidated billing

## Consolidate Billing

* Paying account with multiple linked accounts
* Paying account is independent and should be only used for billing purpose
* Paying account cannot access resources of other accounts unless given exclusively access through Cross Account roles
* All linked accounts are independent and soft limit of 20
* One bill per AWS account
* provides
  **Volume pricing discount**
  for usage across the accounts
* allows 
  **unused Reserved Instances**
  to be applied across the group
* Free tier is not applicable across the accounts






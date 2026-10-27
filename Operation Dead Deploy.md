# Azure Fundamentals: Investigating Azure deployment activity

## Scenario
An intern was given temporary contributor access on Friday to create a test environment for experimenting. On Monday morning, I found this in the subscription, i'm investigating the damage and why this was allowed to happen.

## Environment
Mad Hat Labs Azure Training Platform Reader Access.

## Investigation
1. Locate the non-compliant resource group
  - The company has a standard naming convention of {resource-type}-{workload}-{environment}
  - eg. rg-madhat-public-readonly
<img width="1024" height="443" alt="image" src="https://github.com/user-attachments/assets/1cf6fd67-b0d5-4de2-aa8d-18e09ce1fc42" />


2. Investigate the resource
  - Investigate the tags to find who the resource belongs to and find the purpose of the resource.
<img width="1697" height="257" alt="image" src="https://github.com/user-attachments/assets/22ce4a77-b83c-4e69-a8fd-7c8a042f4b3d" />

3. Investigate Deployment History
   - Screenshot shows the deployment history.

<img width="1505" height="106" alt="image" src="https://github.com/user-attachments/assets/5080752b-cb99-44a6-b170-33c582da8876" />

4. Investigate Policy
   - Why did our company's policy not block the incorrect naming convention?
   - The screenshot shows that the policy is used for auditing
<img width="1045" height="152" alt="image" src="https://github.com/user-attachments/assets/c4333143-eb56-4570-ace6-ac84f52cd34f" />



## What broke / what surprised me
Nothing in particular surprised me, this lab was used to explore Azure.

## Findings and recommendations
Findings: 
The intern was practicing deploying resource groups in Azure. The intern forgot to delete the resource and did not comply with company naming standards.

Recommendations: 
Fix effect types of policies. Our naming convention policy had an audit effect type. This allows resources to be created although they do not follow proper naming convention. This should be fixed to Deny.


## What I learned
- Learnt the importance of tagging
- Learnt how to navigate Azure
- Learnt the different effect types

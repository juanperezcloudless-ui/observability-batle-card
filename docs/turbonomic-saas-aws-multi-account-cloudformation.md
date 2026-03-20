# Turbonomic SaaS AWS Multi-Account Onboarding Runbook

## 1. Onboarding AWS Organizations Root into Turbonomic SaaS

- Step 1: Create a CloudFormation StackSet to deploy cross-account IAM roles.
- Step 2: Configure permissions in IAM for all accounts in your organization.
- Step 3: Verify the roles are assumed correctly in Turbonomic SaaS.

## 2. EKS + RDS Discovery Permissions

In your CloudFormation template, ensure to include the following permissions:

```yaml
Resources:
  EKSDiscoveryRole:
    Type: AWS::IAM::Role
    Properties:
      Policies:
        - PolicyName: EKSDiscoveryPolicy
          PolicyDocument:
            Version: '2012-10-17'
            Statement:
              - Effect: Allow
                Action:
                  - eks:DescribeCluster
                  - rds:DescribeDBInstances
                Resource: '*'
```

## 3. Optimizing Containers in EKS

To optimize containers in EKS, follow these steps:

1. Ensure you have the required Kubernetes access via RBAC.
2. Use the `aws-auth` ConfigMap to grant access to the IAM roles created earlier.
3. Recommended approach includes setting resource requests and limits in your pod definitions.

## 4. Screenshots Section

### Navigation Steps:
1. Log into the Turbonomic SaaS UI.
2. Navigate to **Settings** > **Integrations** > **AWS**.
3. Click on **Add AWS Account**.

![Screenshot 1](../screenshots/screenshot1.png)

![Screenshot 2](../screenshots/screenshot2.png)

## 5. Screenshots

### Placeholder for Screenshots
1. ![screenshot1](../screenshots/screenshot1.png) - First screenshot description.
2. ![screenshot2](../screenshots/screenshot2.png) - Second screenshot description.

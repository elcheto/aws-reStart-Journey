Lab Report: Using Amazon Inspector for vulnerability assesment and remediation
Prepared by: Elena

### Lab Overview
In this lab, I used Amazon Inspector to identify and fix security vulnerabilities within AWS Lambda functions. The goal was to practice automating security scans for both software dependencies and custom code to ensure the application remains secure during development.

Objectives Completed
Activated Amazon Inspector to monitor the AWS environment.

Analyzed security findings and interpreted CVE data.

Remediated vulnerabilities by updating function dependencies.

## Task 1: Activating the Service
I started by navigating to the Amazon Inspector console and activating the service. I monitored the dashboard until the Environment coverage for Lambda functions reached 100%, confirming that Inspector was actively scanning my resources.

## Task 2: Reviewing Vulnerabilities
Under All findings, I identified a medium-severity vulnerability (CVE-2023-32681) related to an outdated requests library.

I researched the specific threat via the National Vulnerability Database (NVD) link provided in the console.

I checked the Remediation section, which advised upgrading the package to a more recent version.

## Task 3: Remediating and Verifying
To fix the issue, I performed the following steps:

1. Code Update: I navigated to the Lambda console and opened the get-request function.

2. Version Control: I modified the requirements.txt file, changing requests==2.20.0 to requests to ensure the latest secure version would be used.

3. Deployment: I deployed the changes, which automatically triggered a re-scan by Inspector.

4. Confirmation: I returned to the Inspector dashboard and confirmed the finding was moved to Closed status, verifying that the vulnerability was successfully resolved.

### Conclusion
By completing this lab, I successfully demonstrated how to use automated tools to maintain a strong security posture. I now know how to interpret Inspector's reports and apply quick remediations to keep cloud-native applications safe from known exploits.

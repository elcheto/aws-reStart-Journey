# Lab Using Amazon Inspector for vulnerability assesment and remediation
Prepared by: Elena

### Lab Overview
In this lab, I used Amazon Inspector to identify and fix security vulnerabilities within AWS Lambda functions. The goal was to practice automating security scans for both software dependencies and custom code to ensure the application remains secure during development.

Objectives Completed
Activated Amazon Inspector to monitor the AWS environment.

Analyzed security findings and interpreted CVE data.

Remediated vulnerabilities by updating function dependencies.

## Task 1: Activating the Service
I started by navigating to the Amazon Inspector console and activating the service. I monitored the dashboard until the Environment coverage for Lambda functions reached 100%, confirming that Inspector was actively scanning my resources.

<img width="700" height="350" alt="Lab 279_1" src="https://github.com/user-attachments/assets/e5c3034e-ed9c-41e5-914d-459963b4129e" />

<img width="400" height="240" alt="Lab 279_2" src="https://github.com/user-attachments/assets/188c768e-4526-47e5-8a10-37f3b0879f68" />



## Task 2: Reviewing Vulnerabilities
Under All findings, I identified a medium-severity vulnerability (CVE-2023-32681) related to an outdated requests library.

<img width="700" height="350" alt="Lab 279_4" src="https://github.com/user-attachments/assets/02b752cd-786c-44a8-847e-768f8805271d" />

I researched the specific threat via the National Vulnerability Database (NVD) link provided in the console.

I checked the Remediation section, which advised upgrading the package to a more recent version.

<img width="300" height="500" alt="Lab 279_5" src="https://github.com/user-attachments/assets/c5ee69ad-6d24-4eba-9ad5-f307730284a6" />


## Task 3: Remediating and Verifying
To fix the issue, I performed the following steps:

1. Code Update: I navigated to the Lambda console and opened the get-request function.

<img width="700" height="7350" alt="Lab 279_6" src="https://github.com/user-attachments/assets/27069386-d401-4deb-a8d1-d63b815247cd" />


2. Version Control: I modified the requirements.txt file, changing requests==2.20.0 to requests to ensure the latest secure version would be used.

  <img width="700" height="350" alt="Lab 279_8" src="https://github.com/user-attachments/assets/ebeaf631-51f0-4b05-be13-cbd6897a8bfe" />

<img width="600" height="300" alt="Lab 279_9" src="https://github.com/user-attachments/assets/8853294b-8b5d-4c8a-b00c-0736d645999b" />

3. Deployment: I deployed the changes, which automatically triggered a re-scan by Inspector.

   <img width="700" height="350" alt="Lab 279_10" src="https://github.com/user-attachments/assets/88877ffa-5113-462c-84c5-6613e25a037b" />


4. Confirmation: I returned to the Inspector dashboard and confirmed the finding was moved to Closed status, verifying that the vulnerability was successfully resolved.

   <img width="700" height="300" alt="Lab 279_11" src="https://github.com/user-attachments/assets/3b0e4314-ad83-40bd-9854-646522e61faf" />


### Conclusion
By completing this lab, I successfully demonstrated how to use automated tools to maintain a strong security posture. I now know how to interpret Inspector's reports and apply quick remediations to keep cloud-native applications safe from known exploits.

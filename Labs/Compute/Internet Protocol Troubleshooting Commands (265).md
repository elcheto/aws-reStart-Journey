### Lab Summary: Mastering Network Troubleshooting in AWS (macOS)

Purpose of This LabThe objective of this lab was to transition into the role of a Network Administrator and gain hands-on experience with fundamental diagnostic tools. 
Using a macOS environment, I bridged the gap between abstract networking concepts (the OSI Model) and real-world troubleshooting. 
By connecting to a remote Amazon Linux instance, I practiced identifying connectivity gaps, latency issues, and service availability across multiple network layers.

## Steps Taken to Complete the Lab1. 
# 1. Establishing a Secure Connection (SSH)
Since I am using macOS, I used the native Terminal app to establish a secure shell (SSH) connection to the cloud instance.
- Credential Retrieval: I downloaded the .pem key file (private key) and recorded the instance's Public IP address from the lab console.
- Key Permissions: Before connecting, I restricted the key's permissions to comply with AWS security requirements:Bashchmod 400 labsuser.pem
- Remote Access: I initialized the connection using the SSH command:Bashssh -i labsuser.pem ec2-user@<public-ip>
<img width="602" height="470" alt="Screenshot 2026-04-08 at 21 28 15" src="https://github.com/user-attachments/assets/d8d87ed1-8689-4af7-859f-eef15c8f2136" />

<img width="603" height="211" alt="Screenshot 2026-04-08 at 21 29 00" src="https://github.com/user-attachments/assets/a091c93a-81c5-409b-a1e7-abdd30b2d299" />


# 2. Network Layer Diagnostics (Layer 3)

I used tools to verify if traffic could physically reach a destination and to map the path it took.Connectivity Check (ping): 

I verified basic reachability to external servers (e.g., 8.8.8.8). 
This confirmed that Security Groups and Network ACLs were correctly allowing ICMP traffic.Route Discovery (traceroute): I mapped the "hops" between my instance and a destination. This helped pinpoint whether latency was occurring within the AWS network or at an external ISP.

# 3. Transport Layer Analysis (Layer 4)
I shifted focus to how data is transported between specific ports and services.
Service Auditing (netstat): I used netstat -tp to see which ports were actively "listening" or had established connections. This is a critical step for security audits and verifying host-level connectivity.
Port Verification (telnet): After installing the telnet utility, I tested specific ports (like Port 80 for HTTP). 

This allowed me to distinguish between a "Connection Refused" (firewall/security group block) and a "Connection Timed Out" (routing or path issue).
<img width="605" height="224" alt="Screenshot 2026-04-08 at 21 29 37" src="https://github.com/user-attachments/assets/9956fea8-d872-4084-8474-b9bb85f41abf" />

# 4. Application Layer Testing (Layer 7)
Finally, I tested the end-to-end functionality of web services.
Data Transfer (curl): I used curl -vLo /dev/null to simulate a web request. 
By analyzing the verbose output, I could confirm if a web server was returning a successful 200 OK status without needing a full web browser.
<img width="592" height="706" alt="Screenshot 2026-04-08 at 21 30 29" src="https://github.com/user-attachments/assets/0746966e-9fae-4c97-b4e1-d8eeebc1e5ed" />

## Key Findings and OSI Mapping
This lab demonstrated how specific commands correlate directly to the OSI model to streamline troubleshooting.

Command OSI Layer Troubleshooting 
GoalPing / TracerouteLayer 3 (Network)Is the "wire" connected? Where is the lag?Netstat / TelnetLayer 4 (Transport)Is the specific port open and listening?CurlLayer 7 (Application)Is the website or API actually working?


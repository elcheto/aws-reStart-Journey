<b>Amazon Elastic Compute Cloud (Amazon EC2)<b> is a web service that provides resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers.

Amazon EC2's simple web service interface allows you to obtain and configure capacity with minimal friction. It provides you with complete control of your computing resources and lets you run on Amazon's proven computing environment. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change.

Amazon EC2 changes the economics of computing by allowing you to pay only for capacity that you actually use. Amazon EC2 provides developers the tools to build failure resilient applications and isolate themselves from common failure scenarios.

Topics covered

Launch a web server with termination protection enabled

Monitor Your EC2 instance
Modify the security group that your web server is using to allow HTTP access
Resize your Amazon EC2 instance to scale
Test termination protection
Terminate your EC2 instance

<img width="357" height="130" alt="Screenshot 2026-03-12 at 08 42 44" src="https://github.com/user-attachments/assets/9092d999-7fda-4e6f-8c4f-f239ad42d83f" />


<h2>Task 1: Launch an EC2 Instance</h2>
<p>In this task, I launched an Amazon EC2 instance with termination protection and set up a simple web server using a user data script.</p>

<h3>Open EC2</h3>
<ol>
  <li>Go to the AWS Management Console.</li>
  <li>Click <strong>Services</strong> and select <strong>EC2</strong>.</li>
  <li>In the left menu, click <strong>EC2 Dashboard</strong>.</li>
  <li>Click <strong>Launch instance</strong>.</li>
</ol>

<h3>Step 1: Name the Instance</h3>
<ol>
  <li>In <strong>Name and tags</strong>, enter: <strong>Web Server</strong>.</li>
</ol>

<h3>Step 2: Choose an AMI</h3>
<ol>
  <li>In <strong>Application and OS Images</strong>, keep the default: <strong>Amazon Linux 2023</strong>.</li>
</ol>

<h3>Step 3: Choose Instance Type</h3>
<ol>
  <li>Select <strong>t3.micro</strong> (2 vCPU, 1 GiB memory).</li>
</ol>

<h3>Step 4: Key Pair</h3>
<ol>
  <li>Under <strong>Key pair (login)</strong>, choose <strong>Proceed without a key pair</strong>.</li>
</ol>

<h3>Step 5: Network Settings</h3>
<ol>
  <li>Click <strong>Edit</strong> in Network settings.</li>
  <li>For <strong>VPC</strong>, select <strong>Lab VPC</strong>.</li>
  <li>Create a security group:</li>
  <ul>
    <li><strong>Name:</strong> Web Server security group</li>
    <li><strong>Description:</strong> Security group for my web server</li>
  </ul>
  <li>Remove the default <strong>SSH</strong> inbound rule.</li>
</ol>

<h3>Step 6: Storage</h3>
<ol>
  <li>Keep the default storage (8 GiB).</li>
</ol>

<h3>Step 7: Advanced Details</h3>
<ol>
  <li>Open <strong>Advanced details</strong>.</li>
  <li>Set <strong>Termination protection</strong> to <strong>Enable</strong>.</li>
  <li>Paste this script into <strong>User data</strong>:</li>
</ol>

<pre>
#!/bin/bash
yum -y install httpd
systemctl enable httpd
systemctl start httpd
echo '&lt;html&gt;&lt;h1&gt;Hello From Your Web Server!&lt;/h1&gt;&lt;/html&gt;' &gt; /var/www/html/index.html
</pre>

<p>This script installs Apache, starts the web server, and creates a simple web page.</p>

<h3>Step 8: Launch the Instance</h3>
<ol>
  <li>Click <strong>Launch instance</strong>.</li>
  <li>Click <strong>View all instances</strong>.</li>
  <li>Wait until the instance status shows:</li>
  <ul>
    <li><strong>Instance State:</strong> Running</li>
    <li><strong>Status Checks:</strong> 2/2 checks passed</li>
  </ul>
</ol>

<p>You can now see your instance details, including the public DNS.</p>

<img width="500" height="300" alt="Screenshot 2026-03-12 at 08 54 30" src="https://github.com/user-attachments/assets/554a3fe1-27a6-4b6c-9096-6737f862d9d4" />

I need to add info here

<img width="500" height="350" alt="Screenshot 2026-03-12 at 09 00 28" src="https://github.com/user-attachments/assets/b525855c-6f22-459c-8baa-3aa09bab6bf8" />

I am not currently able to access my web server because the security group is not permitting inbound traffic on port 80, which is used for HTTP web requests.



<h2>Enable Access to the Web Server</h2>

<p>After launching the EC2 instance, I allow web traffic so the server page could be opened in a browser.</p>

  <li>Returned to the <strong>EC2 Management Console</strong>.</li>
  <li>In the left menu, opened <strong>Security Groups</strong> under <strong>Network & Security</strong>.</li>
  <li>Selected <strong>Web Server security group</strong>.</li>
  <li>Opened the <strong>Inbound rules</strong> tab.</li>
  <li>Clicked <strong>Edit inbound rules</strong>.</li>
  <li>Clicked <strong>Add rule</strong> and set:</li>
</ol>

<ul>
  <li><strong>Type:</strong> HTTP</li>
  <li><strong>Source:</strong> Anywhere-IPv4</li>
</ul>

<ol start="7">
  <li>Clicked <strong>Save rules</strong>.</li>
  <li>Went back to the browser tab with the web server and refreshed the page.</li>
</ol>

<p>The page now shows: <strong>Hello From Your Web Server!</strong></p>

<img width="700" height="310" alt="Screenshot 2026-03-12 at 09 10 30" src="https://github.com/user-attachments/assets/0e8fa945-5de5-4792-9e1d-d42e51633633" />

<h2>Resize the EC2 Instance</h2>

<p>I first stopped the <strong>Web Server</strong> instance from the EC2 console. After the instance status showed <strong>stopped</strong>, I changed the instance type from <strong>t3.micro</strong> to <strong>t3.small</strong>.</p>

<p>Next, I opened <strong>Volumes</strong> under Elastic Block Store and modified the disk size from <strong>8 GiB</strong> to <strong>10 GiB</strong>.</p>

<p>Finally, I went back to <strong>Instances</strong> and started the Web Server again. The instance now runs with more memory and more disk space.</p>

<img width="500" height="280" alt="Screenshot 2026-03-12 at 11 13 07" src="https://github.com/user-attachments/assets/b4ef9efe-1705-4c9b-8217-7a33697c76e1" />


<h2>Test Termination Protection</h2>

<p>I opened <strong>Instances</strong> in the EC2 console and tried to terminate the <strong>Web Server</strong> instance. The termination failed because termination protection was enabled.</p>

<img width="500" height="260" alt="Screenshot 2026-03-12 at 11 27 50" src="https://github.com/user-attachments/assets/97094ffb-f836-4e1a-9c0f-c3f0dcaec322" />

<p>I then went to <strong>Actions → Instance settings → Change termination protection</strong> and disabled it.</p>

<p>After saving the change, I terminated the instance successfully using <strong>Instance state → Terminate instance</strong>.</p>

<img width="500" height="260" alt="Screenshot 2026-03-12 at 11 34 39" src="https://github.com/user-attachments/assets/65b5f128-887a-433c-8d27-1dd1f1a562e4" />

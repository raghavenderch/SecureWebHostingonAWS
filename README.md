<h1>Secure Web Hosting on AWS</h1>

<a>In this project I have built a simple and secure serverless web application using various AWS services.</a>

<h3>Services Used</h3>
<ul>
  <li>S3 - Stores the static website files</li>
  <li>AWS WAF - set ACLs for protection against common web attacks</li>
  <li>CloudFront - Distribute content globally through CDN</li>
  <li>IAM - assign least-privilege permissions for access control</li>
  <li>CloudWatch & CloudTrail - Monitor logs, user activity and detect anomalies</li>
</ul>

<h3>Architecture Diagram</h3>
<img width="600" height="auto" alt="Architecture_Diagram" src="https://github.com/user-attachments/assets/953f54de-b8ec-4330-a751-592e41f3f5e1" />

<h2>Project Implementation</h2> 

<h4>1. Created the S3 Bucket</h4> 

<p> Created an Amazon S3 bucket to store the static website files (index.html, web.css and web.js)</p>

<img width="500" height="auto" alt="image" src="https://github.com/user-attachments/assets/51a5b886-b3f9-424b-9ce7-709ada0894c4" />
<img width="500" height="auto" alt="image" src="https://github.com/user-attachments/assets/a0b0435d-2368-4f62-9bba-4bbaacce3af9" />

<h4>2. Configured CloudFront</h4>
<p>Created a CloudFront distribution with Origin Access Control to securely access S3 bucket blocking the public access to the bucket</p>
<img width="500" height="auto" alt="image" src="https://github.com/user-attachments/assets/ccc7c74b-1235-4007-9a8c-2ecc61219979" />
<img width="500" height="auto" alt="image" src="https://github.com/user-attachments/assets/d6a2e3d8-d212-46d7-902b-3013faf1ac46" />

<h4>3. Configured AWS WAF</h4>
<p>Created a Web ACL in AWS WAF and associated it with the CloudFront distribution to inspect and filter incoming web requests. The configuration was validated by sending a test SQL injection (SQLi) string to the CloudFront URL and verifying that the request was blocked.</p>
<img width="500" height="auto" alt="image" src="https://github.com/user-attachments/assets/ae2c2b2a-290b-4575-9c97-bae561fa6036" />
<img width="500" height="auto" alt="image" src="https://github.com/user-attachments/assets/6dcf0abc-dca2-45b6-8c0c-21164cc52b0f" />
<p>CloudFront URL without SQLi string</p>
<img width="500" height="auto" alt="image" src="https://github.com/user-attachments/assets/2ac0b318-2dd0-4162-acee-240f33b4f4a2" />
<br>
<p>CloudFront URL with SQLi string</p>
<img width="500" height="auto" alt="image" src="https://github.com/user-attachments/assets/4d2b80db-3d3b-457b-af14-8d14a4c666af" />

<h4>4. Created an IAM User</h4>
<p>Created a dedicated IAM user with limited permissions instead of using the AWS root account. The user is granted the required permissions for S3, CloudFront, WAF while limited access (read-only permissions) to IAM </p>
<img width="500" height="auto" alt="image" src="https://github.com/user-attachments/assets/ecd40c33-222c-4eb6-90db-a0dba9110dbf" />

<h4>5. Configured CloudWatch and CloudTrail</h4>
<p>Configured Amazon CloudWatch to monitor the CloudFront distribution and provide visibility into website traffic and operational metrics. Enabled AWS CloudTrail to record API activity and provide an audit trail for actions performed on AWS resources.</p>

<h3>What I Learned</h3>
<p>Through this project, I gained hands-on experience with:</p>
<ul>
  <li>Deploying a static website securely using Amazon S3</li>
  <li>Configuring CloudFront distributions with Origin Access Control</li>
  <li>Implementing AWS WAF rules for protection against web attacks</li>
  <li>Implementing least-privilege principle by creating a dedicated IAM user instead of using the AWS root account</li>
  <li>Learned how CloudWatch and CloudTrail provide monitoring and auditing capabilities within AWS</li>
</ul>

<h2>Cleanup</h2>
<p>
    After completing the implementation and validation, the AWS resources were removed to prevent unnecessary ongoing costs.
</p>

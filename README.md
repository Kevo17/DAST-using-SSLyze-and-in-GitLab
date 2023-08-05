<h1>DAST using SSLyze and in GitLab</h1>


<h2>Description</h2>
This lab focuses on utilizing SSLyze, a powerful Dynamic Application Security Testing (DAST) tool for analyzing SSL/TLS configurations and vulnerabilities, within the GitLab platform. SSLyze enables you to assess the security of your web applications by scanning for SSL/TLS-related weaknesses and potential vulnerabilities.

During this hands-on lab, participants will gain practical experience in integrating SSLyze into the GitLab pipeline to enhance the security of their web applications.
<br />


<h2>Languages and Utilities Used</h2>

- <b>SSLyze</b>
- <b>JSON</b>
- <b>GitLab</b>

<h2>Environments Used </h2>

- <b>Windows 11</b>
- <b>Linux</b> 

<h2>Program walk-through:</h2>

Let’s install SSlyze to perform Dynamic analysis: <br/>
```
pip3 install sslyze==5.0.3
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/2MyMQxh.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

We have successfully installed SSLyze scanner, let’s explore the functionality it provides us: <br/>
```
sslyze --help
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/qVDLBbn.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s run sslyze with the following options: <br/>
```
sslyze --json_out sslyze-output.json prod-rcgsg0ei.lab.practical-devsecops.training:443
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/e2fh6Q2.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

We can check the scan output using the following command: <br/>
```
cat sslyze-output.json
```
<br/>
 
<p align="center">
<img src="https://i.imgur.com/aElBSB4.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Let’s run the scan in GitLab in the YAML configuration file: <br/>
```
- docker pull hysnsec/sslyze
```
```
- docker run --rm -v $(pwd):/tmp hysnsec/sslyze <YOUR HOST>:443 --json_out /tmp/sslyze-output.json
```
<p align="center">
<img src="https://i.imgur.com/VwbLxft.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

Here is the result of this job: <br/>
<p align="center">
<img src="https://i.imgur.com/yCPebnu.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

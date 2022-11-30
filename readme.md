# 2420_AS2
<h2>STEP ONE: CREATING DO INFRASTRUCTURE</h2>

<h3>Step 1: Open Digital Ocean and create a new project</h3>
<h3>Step 2: Click on Networking and then VPC</h3>
<img src="Screenshots/1.png" width="800" />
<h3>Step 3: Choose your closest data centre, let DO generate an IP range for you, Name your VPC and then click on CREATE VPC NETWORK</h3>
<img src="Screenshots/2.png" width="800" />

<h3>Step 4: Go back to your project and Click on Get Started with a Droplet</h3>

<h3>Step 5: Select Ubuntu, choose your plan, Select the same data centre as your VPC, Select the VPC you just made, create two droplets and give them names, and then click Create Droplet</h3>
<img src="Screenshots/3.png" width="800" />
<img src="Screenshots/4.png" width="800" />
<img src="Screenshots/5.png" width="800" />


<h3>Step 6: Go back to Networking Section again and Click on Load Balancers</h3>
<img src="Screenshots/6.png" width="800" />

<h3>Step 7: Click on Create Load Balancers</h3>
<h3>Step 8: Choose the same data centre as your VPC and Select the VPC you created before</h3>
<img src="Screenshots/7.png" width="800" />

<h3>Step 9: Under Connect Droplets, select the two droplets you created before, and leave the other defaults as is. Then Click Create Load Balancer</h3>
<img src="Screenshots/8.png" width="800" />

<h3>Step 10: Now go back to Networking and Click on Firewalls and then Create Firewall</h3>
<img src="Screenshots/9.png" width="800" />

<h3>Step 11: Give it a suitable name and add HTTP under Inbound Rules. Under Inbound Rules, Delete default settings and Add your Load Balancer</h3>
<img src="Screenshots/10.png" width="800" />

<h3>Step 12: Under apply to Droplets, add the two droplets you created before and then  select Create Firewall</h3>
<img src="Screenshots/11.png" width="800" />

<b><h2>Your DO infrastructure is Complete</h2></b>


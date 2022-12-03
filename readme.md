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

<h2>STEP TWO: CREATING REGULAR USERS IN DROPLETS</h2>
<h3>Step 1: SSH as root into one of your droplet</h3>
<h3>Step 2: Create a new user</h3> 
<pre><code>useradd -ms /bin/bash USERNAME</code></pre>
<img src="Screenshots_S2/1.png" width="800" />
<h3>Step 3: Give this user root access</h3> 
<pre><code>usermod -aG sudo USERNAME</code></pre>
<img src="Screenshots_S2/2.png" width="800" />
<h3>Step 4: Give this user a password</h3> 
<pre><code>passwd USERNAME</code></pre>
<img src="Screenshots_S2/3.png" width="800" />
<h3>Step 5: Run this so only the user can login via ssh on your droplet</h3> 
<pre><code>rsync --archive --chown=USERNAME:USERNAME ~/.ssh /home/USERNAME</code></pre>
Now login to your regular user and run
<pre><code>sudo vi /etc/ssh/sshd_config</code></pre>
<img src="Screenshots_S2/5.png" width="800" />
Change PermitRootLogin from yes to no
<img src="Screenshots_S2/6.png" width="800" />
<h3>Step 6: Repeat the same steps with other droplet with same username and password for convienence</h3> 
<h2>Step Two is complete</h2>

<h2>STEP THREE: INSTALLING CADDY</h2>
<h3>Step:1Use this command to download the installation files for Caddy</h3>
<pre><code>wget https://github.com/caddyserver/caddy/releases/download/v2.6.2/caddy_2.6.2_linux_amd64.tar.gz</code></pre>
<img src="Screenshots_S2/7.png" width="800" />
<h3>This will unarchive the installation files</h3>
<pre><code>tar xvf caddy_2.6.2_linux_amd64.tar.gz</code></pre>
<img src="Screenshots_S2/11.png" width="800" />
<h3>Change Caddy file permission to root</h3>
<pre><code>sudo chown root: caddy</code></pre>
<img src="Screenshots_S2/12.png" width="800" />
<h3>copy the Caddy file to /usr/bin/</h3>
<pre><code>    sudo cp caddy /usr/bin/</code></pre>
<img src="Screenshots_S2/13.png" width="800" />
<h3>Update</h3>
<pre><code>Sudo apt update && sudo apt upgrade</code></pre>
<h2>You successfully install Caddy server</h2>

<h2>STEP FOUR: SETTING UP WSL</h2>
<h3>Step 1:Make a new directory and then make two directories named html and src inside this directory.</h3>
<img src="Screenshots_S2/8.png" width="800" />
<h3>Step 2: Create a html file index.html inside the html folder and code it with HTML so it outputs "Hello World!"</h3>
<img src="Screenshots_S2/9.png" width="800" />
<h3>Step 3: Go to https://volta.sh/ and install node using volta</h3>
<h3>Step 4: Cd into src folder and run the following commands</h3>
<pre><code>npm init</code></pre>
<pre><code>npm i fastify</code></pre>
<h3>Step 5: Edit your index.js file and put the following code in it</h3>
<pre><code>// Require the framework and instantiate it
const fastify = require('fastify')({ logger: true })

// Declare a route
fastify.get('/', async (request, reply) => {
  return { hello: 'Server x' }
})

// Run the server!
const start = async () => {
  try {
    await fastify.listen({ port: 3000 })
  } catch (err) {
    fastify.log.error(err)
    process.exit(1)
  }
}
start()</code></pre>
<h3>This is a code for a basic Web server</h3>
<h3>Step 6: Run your server to test it</h3>
<pre><code>node index.js</code></pre>
<img src="Screenshots_S2/10.png" width="800" />











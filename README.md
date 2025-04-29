# Node.Js-node
Node.js-Node
et up Node.js inside WSL2 (Ubuntu) 0. Quick: Make Sure You Have WSL2 Installed If not yet installed:

On Windows PowerShell (as Admin): wsl --install ✅ It will install WSL and Ubuntu by default.

Then reboot your system

Update Ubuntu inside WSL2 Open Ubuntu (WSL2 Terminal):
bash Copy Edit

Update package list and packages
sudo apt update && sudo apt upgrade -y 2. Install Curl and Required Tools bash Copy Edit sudo apt install -y curl build-essential gcc g++ make (build-essential installs C compiler tools, useful later for Node modules that need compiling.)

Install Node.js (Latest LTS) Use NodeSource, the cleanest method:
bash Copy Edit

Download Node.js setup script
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -

Install Node.js
sudo apt install -y nodejs ✅ Confirm installation:

bash Copy Edit node -v npm -v You should see something like:

Copy Edit v20.10.0 9.6.7 (depends on latest version)

Create Your Node.js App bash Copy Edit
Go to your home directory
cd ~

Make a project folder
mkdir my-node-app cd my-node-app 5. Initialize Node.js Project bash Copy Edit

Initialize a new Node.js project
npm init -y This will create a package.json file automatically.

Create Your Server File bash Copy Edit
Create app.js
nano app.js Paste this code:

javascript Copy Edit // app.js

const http = require('http');

// Create server const server = http.createServer((req, res) => { res.statusCode = 200; res.setHeader('Content-Type', 'text/plain'); res.end('Hello World from Node.js inside WSL2!\n'); });

// Define PORT const PORT = 3000;

// Start server server.listen(PORT, () => { console.log(Server running at http://localhost:${PORT}/); }); Save the file (CTRL+O, Enter, CTRL+X if using nano).

Run Your Server bash Copy Edit
Start your app
node app.js ✅ You should see:

arduino Copy Edit Server running at http://localhost:3000/ 8. Access Your App from Windows Browser Open your Windows Browser (Chrome, Edge, etc.) and go to:

➡️ http://localhost:3000

You should see:

csharp Copy Edit Hello World from Node.js inside WSL2! 🛠 Full Automation Script If you want everything above packed into one big script (except editing app.js manually):

bash Copy Edit sudo apt update && sudo apt upgrade -y &&
sudo apt install -y curl build-essential gcc g++ make &&
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash - &&
sudo apt install -y nodejs &&
mkdir -p ~/my-node-app && cd ~/my-node-app &&
npm init -y &&
echo "const http = require('http'); const server = http.createServer((req, res) => { res.statusCode = 200; res.setHeader('Content-Type', 'text/plain'); res.end('Hello World from Node.js inside WSL2!\n'); }); const PORT = 3000; server.listen(PORT, () => { console.log(`Server running at http://localhost:\${PORT}/\`); });" > app.js &&
node app.js ⚡ Bonus: Install nodemon (optional) Auto-restart server when files change:

bash Copy Edit npm install -g nodemon

Then run
nodemon app.js 🚀 Diagram of Steps pgsql Copy Edit WSL2 (Ubuntu) ➔ Update packages ➔ Install Node.js ➔ Create Project ➔ Write Server ➔ Run Server ➔ Access from Browser 📦 Important Note In WSL2, localhost automatically works between Windows and WSL2! (Unlike WSL1, no complex IPs needed.)

If you have a firewall, just make sure port 3000 is open for local connections.

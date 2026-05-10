Technical Deployment Guide: Cognitive-Asset-Zero
Phase 1: Hardening the Foundation (Environment Prep)
Before installing the "brain," you must prepare the chassis. An unoptimized VPS is technical debt waiting to happen.

Bash
# Update system packages to the latest stable versions
sudo apt update && sudo apt upgrade -y

# Install essential dependencies for Python environments and version control
sudo apt install -y python3-pip python3-venv git curl pipx

# Ensure pipx is in your PATH for global CLI tool access
pipx ensurepath
source ~/.bashrc
Phase 2: Installing the Engine (Aider & OpenRouter)
We use Aider because it provides atomic Git integration—the difference between a disorganized workshop and a factory line where every bolt is tracked.

Bash
# Install Aider globally via pipx
pipx install aider-chat

# Verify installation
aider --version
Phase 3: The Trinity of Memory (File Initialization)
Miliarders do not operate without a ledger. We will now initialize the "Trinity" files that serve as the persistent logic layer of your asset.

Bash
# Navigate to your project directory (The Cognitive Asset Sector)
mkdir -p ~/COGNITIVE-ASSET-ZERO
cd ~/COGNITIVE-ASSET-ZERO

# Initialize the Trinity files
touch soul.md memory.md skills.md

# Create the Global Soul directory for centralized session tracking
mkdir -p /home/debian/MASTER_MEMORY
Phase 4: Security & Credential Isolation (The Vault)
Never hardcode your credentials. Your API keys must be isolated from your logic files to prevent catastrophic leakage.

Bash
# Create the environment configuration file
touch .env

# Add your OpenRouter API Key to the .env file
# Replace 'your_key_here' with your actual OpenRouter token
echo "OPENROUTER_API_KEY=your_key_here" >> .env

# Configure the 'Ignore' protocol to ensure the Vault stays off GitHub
cat <<EOF > .gitignore
.env
.aider*
*.log
__pycache__/
EOF
Phase 5: Version Control Integration (The Black Box)
In a professional FDE workflow, every change must be auditable.

Bash
# Initialize Git to track all architectural evolutions
git init
git add .
git commit -m "Initial Deployment: Cognitive-Asset-Zero Infrastructure"
Phase 6: Ignition (System Launch)
Launch the orchestrator by mounting the Trinity files into the active context. This command links your VPS hardware to the global LLM intelligence layer via OpenRouter.

Bash
aider --model openrouter/anthropic/claude-3.5-sonnet \
--no-show-model-warnings \
--chat-history-file /home/debian/MASTER_MEMORY/global_soul.md \
--read soul.md \
--read memory.md \
--read skills.md
Strategic Analogy: The Special Operations Command
Think of this setup as a high-altitude surveillance drone.

The VPS is the airframe (Physical Hardware).

Aider is the avionics system (Control Logic).

OpenRouter is the satellite uplink (Intelligence Feed).

The Trinity (.md files) is the mission data (Persistent Memory).

If the satellite uplink (LLM) fails, you swap providers mid-flight. The drone stays in the air because the mission data—your Soul, Memory, and Skills—resides in the airframe, not the satellite.

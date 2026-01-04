## Beginner Guide: Running OM1 on OctaSpace (Step-by-Step)

This guide walks you through setting up and running **OM1** using **OctaSpace**. No prior server experience needed — just patience.

---

## What You Need Before Starting

Make sure you have the following:

* ✅ **OctaSpace account**
* ✅ **@openmind_agi account**
* ✅ **OM1 API key**
* ✅ **$1 worth of OCTA tokens**
* ✅ **$2 API credit on OpenMind**
* ✅ **Patience** (first setup always takes time)

---

## STEP 1: Rent a Machine on OctaSpace

### 1. Open the OctaSpace marketplace

Visit:
👉 **marketplace.octa.computer/compute**
(remove the space in the link)

### 2. Sign in to your OctaSpace account

### 3. Fund your wallet

* Buy **OCTA tokens** from **MEXC**
* Transfer them to your OctaSpace wallet
* **10 OCTA tokens is more than enough**

### 4. Choose a machine

* Go to **Compute**
* On the **right-hand side**, use filters:

  * **System:** Ubuntu 22.04
  * **GPU:** RTX (choose a **US-based** machine)

### 5. Configure the machine

* Click **Configure**
* Go to **Apps**
* Select: **PyTorch JupyterLab**
  (it runs on Ubuntu 22.04)
* Set **Disk Size:** at least **40GB**
* Click **Deploy**

---

## STEP 2: Access Your Server

### 1. Wait for setup

* Status will change to **“Service Configured”**
* This may take a few minutes

### 2. Open the terminal

* Click the machine
* Select **Access Web SSH**

### 3. Test if the server is running

Run this command:

```bash
uptime
```

✅ If you see time-related output, your server is ready.

---

## STEP 3: Install Basic Dependencies

Copy **everything below**, then:

* Right-click inside the terminal
* Select **Paste**
* Press **Enter**

```bash
apt-get update
apt-get install -y git curl build-essential python3-dev portaudio19-dev ffmpeg
```

---

## STEP 4: Install `uv` (Python Manager)

Paste and run:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
source $HOME/.cargo/env
```

---

## STEP 5: Clone the OM1 Repository

Paste and run:

```bash
git clone https://github.com/OpenMind/OM1.git
cd OM1
git submodule update --init
uv venv
```

---

## STEP 6: Create Your OM1 API Key

### 1. Go to the API portal

👉 [http://portal.openmind.org](http://portal.openmind.org)

### 2. Sign in

⚠️ Use the **same account** you used on the Fabric platform.

### 3. Create an API key

* Copy the API key
* Buy **$2 API credits**
  (required for requests to work)

---

**Step #: Add a security warning (strongly recommended)**
## Security Notice

⚠️ Never commit your `.env` file or API keys to GitHub.  
Always keep API keys private and local to your server.


## STEP 7: Add Your API Key to the Project

In the terminal, run this command:

```bash
echo "OM_API_KEY=om1_live_YOUR_KEY_HERE" > .env
```

### Important:

* Replace `om1_live_YOUR_KEY_HERE` with **your actual API key**

Example:

```bash
echo "OM_API_KEY=yournewapikey" > .env
```

Paste → Enter.

---

## STEP 8: Run OM1 🎉

Paste and run:

```bash
uv run src/run.py spot
```

### What happens next:

* It will download required modules
* This may take a few minutes

### Successful output looks like:

```text
INFO:root:Loading vision model...
Object Detector INPUT
AVAILABLE ACTIONS: move, speak, emotion
```

---

## Notes & Tips

* If it asks for more API credits, that’s normal (Stripe things 😅)
* Let it run for 3–5 hours, then stop the instance
* Badge approval takes time — the team reviews activity manually
* Always use the same account across Fabric & OpenMind portal



# Blockchain_Based_Secured_Electronic_Voting_Machine

This repository presents our 3rd year EEE (Electrical and Electronics Engineering) project, which introduces a secure and transparent electronic voting system using blockchain technology. It aims to address vulnerabilities in traditional voting by using cryptographic fingerprint authentication and Ethereum smart contracts to ensure real-time, immutable,and anonymous vote recording.

## 🧠 Project Summary 

The system integrates a fingerprint scanner, LCD, physical voting buttons, and a Raspberry Pi with blockchain protocols. Fingerprints are hashed and verified before votes are encrypted and transmitted to the Ethereum blockchain (via Ganache) in real-time. This ensures data cannot be tampered with and eliminates single points of failure — improving both resilience and trust in the voting process.

## 🔧 How to Set Up and Run the Project

### Step 1: Hardware Requirements
- Raspberry Pi (Model 3 or 4 preferred)
- 16x2 LCD with I2C module (e.g., JHD 162A)
- Fingerprint sensor via UART TX/RX (e.g., ZA650_M5)
- 3 voting buttons and 1 confirm button
- Pull-up or pull-down resistors based on GPIO setup  
⚠️ *If you change any GPIOs components or connections, update the corresponding pin numbers and logic in the code.*

### Step 2: Clone the Project Repository
```bash
git clone https://github.com/yagyashahi7/Secured_Blockchain_Based-Electronic_Voting_System
cd electronic_voting_machine
```

### Step 3: Set Up Ganache for Ethereum Blockchain
1. Download and launch **Ganache** on your PC.
2. Create a new workspace.
3. Set the HTTP RPC server to `All Interfaces` (default: `http://127.0.0.1:7545`).
4. Keep Ganache running in the background throughout the process.

### Step 4: Compile and Deploy Smart Contract
```bash
truffle compile
truffle migrate --reset
```
Once deployed, copy the contract address and paste it into:
- `evm_v2.py` (backend Python script)
- `app.js` (frontend JS file)

### Step 5: Prepare Raspberry Pi Python Environment
1. Connect to Raspberry Pi using RealVNC or Putty.
2. Install dependencies and create a virtual environment:
```bash
sudo apt update
sudo apt install python3-pip
python3 -m venv myenv
source myenv/bin/activate
```
3. Install required Python libraries:
```bash
pip install -r requirements.txt
```
Ensure the `requirements.txt` includes packages like:
```
web3
RPI.GPIO
pyserial
pandas
```

### Step 6: Enroll Fingerprints and Run Voting
1. Run fingerprint enrollment script:
```bash
python3 enroll_fingerprint.py
```
2. Run the main voting program:
```bash
python3 evm_v2.py
```
- Users authenticate using fingerprint.
- Press buttons to cast vote.
- Vote is encrypted and stored on the blockchain.

### Step 7: View Results via Browser
Open the `UI.html` file in a browser to view results and blockchain-submitted votes.

## 📁 Project Structure
```
Blockchain-Based-EVM/
├── contracts/ <br>
├── migrations/<br>
├── UI.html<br>
├── evm_v2.py<br>
├── enroll_fingerprint.py<br>
├── app.js<br>
├── requirements.txt<br>
├── truffle-config.js<br>
└── README.md<br>
```

## ✅ Key Features
- Blockchain-backed, tamper-proof voting
- Fingerprint authentication for voter validation
- Real-time Ethereum smart contract integration
- Web-based UI for result display
- Raspberry Pi hardware control

## 👨‍💻 Maintainer
This version of the project is maintained by **Yagya Bahadur Shahi** as part of our team submission for our third-year engineering course.  
GitHub: [https://github.com/yagyashahi7](https://github.com/yagyashahi7)

## 📚 References
- https://trufflesuite.com/ganache/
- https://web3py.readthedocs.io/
- https://ethereum.org/
- https://www.raspberrypi.com/documentation/

## 📝 License
Consider adding an open-source license such as MIT by including a LICENSE file or using [https://choosealicense.com](https://choosealicense.com).

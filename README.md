# 🚀 Hyperledger Fabric Asset Transfer Project

This project demonstrates setting up a **Hyperledger Fabric test network** and running a simple **Asset Transfer API Server** using **Node.js**.

---

## 📂 Project Structure
```

HFL-Project-Asset-Transfer/
├── fabric-samples/       # Hyperledger Fabric sample network
│   └── test-network/     # Test network scripts
└── api-server/           # Express.js server for Asset Transfer
└── chaincode/            # Chaincode Written in Go

```

---

## ⚙️ Prerequisites
- **Git**
- **cURL / wget**
- **Docker & Docker Compose**
- **Node.js (>= 14.x) & npm**
- **Go (for chaincode development)**

---

## 🛠️ Setup Instructions

### 1️⃣ Clone Fabric Samples
```bash
# location: HFL-Project-Asset-Transfer/
git clone https://github.com/hyperledger/fabric-samples.git
cd fabric-samples
````

### 2️⃣ Install Fabric Binaries

```bash
git checkout release-2.2
# use sudo if permission issues occur
curl -sSL https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/install-fabric.sh | bash -s
export PATH=$PATH:$PWD/bin

# verify installation
peer version
```

### 3️⃣ Start the Test Network

```bash
cd test-network

# bring up network and create a channel
./network.sh up createChannel

# deploy the chaincode
./network.sh deployCC -ccn asset -ccp ../../chaincode -ccl go
```

---

## 🌐 Run the API Server

```bash
# location: HLF-Project-Asset-Transfer/api-server
cd ../../api-server

npm install express @hyperledger/fabric-gateway @grpc/grpc-js

# start server
node server.js
```

---

## 🛑 Shutting Down the Network

```bash
# location: HLF-Project-Asset-Transfer/fabric-samples/test-network
./network.sh down
```

---

## ✅ Summary

* Fabric binaries & Docker containers set up using `install-fabric.sh`
* Test network launched with a single channel
* Asset Transfer chaincode deployed
* Node.js API server connected to the Fabric Gateway

---

## 📖 References

* [Hyperledger Fabric Documentation](https://hyperledger-fabric.readthedocs.io/)
* [Fabric Samples GitHub](https://github.com/hyperledger/fabric-samples)


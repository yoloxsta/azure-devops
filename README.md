# azure-devops

- https://ibrahims.medium.com/azure-devops-basic-a5825154df8d (day-01-basic)
- https://ibrahims.medium.com/azure-boards-devops-05413ae466c8 (day-02-azure board)
- https://allangraves.medium.com/getting-started-with-azure-devops-repos-3580c97467aa (Repo)
- https://ibrahims.medium.com/azure-pipeline-devops-b6fe8d8505ba (pipeline)
- https://ibrahims.medium.com/azure-artifacts-devops-6298adae0ce5 (Artifacts)
- https://ibrahims.medium.com/azure-release-pipelines-devops-c23bd4c43066 (Azure Release Pipelines)

## Azure agent
```
Step 1 — Install venv support
sudo apt update
sudo apt install python3-venv -y

Step 2 — Create a virtual environment
cd ~/myagent
python3 -m venv azcli-venv

Step 3 — Activate the virtual environment
source azcli-venv/bin/activate


Your shell prompt should now show (azcli-venv) in front.

Step 4 — Upgrade pip inside the venv
pip install --upgrade pip

Step 5 — Install Azure CLI
pip install azure-cli

Step 6 — Verify installation
az version

For a service principal login (recommended for pipelines):
az login --service-principal -u <APP_ID> -p <PASSWORD_OR_CERT> --tenant <TENANT_ID>


#If you don’t want to source it every time, you can add an alias in your ~/.bashrc:
echo "alias azcli='source ~/myagent/azcli-venv/bin/activate'" >> ~/.bashrc
source ~/.bashrc

#Then anytime you want to use Azure CLI, just run:

azcli
az version
```
## Install Azure CLI system-wide on the agent VM
```
You must NOT rely on venv for Azure DevOps agents

 curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
 sudo ./svc.sh stop
 cd myagent/
 sudo ./svc.sh stop
 sudo ./svc.sh start
 sudo -u ubuntu az version
```
# Azure Blob Storage Tiers Explained

This README explains the **Hot, Cool, and Archive tiers** in Azure Blob Storage, including cost, use cases, examples, and analogies.

---

## 1️⃣ Hot Tier 🌞

- **Purpose:** Data you access frequently.  
- **Cost:** Highest storage cost, lowest access cost.  
- **Use case:** Active apps, logs, database backups you read often.  

**Example:**  
You have a web app storing user profile images or recent files. Users access them multiple times a day.  

- **Storage cost:** Higher per GB  
- **Access cost:** Minimal  

**Analogy:** Hot tier = your desktop files you use every day.

---

## 2️⃣ Cool Tier ❄️

- **Purpose:** Data you access less frequently (maybe once a month).  
- **Cost:** Lower storage cost than Hot, higher access cost.  
- **Use case:** Backups, old logs, archived project files that you rarely read.  

**Example:**  
Your company stores last year’s financial reports or logs from 3–6 months ago. You rarely need to read them, but they must be available if needed.  

- **Storage cost:** Cheaper than Hot  
- **Access cost:** Higher if you read frequently  

**Analogy:** Cool tier = files in an external hard drive you check monthly.

---

## 3️⃣ Archive Tier 🗄️

- **Purpose:** Data you rarely access (maybe once a year).  
- **Cost:** Cheapest storage cost, highest access cost and retrieval time.  
- **Use case:** Compliance, old backups, old audit logs, rarely-read data.  

**Example:**  
Your company must store tax records for 7 years. Nobody reads them until audit time.  

- **Storage cost:** Very cheap  
- **Access cost:** Very high (retrieval can take hours)  

**Analogy:** Archive tier = warehouse storage for old boxes. You pay little, but it takes time to get them.

---

## 🔹 Comparison Table

| Tier    | Storage cost | Access cost | Latency   | Example                                |
|--------|--------------|------------|-----------|----------------------------------------|
| Hot    | High         | Low        | Immediate | Active user files, current logs        |
| Cool   | Medium       | Medium     | Immediate | 6-month-old backups, old logs          |
| Archive| Very low     | Very high  | Hours     | 7-year tax records, compliance backups |

---

## 💡 Pro Tips

- **Use lifecycle rules** to automatically move data:
  - Hot → Cool → Archive based on age  
- **Choose tier based on access pattern** to optimize costs.

## Azure Storage Services
<img width="1536" height="1024" alt="3f3113ae-8606-4760-9df0-6a5371a8b2c9" src="https://github.com/user-attachments/assets/a0fa82fc-fd36-4fb5-bc23-32336946e42a" />

## AKS
```
az aks get-credentials \
  --resource-group rg-name \
  --name cluster-name

```


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

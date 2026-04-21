Aim

To deploy and run a web application using Microsoft Azure App Service.

Requirements
Azure Student Account
Azure CLI installed
VS Code (optional)
Basic web app (Python / Node.js / HTML)
Theory

Azure App Service is a cloud platform provided by Microsoft Azure that allows developers to host web applications without managing servers. It supports automatic scaling, deployment, and monitoring.

Procedure
1. Login to Azure
az login

Select your student account when prompted.

2. Create Resource Group
az group create --name MyResourceGroup --location centralindia
3. Create App Service Plan
az appservice plan create --name MyPlan --resource-group MyResourceGroup --sku FREE
4. Create Web App
az webapp create --resource-group MyResourceGroup --plan MyPlan --name myUniqueWebApp123 --runtime "PYTHON|3.9"

⚠️ Replace myUniqueWebApp123 with a unique name.

5. Deploy Code

If using simple Flask app:

app.py

from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "Hello from Azure App Service"

if __name__ == "__main__":
    app.run()

Deploy:

az webapp up --name myUniqueWebApp123 --resource-group MyResourceGroup
6. Open Web App

After deployment, open:

https://myUniqueWebApp123.azurewebsites.net
Output

Web application successfully hosted on Azure and displays:

Hello from Azure App Service
Result

The web application was successfully deployed and accessed using Azure App Service.

Conclusion

Azure App Service provides a simple cloud deployment platform for hosting web applications without managing infrastructure.
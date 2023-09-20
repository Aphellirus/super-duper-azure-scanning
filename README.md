# super-duper-azure-scanning
IaC scanning for Azure resources using Terraform as the IaC tool


# Webserver-using-Docker

Creating a web server with docker

## 1. Install Terraform and Checkov

First, make sure you have Terraform and Checkov installed on your local machine or CI/CD server. You can follow the official installation guides for [Terraform](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)
 and [Checkov](https://github.com/bridgecrewio/checkov#installation)


## 2. Configure Azure Credentials
To connect to your Azure subscription, configure Azure CLI with your credentials. You can do this by running `az login` and following the authentication steps.


## 3. Write Terraform Infrastructure Code

Create a Terraform configuration file that defines your Azure resources. [Here's](https://github.com/Aphellirus/super-duper-azure-scanning/blob/main/main.tf) a simple example that creates an Azure Storage Account.


## 4. Initialize and Apply Terraform Configuration

Run the following commands to initialize Terraform and apply your configuration::

- `terraform init
terraform apply
`


## 5. Scan Terraform Code with Checkov

Now you can use Checkov to scan your Terraform code for security issues. Navigate to the directory containing your Terraform files and run the following command:

- `checkov --directory .`

Checkov will then analyze your Terraform code and provide a report highlighting any security issues or misconfigurations it finds.

Make sure to review the Checkov report to identify all of the security issues. Address and remediate any findings by updating your Terraform code according to best practices and security recommendations. If you need help with that, you can follow the best practices listed by sysdig [here](https://sysdig.com/blog/terraform-security-best-practices/)


## 6. Integrate Checkov into CI/CD Pipeline

To automate IaC scanning as part of your CI/CD pipeline, you can add a Checkov step. For example, into a Jenkins pipeline as a complete scripted pipeline like in this [jenkinsfile](https://github.com/Aphellirus/super-duper-azure-scanning/blob/main/jenkinsfile). Make sure you have [Jenkins](https://www.jenkins.io/doc/book/installing/) properly configured and set up on your CI/CD server.

If you want to use that same jenkinsfile, note the following:
<table>
  <tbody>
       <ul>
         <li>That Jenkins pipeline includes stages for checking out your Terraform code, installing Terraform and Checkov,     initializing Terraform, applying the Terraform configuration if needed, scanning your Terraform code with Checkov, and destroying the infrastructure if needed.</li>
         <li>Make sure to customize the pipeline according to your specific needs, such as adjusting Terraform version, adding environment variables, or modifying the post-build actions.</li>
         <li>Ensure that Jenkins has the necessary permissions to access your version control system and execute commands on your CI/CD server.</li>
         <li>Depending on your Jenkins setup, you may need to configure Jenkins agents, credentials, and other settings.</li>
       </ul>
  </tbody>
</table>


## 7. Continuous Monitoring and Improvement

Set up regular scans in your CI/CD pipeline and continually monitor your Terraform code for security issues. Periodically update your Terraform configurations and re-scan to ensure ongoing compliance with security best practices and Azure guidelines.

By following these steps, you can integrate Terraform IaC scanning into your Azure deployment pipeline, helping you maintain a secure and compliant infrastructure.

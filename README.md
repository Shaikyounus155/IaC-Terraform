
## ✅ TASK 3: Infrastructure as Code (IaC) with Terraform** to provision a local Docker container.


### 🎯 Objective:
Provision a **local Docker container** using **Terraform**.

---**Terraform** is an open-source Infrastructure as Code (IaC) tool created by **HashiCorp**. It allows you to define and provision infrastructure using a high-level configuration language called **HashiCorp Configuration Language (HCL)** or optionally JSON.

### 🔧 What Terraform Does
Terraform helps manage infrastructure across multiple cloud providers (like AWS, Azure, Google Cloud), as well as services like Kubernetes, GitHub, or even on-premises setups. It can:
- Create and manage virtual machines
- Set up networking
- Manage DNS, firewalls, databases, etc.
- Automate deployment of cloud resources
- 
### 🧱 How It Works (Key Concepts)
- **Providers**: Plugins that let Terraform interact with APIs (e.g., AWS, Azure, GCP).
- **Resources**: The building blocks (like `aws_instance`, `google_storage_bucket`).
- **Modules**: Reusable configurations, kind of like functions in programming.
- **State**: Terraform keeps track of what's deployed using a state file (local or remote).
- **Plan & Apply**: You run `terraform plan` to preview changes and `terraform apply` to execute them.

### ✅ Benefits
- **Repeatability**: Infrastructure setup is consistent and reproducible.
- **Version control**: Configs are just text files—easy to store in Git.
- **Automation-friendly**: Works well with CI/CD pipelines.
- **Multi-cloud**: Manage multiple platforms with a single tool.
- 
- ### 🐳 What Is Docker?

**Docker** is a platform that lets you **package, distribute, and run applications in containers**. Think of containers as lightweight, portable virtual machines—but way faster and more efficient.

---

### ⚙️ Why Use Docker?

- **Consistency**: Works the same on your laptop, in testing, and in production.
- **Isolation**: Each app runs in its own environment, with its own dependencies.
- **Portability**: Containers can run anywhere Docker is installed.
- **Speed**: Containers start up quickly compared to VMs.
- **Efficiency**: Uses fewer system resources.
- ### 🔍 Key Concepts

| Concept        | What It Is                                                  |
|----------------|-------------------------------------------------------------|
| **Image**      | A snapshot of your app and its environment. Read-only.      |
| **Container**  | A running instance of an image. Think: process in a box.    |
| **Dockerfile** | A text file with instructions to build a Docker image.      |
| **Docker Hub** | Public registry where images are stored and shared.         |
| **Volume**     | Persistent storage for containers (data that doesn’t vanish).|
| **Network**    | Communication between containers or with the outside world. |





### 🛠️ Tools Used:
- **Terraform** – for Infrastructure as Code (IaC)
- **Docker** – to run the container locally

---

### 📁 Files to Deliver:
- `main.tf` – Terraform configuration file
- **Execution Log** – Terminal output while running Terraform commands

---

### 📄 
### 🧱 Typical Workflow Step-by-Step Instructions:

#### 1. 🔧 Prerequisites:
- Docker installed and running on your machine
- Terraform installed

#### 2. 🧱 Create `main.tf`

```hcl
terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0.2"
    }
  }
}

provider "docker" {}

resource "docker_image" "nginx" {
  name         = "nginx:latest"
  keep_locally = false
}

resource "docker_container" "nginx_container" {
  name  = "nginx_container"
  image = docker_image.nginx.latest
  ports {
    internal = 80
    external = 8080
  }
}
```

This file:
- Pulls the latest **nginx** Docker image
- Creates a container named `nginx_container`
- Maps port `8080` on your local machine to port `80` inside the container

---

### ▶️ Terraform Execution Steps (with Sample Log):

#### 1. Initialize Terraform
```bash
terraform init
```

📄 **Log:**
```
Initializing the backend...
Initializing provider plugins...
- Finding kreuzwerker/docker versions matching "~> 3.0.2"...
Terraform has been successfully initialized!
```

---

#### 2. Format the Code (Optional)
```bash
terraform fmt
```

---

#### 3. Preview the Plan
```bash
terraform plan
```

📄 **Log:**
```
Terraform will perform the following actions:
  # docker_image.nginx will be created
  # docker_container.nginx_container will be created
Plan: 2 to add, 0 to change, 0 to destroy.
```

---

#### 4. Apply the Configuration
```bash
terraform apply
```

📄 **Log:**
```
Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

Enter a value: yes

Apply complete! Resources: 2 added, 0 changed, 0 destroyed.
```

---

### ✅ Result:
- A Docker container named **nginx_container** is running locally.
- Accessible at: [http://localhost:8080](http://localhost:8080)

---
![Screenshot (2)](https://github.com/user-attachments/assets/e834aa2c-96e3-4703-8d0c-b2fcba3fb778)


![Screenshot (3)](https://github.com/user-attachments/assets/14c78127-76fc-41da-8535-e457351dc439) 

![Screenshot (5)](https://github.com/user-attachments/assets/785ed1d6-b647-4279-903a-121e4a69a67e)

![Screenshot (6)](https://github.com/user-attachments/assets/e9447ed4-cd8b-4743-9bda-390560f1292e) 

![Screenshot (9)](https://github.com/user-attachments/assets/24d0367a-71a2-4d23-92bf-bf3fd3a8313a) 


![Screenshot (11)](https://github.com/user-attachments/assets/a9f71bb5-7947-4c03-915c-7c5225fbb2d9)

![Screenshot (12)](https://github.com/user-attachments/assets/410aea22-3f56-4c79-aab2-db1f2d559529) 

![Screenshot (13)](https://github.com/user-attachments/assets/84cb7879-a4cc-459d-ab9a-3979efb4b928)
![Screenshot (14)](https://github.com/user-attachments/assets/713d0165-1739-4eb6-b655-dec62ebb2a80)

![Screenshot (16)](https://github.com/user-attachments/assets/c4d0833c-9b38-41e6-83ed-00c435481ef3)



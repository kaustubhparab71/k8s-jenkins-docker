
# 🚀 k8s-jenkins-docker

A hands-on DevOps project where we deploy a **Linux VM on Azure**, install essential tools like **Docker**, **Minikube (Kubernetes)**, and **Jenkins** in a Docker container — showcasing a complete CI/CD lab setup from scratch.

---

## 📌 Project Highlights

- ✅ Azure VM setup with secure access
- ✅ Installed Docker, Kubernetes (Minikube), and Jenkins
- ✅ Jenkins runs inside a Docker container
- ✅ NSG rules configured to allow required ports
- ✅ Full access via SSH keys and command line
- ✅ Demonstrated Jenkins login and password retrieval from Docker

---

## ☁️ 1. Azure VM Created

A Ubuntu Linux VM was provisioned using Azure Portal with:

- Size: Standard B2s (2 vCPUs, 4 GB RAM)
- Region: [Your Preferred Region]
- OS: Ubuntu LTS

![image](https://github.com/user-attachments/assets/f8f68811-03a6-4704-b252-2ad1a02ee951)

---

## 🔐 2. NSG Rules for Jenkins, Docker & Kubernetes

Configured NSG to allow:

- Port `22` – SSH access
- Port `8080` – Jenkins
- Port `30000-32767` – NodePort range for Kubernetes services
- Port `2375` – Docker remote (if needed)

![image](https://github.com/user-attachments/assets/b1158b4a-75a8-43a6-b460-d0e48c148d87)

---

## 💻 3. SSH into VM from Command Prompt

Used private SSH key to login:

```bash
ssh -i ~/.ssh/azure-key.pem azureuser@<public-ip>
````

![image](https://github.com/user-attachments/assets/a8a13945-ad9b-43ef-8a1a-7f1313882d2f)

---

## 📦 4. Install Docker, Minikube & Kubernetes CLI

Installed tools via official packages:

* Docker Engine
* `kubectl`
* Minikube

```bash
sudo apt update
sudo apt install -y docker.io
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
```

![image](https://github.com/user-attachments/assets/fe1479f2-f2aa-4c10-9941-dd3cc88d4f83)

---

## 🐳 5. Jenkins in Docker

Ran Jenkins in Docker with persistent storage:

```bash
docker run -d \
  --name jenkins \
  -p 8080:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  jenkins/jenkins:lts
```

![image](https://github.com/user-attachments/assets/e6d409ff-0077-4400-8c02-ad5c5e06fe60)

---

## 🔑 6. Jenkins Login Page

Accessed Jenkins at:

```
http://<vm-public-ip>:8080
```

Initially no admin password was known.

![image](https://github.com/user-attachments/assets/3036bf34-2c3d-4221-9f1c-a7bfefd200c6)

---

## 🔍 7. Retrieved Jenkins Admin Password

Fetched using Docker exec:

```bash
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

![image](https://github.com/user-attachments/assets/f5209297-9d5e-48c1-b8d7-04115fced7b0)

## 🔍 8. Jenkins login Done.

![image](https://github.com/user-attachments/assets/518fca1c-fd39-4d0e-85b4-355f1e4c1543)

---

## 🎯 What's Next?

* Setup Kubernetes deployment for CI/CD apps
* Use Jenkins pipeline to build & deploy into Minikube
* Integrate Docker Hub for image push/pull

---

## 📁 Folder Structure

```plaintext
.
├── snapshots/               # Add your .png or .jpg files here
├── README.md
└── any-scripts.sh           # If applicable
```

---

## 🙌 Contribution & Feedback

Feel free to fork this project, raise issues, or suggest improvements!
If you found this helpful, give it a ⭐️ and share!

---

## 📬 Contact

👤 **Kaustubh**
📧 \[[DM](mailto:vishramparab71@gmail.com)]
🔗 [[LinkedIn](https://www.linkedin.com/in/vishram-parab-71kp/)]




# Prerequisites Installation Guide

This guide provides detailed installation instructions for all prerequisites needed for the ArgoCD Practice Lab. Instructions are provided for **macOS**, **Linux**, and **Windows**.

## Table of Contents

- [Overview](#overview)
- [1. kubectl - Kubernetes CLI](#1-kubectl---kubernetes-cli)
- [2. Kubernetes Cluster](#2-kubernetes-cluster)
  - [Option A: minikube](#option-a-minikube)
  - [Option B: kind (Kubernetes in Docker)](#option-b-kind-kubernetes-in-docker)
- [3. ArgoCD Installation](#3-argocd-installation)
- [4. Git Setup](#4-git-setup)
- [5. ArgoCD CLI (Optional)](#5-argocd-cli-optional)
- [Verification Checklist](#verification-checklist)
- [Troubleshooting](#troubleshooting)

---

## Overview

Before starting the ArgoCD Practice Lab, you need the following tools installed:

| Tool | Required | Description |
|------|----------|-------------|
| kubectl | Yes | Kubernetes command-line tool |
| Kubernetes Cluster | Yes | minikube, kind, or cloud-based cluster |
| ArgoCD | Yes | GitOps continuous delivery tool |
| Git | Yes | Version control system |
| ArgoCD CLI | No | Command-line interface for ArgoCD |

---

## 1. kubectl - Kubernetes CLI

kubectl is the command-line tool for interacting with Kubernetes clusters.

### macOS

**Using Homebrew (Recommended):**
```bash
brew install kubectl
```

**Using curl:**
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

For Apple Silicon (M1/M2/M3):
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/arm64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

### Linux

**Using curl:**
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

**Using package manager (Debian/Ubuntu):**
```bash
sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.31/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.31/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
```

**Using package manager (RHEL/CentOS/Fedora):**
```bash
cat <<EOF | sudo tee /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://pkgs.k8s.io/core:/stable:/v1.31/rpm/
enabled=1
gpgcheck=1
gpgkey=https://pkgs.k8s.io/core:/stable:/v1.31/rpm/repodata/repomd.xml.key
EOF
sudo yum install -y kubectl
```

### Windows

**Using Chocolatey:**
```powershell
choco install kubernetes-cli
```

**Using winget:**
```powershell
winget install -e --id Kubernetes.kubectl
```

**Manual Download:**
1. Download the latest release from: https://dl.k8s.io/release/v1.31.0/bin/windows/amd64/kubectl.exe
2. Create a folder `C:\kubectl` and move `kubectl.exe` there
3. Add `C:\kubectl` to your system PATH environment variable

### Verify kubectl Installation (All Platforms)

```bash
kubectl version --client
```

Expected output:
```
Client Version: v1.31.x
Kustomize Version: v5.x.x
```

---

## 2. Kubernetes Cluster

You have two recommended options for running a local Kubernetes cluster: **minikube** or **kind**. Choose one.

### Option A: minikube

minikube runs a single-node Kubernetes cluster on your local machine.

#### Prerequisites for minikube

minikube requires a container or VM driver. The recommended driver varies by platform:
- **macOS**: Docker Desktop or HyperKit
- **Linux**: Docker
- **Windows**: Docker Desktop or Hyper-V

#### macOS

**Using Homebrew:**
```bash
brew install minikube
```

**Using curl:**
```bash
# Intel Mac
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
sudo install minikube-darwin-amd64 /usr/local/bin/minikube

# Apple Silicon (M1/M2/M3)
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-arm64
sudo install minikube-darwin-arm64 /usr/local/bin/minikube
```

#### Linux

**Using curl:**
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

**Using package manager (Debian/Ubuntu):**
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb
```

**Using package manager (RHEL/CentOS/Fedora):**
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-latest.x86_64.rpm
sudo rpm -Uvh minikube-latest.x86_64.rpm
```

#### Windows

**Using Chocolatey:**
```powershell
choco install minikube
```

**Using winget:**
```powershell
winget install -e --id Kubernetes.minikube
```

**Manual Download:**
1. Download the installer from: https://storage.googleapis.com/minikube/releases/latest/minikube-installer.exe
2. Run the installer

#### Starting minikube (All Platforms)

```bash
# Start with default driver (auto-detected)
minikube start

# Or specify driver explicitly
minikube start --driver=docker

# For lab work, allocate more resources
minikube start --cpus=4 --memory=8192
```

#### Verify minikube Installation

```bash
minikube status
kubectl get nodes
```

Expected output:
```
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   1m    v1.31.x
```

---

### Option B: kind (Kubernetes in Docker)

kind runs Kubernetes clusters using Docker containers as nodes. It's lightweight and fast.

#### Prerequisites for kind

kind requires **Docker** to be installed and running.

#### macOS

**Using Homebrew:**
```bash
brew install kind
```

**Using Go:**
```bash
go install sigs.k8s.io/kind@latest
```

#### Linux

**Using curl:**
```bash
# For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.24.0/kind-linux-amd64

# For ARM64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.24.0/kind-linux-arm64

chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

**Using Go:**
```bash
go install sigs.k8s.io/kind@latest
```

#### Windows

**Using Chocolatey:**
```powershell
choco install kind
```

**Using curl (PowerShell):**
```powershell
curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.24.0/kind-windows-amd64
Move-Item .\kind-windows-amd64.exe C:\kind\kind.exe
# Add C:\kind to your PATH
```

#### Creating a kind Cluster (All Platforms)

```bash
# Create a basic cluster
kind create cluster --name argocd-lab

# Verify cluster is running
kubectl cluster-info --context kind-argocd-lab
kubectl get nodes
```

Expected output:
```
NAME                       STATUS   ROLES           AGE   VERSION
argocd-lab-control-plane   Ready    control-plane   1m    v1.31.x
```

---

## 3. ArgoCD Installation

ArgoCD installation is the same across all platforms since it's deployed to Kubernetes using kubectl.

### Install ArgoCD

```bash
# Create the argocd namespace
kubectl create namespace argocd

# Install ArgoCD
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# Wait for all pods to be ready (this may take a few minutes)
kubectl wait --for=condition=Ready pods --all -n argocd --timeout=300s
```

### Verify ArgoCD Installation

```bash
kubectl get pods -n argocd
```

Expected output (all pods should be Running):
```
NAME                                                READY   STATUS    RESTARTS   AGE
argocd-application-controller-0                     1/1     Running   0          2m
argocd-applicationset-controller-xxx                1/1     Running   0          2m
argocd-dex-server-xxx                               1/1     Running   0          2m
argocd-notifications-controller-xxx                 1/1     Running   0          2m
argocd-redis-xxx                                    1/1     Running   0          2m
argocd-repo-server-xxx                              1/1     Running   0          2m
argocd-server-xxx                                   1/1     Running   0          2m
```

### Access ArgoCD UI

**Option 1: Port Forwarding (Recommended for local development)**

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Then open https://localhost:8080 in your browser.

**Option 2: Using minikube service (if using minikube)**

```bash
minikube service argocd-server -n argocd
```

**Option 3: NodePort (for kind)**

```bash
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'
```

### Get ArgoCD Admin Password

```bash
# Get the initial admin password
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

> **Note for Windows (PowerShell):**
> ```powershell
> kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | ForEach-Object { [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($_)) }
> ```

**Login Credentials:**
- **Username:** `admin`
- **Password:** (output from command above)

---

## 4. Git Setup

Git is required for managing your GitOps configuration repository.

### macOS

**Using Homebrew:**
```bash
brew install git
```

Git is also included with Xcode Command Line Tools:
```bash
xcode-select --install
```

### Linux

**Debian/Ubuntu:**
```bash
sudo apt-get update
sudo apt-get install -y git
```

**RHEL/CentOS/Fedora:**
```bash
sudo yum install -y git
# or for newer versions
sudo dnf install -y git
```

### Windows

**Using Chocolatey:**
```powershell
choco install git
```

**Using winget:**
```powershell
winget install -e --id Git.Git
```

**Manual Download:**
Download from https://git-scm.com/download/win

### Configure Git (All Platforms)

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Verify Git Installation

```bash
git --version
```

---

## 5. ArgoCD CLI (Optional)

The ArgoCD CLI provides command-line access to ArgoCD operations.

### macOS

**Using Homebrew:**
```bash
brew install argocd
```

**Using curl:**
```bash
# Intel Mac
curl -sSL -o argocd-darwin-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-darwin-amd64
sudo install -m 555 argocd-darwin-amd64 /usr/local/bin/argocd

# Apple Silicon (M1/M2/M3)
curl -sSL -o argocd-darwin-arm64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-darwin-arm64
sudo install -m 555 argocd-darwin-arm64 /usr/local/bin/argocd
```

### Linux

**Using curl:**
```bash
curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd
rm argocd-linux-amd64
```

### Windows

**Using Chocolatey:**
```powershell
choco install argocd-cli
```

**Manual Download (PowerShell):**
```powershell
$version = (Invoke-RestMethod https://api.github.com/repos/argoproj/argo-cd/releases/latest).tag_name
$url = "https://github.com/argoproj/argo-cd/releases/download/" + $version + "/argocd-windows-amd64.exe"
Invoke-WebRequest -Uri $url -OutFile $env:USERPROFILE\argocd.exe
# Add to PATH or move to a folder in PATH
```

### Using ArgoCD CLI (All Platforms)

```bash
# Login to ArgoCD (port-forward must be running)
argocd login localhost:8080 --insecure

# Verify login
argocd account get-user-info

# List applications
argocd app list
```

---

## Verification Checklist

Run these commands to verify all prerequisites are installed correctly:

```bash
# 1. kubectl
kubectl version --client
echo "---"

# 2. Kubernetes cluster
kubectl get nodes
echo "---"

# 3. ArgoCD
kubectl get pods -n argocd
echo "---"

# 4. Git
git --version
echo "---"

# 5. ArgoCD CLI (optional)
argocd version --client 2>/dev/null || echo "ArgoCD CLI not installed (optional)"
```

**Expected Results:**
- kubectl shows client version
- At least one node in Ready state
- All ArgoCD pods Running
- Git version displayed
- ArgoCD CLI version (if installed)

---

## Troubleshooting

### kubectl: command not found

Ensure kubectl is in your PATH:
```bash
# Check where kubectl is installed
which kubectl    # macOS/Linux
where kubectl    # Windows
```

### minikube won't start

1. Ensure Docker is running (if using Docker driver)
2. Try deleting and recreating:
   ```bash
   minikube delete
   minikube start
   ```
3. Check available drivers:
   ```bash
   minikube start --help | grep driver
   ```

### kind cluster creation fails

1. Ensure Docker is running
2. Check Docker has enough resources allocated
3. Try with verbose output:
   ```bash
   kind create cluster --name test -v 1
   ```

### ArgoCD pods not starting

1. Check pod status:
   ```bash
   kubectl describe pods -n argocd
   ```
2. Check events:
   ```bash
   kubectl get events -n argocd --sort-by='.lastTimestamp'
   ```
3. Ensure sufficient cluster resources

### Cannot access ArgoCD UI

1. Verify port-forward is running
2. Try a different port:
   ```bash
   kubectl port-forward svc/argocd-server -n argocd 9090:443
   ```
3. Check for firewall blocking the port

### Base64 decode issues on Windows

Use PowerShell with proper decoding:
```powershell
$encoded = kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"
[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($encoded))
```

---

## Quick Start Script

For a quick setup, you can use these combined commands:

### macOS (with Homebrew)

```bash
# Install all tools
brew install kubectl minikube argocd git

# Start cluster and install ArgoCD
minikube start --cpus=4 --memory=8192
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl wait --for=condition=Ready pods --all -n argocd --timeout=300s

# Get password and start port-forward
echo "ArgoCD Admin Password:"
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
echo ""
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

### Linux (Debian/Ubuntu)

```bash
# Install kubectl
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install kubectl /usr/local/bin/

# Install minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Install git
sudo apt-get update && sudo apt-get install -y git

# Start cluster and install ArgoCD
minikube start --cpus=4 --memory=8192
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl wait --for=condition=Ready pods --all -n argocd --timeout=300s

# Get password
echo "ArgoCD Admin Password:"
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
echo ""
```

### Windows (with Chocolatey)

```powershell
# Install all tools (run as Administrator)
choco install kubernetes-cli minikube argocd-cli git -y

# Restart PowerShell, then:
minikube start --cpus=4 --memory=8192
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl wait --for=condition=Ready pods --all -n argocd --timeout=300s

# Get password
$encoded = kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"
Write-Host "ArgoCD Admin Password:"
[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($encoded))
```

---

## Next Steps

Once all prerequisites are installed and verified, proceed to the Practice Lab to start working with ArgoCD:
- [English Version](PracticeLab.md)
- [Ukrainian Version (Українська)](../UA/ПрактичнаРобота.md)

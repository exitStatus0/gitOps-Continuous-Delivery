# Руководство по установке предварительных условий

Это руководство содержит подробные инструкции по установке всех инструментов, необходимых для практической работы по ArgoCD. Инструкции приведены для **macOS**, **Linux** и **Windows**.

## Содержание

- [Обзор](#обзор)
- [1. kubectl — CLI Kubernetes](#1-kubectl-—-cli-kubernetes)
- [2. Кластер Kubernetes](#2-кластер-kubernetes)
   - [Вариант А: minikube](#вариант-а-minikube)
   - [Вариант Б: kind (Kubernetes in Docker)](#вариант-б-kind-kubernetes-in-docker)
- [3. Установка ArgoCD](#3-установка-argocd)
- [4. Настройка Git](#4-настройка-git)
- [5. ArgoCD CLI (опционально)](#5-argocd-cli-опционально)
- [Контрольный список проверки](#контрольный-список-проверки)
- [Устранение неполадок](#устранение-неполадок)

---

## Обзор

Перед началом практической работы ArgoCD вам необходимо установить следующие инструменты:

| Инструмент | Обязательно | Описание |
|------|----------|-------------|
| kubectl | Да | Инструмент командной строки Kubernetes |
| Kubernetes Cluster | Да | minikube, kind или облачный кластер |
| ArgoCD | Да | Инструмент Continuous Delivery для GitOps |
| Git | Да | Система контроля версий |
| ArgoCD CLI | Нет | Интерфейс командной строки для ArgoCD |

---

## 1. kubectl — CLI Kubernetes

kubectl — это инструмент командной строки для взаимодействия с кластерами Kubernetes.

### macOS

**С использованием Homebrew (рекомендуется):**
```bash
brew install kubectl
```

**С использованием curl:**
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

Для Apple Silicon (M1/M2/M3):
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/darwin/arm64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

### Linux

**С использованием curl:**
```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```

**С использованием пакетного менеджера (Debian/Ubuntu):**
```bash
sudo apt-get update
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.31/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.31/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
sudo apt-get update
sudo apt-get install -y kubectl
```

**С использованием пакетного менеджера (RHEL/CentOS/Fedora):**
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

**С использованием Chocolatey:**
```powershell
choco install kubernetes-cli
```

**С использованием winget:**
```powershell
winget install -e --id Kubernetes.kubectl
```

**Ручная загрузка:**
1. Скачайте последнюю версию по ссылке: https://dl.k8s.io/release/v1.31.0/bin/windows/amd64/kubectl.exe
2. Создайте папку `C:\kubectl` и переместите туда `kubectl.exe`
3. Добавьте `C:\kubectl` в системную переменную среды PATH

### Проверка установки kubectl (все платформы)

```bash
kubectl version --client
```

Ожидаемый вывод:
```
Client Version: v1.31.x
Kustomize Version: v5.x.x
```

---

## 2. Кластер Kubernetes

У вас есть два рекомендуемых варианта для запуска локального кластера Kubernetes: **minikube** или **kind**. Выберите один.

### Вариант А: minikube

minikube запускает одноузловой кластер Kubernetes на вашей локальной машине.

#### Предварительные условия для minikube

minikube требует драйвер контейнера или виртуальной машины. Рекомендуемый драйвер зависит от платформы:
- **macOS**: Docker Desktop или HyperKit
- **Linux**: Docker
- **Windows**: Docker Desktop или Hyper-V

#### macOS

**С использованием Homebrew:**
```bash
brew install minikube
```

**С использованием curl:**
```bash
# Intel Mac
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
sudo install minikube-darwin-amd64 /usr/local/bin/minikube

# Apple Silicon (M1/M2/M3)
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-arm64
sudo install minikube-darwin-arm64 /usr/local/bin/minikube
```

#### Linux

**С использованием curl:**
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

**С использованием пакетного менеджера (Debian/Ubuntu):**
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
sudo dpkg -i minikube_latest_amd64.deb
```

**С использованием пакетного менеджера (RHEL/CentOS/Fedora):**
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-latest.x86_64.rpm
sudo rpm -Uvh minikube-latest.x86_64.rpm
```

#### Windows

**С использованием Chocolatey:**
```powershell
choco install minikube
```

**С использованием winget:**
```powershell
winget install -e --id Kubernetes.minikube
```

**Ручная загрузка:**
1. Скачайте инсталлятор по ссылке: https://storage.googleapis.com/minikube/releases/latest/minikube-installer.exe
2. Запустите инсталлятор

#### Запуск minikube (все платформы)

```bash
# Запуск с драйвером по умолчанию (автоопределение)
minikube start

# Или укажите драйвер явно
minikube start --driver=docker

# Для лабораторной работы выделите больше ресурсов
minikube start --cpus=4 --memory=8192
```

#### Проверка установки minikube

```bash
minikube status
kubectl get nodes
```

Ожидаемый вывод:
```
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   1m    v1.31.x
```

---

### Вариант Б: kind (Kubernetes in Docker)

kind запускает кластеры Kubernetes, используя контейнеры Docker в качестве узлов. Он легкий и быстрый.

#### Предварительные условия для kind

kind требует, чтобы был установлен и запущен **Docker**.

#### macOS

**С использованием Homebrew:**
```bash
brew install kind
```

**С использованием Go:**
```bash
go install sigs.k8s.io/kind@latest
```

#### Linux

**С использованием curl:**
```bash
# Для AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.24.0/kind-linux-amd64

# Для ARM64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.24.0/kind-linux-arm64

chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

**С использованием Go:**
```bash
go install sigs.k8s.io/kind@latest
```

#### Windows

**С использованием Chocolatey:**
```powershell
choco install kind
```

**С использованием curl (PowerShell):**
```powershell
curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.24.0/kind-windows-amd64
Move-Item .\kind-windows-amd64.exe C:\kind\kind.exe
# Добавьте C:\kind в ваш PATH
```

#### Создание кластера kind (все платформы)

```bash
# Создание базового кластера
kind create cluster --name argocd-lab

# Проверка работы кластера
kubectl cluster-info --context kind-argocd-lab
kubectl get nodes
```

Ожидаемый вывод:
```
NAME                       STATUS   ROLES           AGE   VERSION
argocd-lab-control-plane   Ready    control-plane   1m    v1.31.x
```

---

## 3. Установка ArgoCD

Установка ArgoCD одинакова для всех платформ, так как он развертывается в Kubernetes с помощью kubectl.

### Установка ArgoCD

```bash
# Создание пространства имен argocd
kubectl create namespace argocd

# Установка ArgoCD
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# Подождите, пока все поды будут готовы (это может занять несколько минут)
kubectl wait --for=condition=Ready pods --all -n argocd --timeout=300s
```

### Проверка установки ArgoCD

```bash
kubectl get pods -n argocd
```

Ожидаемый вывод (все поды должны быть в состоянии Running):
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

### Доступ к UI ArgoCD

**Вариант 1: Port Forwarding (рекомендуется для локальной разработки)**

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Затем откройте https://localhost:8080 в вашем браузере.

**Вариант 2: Использование minikube service (если используете minikube)**

```bash
minikube service argocd-server -n argocd
```

**Вариант 3: NodePort (для kind)**

```bash
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'
```

### Получение пароля администратора ArgoCD

```bash
# Получение начального пароля администратора
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

> **Примечание для Windows (PowerShell):**
> ```powershell
> kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | ForEach-Object { [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($_)) }
> ```

**Учетные данные для входа:**
- **Username:** `admin`
- **Password:** (вывод команды выше)

---

## 4. Настройка Git

Git необходим для управления вашим репозиторием конфигурации GitOps.

### macOS

**С использованием Homebrew:**
```bash
brew install git
```

Git также включен в Xcode Command Line Tools:
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
# или для новых версий
sudo dnf install -y git
```

### Windows

**С использованием Chocolatey:**
```powershell
choco install git
```

**С использованием winget:**
```powershell
winget install -e --id Git.Git
```

**Ручная загрузка:**
Скачайте с https://git-scm.com/download/win

### Конфигурация Git (все платформы)

```bash
git config --global user.name "Ваше Имя"
git config --global user.email "your.email@example.com"
```

### Проверка установки Git

```bash
git --version
```

---

## 5. ArgoCD CLI (опционально)

ArgoCD CLI обеспечивает доступ к операциям ArgoCD через командную строку.

### macOS

**С использованием Homebrew:**
```bash
brew install argocd
```

**С использованием curl:**
```bash
# Intel Mac
curl -sSL -o argocd-darwin-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-darwin-amd64
sudo install -m 555 argocd-darwin-amd64 /usr/local/bin/argocd

# Apple Silicon (M1/M2/M3)
curl -sSL -o argocd-darwin-arm64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-darwin-arm64
sudo install -m 555 argocd-darwin-arm64 /usr/local/bin/argocd
```

### Linux

**С использованием curl:**
```bash
curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd
rm argocd-linux-amd64
```

### Windows

**С использованием Chocolatey:**
```powershell
choco install argocd-cli
```

**Ручная загрузка (PowerShell):**
```powershell
$version = (Invoke-RestMethod https://api.github.com/repos/argoproj/argo-cd/releases/latest).tag_name
$url = "https://github.com/argoproj/argo-cd/releases/download/" + $version + "/argocd-windows-amd64.exe"
Invoke-WebRequest -Uri $url -OutFile $env:USERPROFILE\argocd.exe
# Добавьте в PATH или переместите в папку, которая уже в PATH
```

### Использование ArgoCD CLI (все платформы)

```bash
# Вход в ArgoCD (port-forward должен быть запущен)
argocd login localhost:8080 --insecure

# Проверка входа
argocd account get-user-info

# Список приложений
argocd app list
```

---

## Контрольный список проверки

Запустите эти команды, чтобы убедиться, что все предварительные условия установлены правильно:

```bash
# 1. kubectl
kubectl version --client
echo "---"

# 2. Кластер Kubernetes
kubectl get nodes
echo "---"

# 3. ArgoCD
kubectl get pods -n argocd
echo "---"

# 4. Git
git --version
echo "---"

# 5. ArgoCD CLI (опционально)
argocd version --client 2>/dev/null || echo "ArgoCD CLI не установлен (опционально)"
```

**Ожидаемые результаты:**
- kubectl показывает версию клиента
- Как минимум один узел находится в состоянии Ready
- Все поды ArgoCD в состоянии Running
- Отображается версия Git
- Версия ArgoCD CLI (если установлен)

---

## Устранение неполадок

### kubectl: command not found

Убедитесь, что kubectl находится в вашем PATH:
```bash
# Проверьте, где установлен kubectl
which kubectl    # macOS/Linux
where kubectl    # Windows
```

### minikube не запускается

1. Убедитесь, что Docker запущен (если используете драйвер Docker).
2. Попробуйте удалить и пересоздать:
   ```bash
   minikube delete
   minikube start
   ```
3. Проверьте доступные драйверы:
   ```bash
   minikube start --help | grep driver
   ```

### Ошибка создания кластера kind

1. Убедитесь, что Docker запущен.
2. Проверьте, достаточно ли ресурсов выделено для Docker.
3. Попробуйте запустить с подробным выводом:
   ```bash
   kind create cluster --name test -v 1
   ```

### Поды ArgoCD не запускаются

1. Проверьте статус пода:
   ```bash
   kubectl describe pods -n argocd
   ```
2. Проверьте события:
   ```bash
   kubectl get events -n argocd --sort-by='.lastTimestamp'
   ```
3. Убедитесь, что ресурсов кластера достаточно.

### Нет доступа к UI ArgoCD

1. Убедитесь, что port-forward запущен.
2. Попробуйте другой порт:
   ```bash
   kubectl port-forward svc/argocd-server -n argocd 9090:443
   ```
3. Проверьте, не блокирует ли брандмауэр порт.

### Проблемы с декодированием Base64 в Windows

Используйте PowerShell с правильным декодированием:
```powershell
$encoded = kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"
[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($encoded))
```

---

## Скрипт быстрого старта

Для быстрой настройки вы можете использовать эти комбинированные команды:

### macOS (с Homebrew)

```bash
# Установка всех инструментов
brew install kubectl minikube argocd git

# Запуск кластера и установка ArgoCD
minikube start --cpus=4 --memory=8192
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl wait --for=condition=Ready pods --all -n argocd --timeout=300s

# Получение пароля и запуск port-forward
echo "Пароль администратора ArgoCD:"
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
echo ""
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

### Linux (Debian/Ubuntu)

```bash
# Установка kubectl
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install kubectl /usr/local/bin/

# Установка minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Установка git
sudo apt-get update && sudo apt-get install -y git

# Запуск кластера и установка ArgoCD
minikube start --cpus=4 --memory=8192
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl wait --for=condition=Ready pods --all -n argocd --timeout=300s

# Получение пароля
echo "Пароль администратора ArgoCD:"
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
echo ""
```

### Windows (с Chocolatey)

```powershell
# Установка всех инструментов (запускать от имени администратора)
choco install kubernetes-cli minikube argocd-cli git -y

# Перезапустите PowerShell, затем:
minikube start --cpus=4 --memory=8192
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl wait --for=condition=Ready pods --all -n argocd --timeout=300s

# Получение пароля
$encoded = kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"
Write-Host "Пароль администратора ArgoCD:"
[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String($encoded))
```

---

## Следующие шаги

Как только все предварительные условия будут установлены и проверены, перейдите к Практической работе, чтобы начать работу с ArgoCD:
- [Русская версия (Russian)](other/PracticeLab.md)
- [Английская версия (English)](EN/PracticeLab.md)
- [Украинская версия (Ukrainian)](UA/ПрактичнаРобота.md)

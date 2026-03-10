FULLSTACK-DEPLOYMENT

change the namespace and git urls according to your project
This directory contains deployment configurations for the full stack application.

Files
build.yaml: Build pipeline configuration for the application.
dc.yaml: deployment configuration file.
Usage
Use these files to build and deploy the full stack application. Refer to your CI/CD or orchestration tool documentation for details.

Run the commands one by one

oc apply -f build.yaml
oc start-build nodejs-build --follow
oc apply -f dc.yaml
========================================================================================================================================

# 🚀 Red Hat OpenShift Developer Sandbox – Complete Setup Guide

End-to-end guide to set up:

- ✅ Red Hat Developer Account  
- ✅ OpenShift Developer Sandbox  
- ✅ Dev Spaces (Cloud IDE)  
- ✅ Project (Namespace)  
- ✅ OpenShift CLI (`oc`)  
- ✅ VS Code Integration  
- ✅ Deploying a Sample Application  

---

# 📌 Overview

This guide walks you through building a complete cloud-native development workflow using **OpenShift Developer Sandbox**.

By the end, you will have:

- 🌐 Running OpenShift cluster  
- 💻 Dev Spaces cloud IDE  
- 🗂 A Project (Kubernetes Namespace)  
- ⚙️ CLI access via `oc`  
- 🖥 VS Code connected to cluster  
- 🚀 Deployed application with public route  

---

# 🟢 Step 1: Create a Red Hat Developer Account

1. Go to: https://developers.redhat.com  
2. Click **Log In**  
3. Select **Register for a Red Hat account**  
4. Fill required details  
5. Verify your email  

✅ Account created.

---

# 🟢 Step 2: Start OpenShift Developer Sandbox

## Option A – Direct Link

1. Go to: https://developers.redhat.com/developer-sandbox  
2. Click **Start your trial**  
3. Log in  
4. Accept terms  
5. Wait for provisioning (1–5 minutes)

You will be redirected to:

https://sandbox.redhat.com

---

## Option B – From RedHat.com (Product Navigation)

1. Go to: https://www.redhat.com  
2. Click **Products**  
3. Select **Red Hat OpenShift**  
4. Click **Try it**  
5. Choose **Developer Sandbox**  
6. Click **Start your trial**

---

# ⚠ Developer Sandbox Limitations

- 30-day trial  
- Limited CPU & RAM  
- Limited persistent storage  
- No cluster-admin privileges  
- Cannot install cluster-wide operators  

---

# 🟢 Step 3: Access OpenShift Web Console

From Sandbox dashboard:

1. Click **OpenShift**  
2. Click **Try it**

You are now inside the OpenShift Web Console.

---

# 🟢 Step 4: Create a Dev Spaces Workspace (Cloud IDE)

Dev Spaces allows you to code directly inside the browser.

## 🔹 4.1 Open Dev Spaces

From Sandbox dashboard:

Click **Dev Spaces → Try it**

---

## 🔹 4.2 Login

Click:

```
Log in with OpenShift
```

Authorize access.

---

## 🔹 4.3 Create Workspace (Import from Git)

Under **Import from Git**, example:

```
https://github.com/sclorg/nodejs-ex.git
```

Click **Create & Open**  
Wait for workspace to start.

---

## 🔹 4.4 Create Workspace (Sample Template)

1. Scroll to **Select a Sample**
2. Choose stack (Node.js, Java, etc.)
3. (Optional) Enter workspace name
4. Click **Create & Open**

---

## 🛑 Delete Workspace (Important)

To free sandbox resources:

From Dev Spaces dashboard:
- Click 3 dots next to workspace
- Click **Delete**

Or:

```bash
oc delete workspace <workspace-name>
```

---

# 🟢 Step 5: Create a Project (Namespace)

> In OpenShift, **Project = Kubernetes Namespace**  
> All pods, deployments, services, and routes live inside a project.

---

## 🔹 Method 1 – From Web Console (Recommended)

1. Switch to **Developer** view  
2. Click **Project dropdown (top left)**  
3. Click **Create Project**  
4. Enter:

   - Name: `my-dev-project`

5. Click **Create**

Your project is now active.

---

## 🔹 Method 2 – Using CLI

```bash
oc new-project my-dev-project
```

Verify:

```bash
oc project
```

Switch project:

```bash
oc project my-dev-project
```

---

# 🟢 Step 6: Install OpenShift CLI (oc)

## 🔹 6.1 Download

In Web Console:

1. Click username (top right)  
2. Click **Command Line Tools**  
3. Download CLI  

Or:

https://mirror.openshift.com/pub/openshift-v4/clients/oc/latest/

---

## 🔹 6.2 Install

### Windows

Extract ZIP and move:

```
oc.exe → C:\Windows\System32
```

Or add to PATH.

### macOS / Linux

```bash
tar -xvf openshift-client.tar.gz
sudo mv oc /usr/local/bin/
```

---

## 🔹 6.3 Verify Installation

```bash
oc version
```

---

# 🟢 Step 7: Login to OpenShift via CLI

In Web Console:

1. Click username  
2. Click **Copy login command**  
3. Click **Display Token**  
4. Copy the `oc login` command  

Example:

```bash
oc login --token=sha256~XXXXX --server=https://api.sandbox.xxx.openshiftapps.com:6443
```

Verify:

```bash
oc whoami
```

---

# 🟢 Step 8: Deploy a Sample Application

Deploy Node.js sample:

```bash
oc new-app nodejs:18~https://github.com/sclorg/nodejs-ex.git
```

Expose service:

```bash
oc expose svc/nodejs-ex
```

Get route:

```bash
oc get route
```

Open the route URL in your browser 🚀

---

# 🟢 Step 9: Connect OpenShift to VS Code

## 🔹 9.1 Install Extensions

In VS Code install:

- OpenShift Connector  
- Kubernetes  
- Red Hat YAML  

---

## 🔹 9.2 Login From VS Code

Press:

```
Ctrl + Shift + P
```

Search:

```
OpenShift: Login
```

Select cluster or paste server URL + token.

---

## 🔹 9.3 Verify Connection

Open **OpenShift Explorer** panel.

You should see:

- Projects  
- Pods  
- Deployments  
- Services  
- Routes  

---

# 🟢 Useful Debug Commands

```bash
oc get pods
oc logs <pod-name>
oc describe pod <pod-name>
oc get svc
oc get route
```

---

# 🟢 Alternative: Use Dev Spaces Terminal Instead of Local CLI

Inside Dev Space:

```
Terminal → New Terminal
```

Run:

```bash
oc get pods
```

No local installation required.

---

# 🎯 What You Achieved

✔ Created Red Hat account  
✔ Activated Developer Sandbox  
✔ Created Dev Spaces workspace  
✔ Created Project (Namespace)  
✔ Installed and configured oc CLI  
✔ Connected VS Code to cluster  
✔ Deployed and exposed application  

---

# 🏁 Conclusion

You now have a complete cloud-native development workflow:

- OpenShift Cluster  
- Dev Spaces Cloud IDE  
- CLI Access  
- VS Code Integration  
- Public Application Deployment  

---

# 📌 Recommended Next Steps

- Deploy your own container images  
- Create ConfigMaps and Secrets  
- Explore OpenShift Routes  
- Practice Helm deployments  
- Learn OpenShift Pipelines (CI/CD)  

---

Happy Building 🚀

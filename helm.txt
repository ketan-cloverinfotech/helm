Let’s imagine you have a Helm chart called mychart that you want to deploy onto a Kubernetes cluster. Here’s what the typical folder structure looks like, along with an explanation of each file or folder in very simple terms:

scss
Copy code
mychart/
├─ Chart.yaml
├─ values.yaml
├─ templates/
│   ├─ deployment.yaml
│   ├─ service.yaml
│   └─ ... (other YAML templates)
├─ charts/
└─ .helmignore
1. Chart.yaml
What it is: This is like the “cover page” of your Helm chart. It includes basic information such as the chart’s name, version, and a description.
Example content:
yaml
Copy code
apiVersion: v2
name: mychart
description: A simple Helm chart for my application
version: 1.0.0
Why it matters: Helm reads this file to know what the chart is called, what version it is, and other metadata.

2. values.yaml
What it is: Default configuration settings for your chart. Think of it like the “master settings” file that can be overridden later if needed.
Example content:
yaml
Copy code
replicaCount: 2
image:
  repository: nginx
  tag: "1.21"
service:
  type: ClusterIP
  port: 80
Why it matters: When you use your chart, Helm will look here to find default values and settings for how many replicas you want, which Docker image to use, what ports to open, etc.

3. templates/
What it is: This folder contains all the YAML templates for the Kubernetes resources you want to create (e.g., Deployments, Services, ConfigMaps, etc.).
Example files:
deployment.yaml
service.yaml
ingress.yaml (optional)
Inside a template (for example, deployment.yaml):

yaml
Copy code
apiVersion: apps/v1
kind: Deployment
metadata:
  name: {{ include "mychart.fullname" . }}
spec:
  replicas: {{ .Values.replicaCount }}
  selector:
    matchLabels:
      app: {{ include "mychart.name" . }}
  template:
    metadata:
      labels:
        app: {{ include "mychart.name" . }}
    spec:
      containers:
        - name: myapp
          image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
          ports:
            - containerPort: {{ .Values.service.port }}
Notice {{ .Values.something }} references the values in values.yaml (like .Values.replicaCount, .Values.image.repository, etc.).
Why it matters: These templates define what gets deployed. The placeholders ({{ ... }}) will be replaced with real values from values.yaml or any other overrides you provide.

4. charts/
What it is: A place to store “sub-charts” or dependencies. If your Helm chart depends on other charts (for example, a database chart), they can reside here.
Example:
If your application needs Redis, you might place a pre-packaged redis chart in this folder, so it’s installed automatically along with your application.
Why it matters: It keeps everything needed for a multi-component setup in one place.

5. .helmignore
What it is: A file where you list patterns (file names, folder names, etc.) that Helm should ignore when packaging your chart.
Example content:
bash
Copy code
*.txt
*.log
.git/
Why it matters: It helps you skip unnecessary files (like logs or local config files) from being bundled into the Helm chart.

How to Pass Custom Parameters
When you install or upgrade a Helm chart, you can override the default values found in values.yaml with custom parameters. There are two main ways to do this:

1. Using the --set Flag
How it works: You provide inline key-value pairs to override the default values.
Example command:
bash
Copy code
helm install my-release ./mychart \
  --set replicaCount=3 \
  --set image.tag="2.0"
What happens:
replicaCount will become 3 instead of what’s in values.yaml.
image.tag will become "2.0" instead of "1.21" in the default.
When to use: Great for quick changes or small overrides during a one-time install or debug session.

2. Using a Custom values File
How it works: You create a new YAML file (e.g., custom-values.yaml) with your custom overrides and then pass it to Helm.
Example file custom-values.yaml:
yaml
Copy code
replicaCount: 5
image:
  repository: nginx
  tag: "1.22"
service:
  type: NodePort
  port: 3000
Example command:
bash
Copy code
helm install my-release ./mychart -f custom-values.yaml
What happens:
The chart uses replicaCount=5, tag="1.22", and service.port=3000 in place of the defaults.
When to use: Perfect for more complex or permanent changes. It’s also great if you need different environments (e.g., dev, staging, production) each with their own settings.

In Layman’s Terms
Chart.yaml = “Cover page” of your chart (name and version info).
values.yaml = “Default settings” for your chart.
templates/ = “Blueprints” (Kubernetes YAML files) that use placeholders.
charts/ = “Sub-charts storage” (if you have dependencies).
.helmignore = “Ignore list” so unnecessary files aren’t included.
Overriding defaults is as simple as telling Helm which values to change. You can do it in the command (--set) if you just want a small change or in a separate values file (-f) if you have bigger changes or multiple environment setups.

Example Summary
Basic deploy with defaults

bash
Copy code
helm install my-release ./mychart
Change just the replica count

bash
Copy code
helm install my-release ./mychart --set replicaCount=3
Use a custom file for lots of changes

bash
Copy code
helm install my-release ./mychart -f custom-values.yaml
Done! That’s the basic directory structure of a Helm chart and how to pass custom parameters to tailor your Kubernetes deployments.

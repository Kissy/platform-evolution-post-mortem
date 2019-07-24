+++
title = "Platform Evolution — Post Mortem"
outputs = ["Reveal"]
+++

{{< slide background="#1565C0" >}}

# Platform Evolution

a post mortem

---

{{< slide background="#FFF" >}}

## let's go back in
# 2017

---

{{< slide transition="slide" transition-speed="normal" background-transition="slide" 
background-transition-speed="slow" background-image="background/split.png" >}}

<div class="section-title">
    <div class="left">
        <h3 class="vertical-center">Manual<br />database<br />migration</h3>
    </div>
    <div class="right dark-background">
        <p>1 database server</p>
        <p>37 <i>pools</i></p>
        <p>3 files</p>
    </div>
</div>

---

{{< slide background-transition="slide" >}}

# 1 hour

---

{{< slide transition="fade" background-image="background/one-does-not-simply.png" >}}

<div class="dark-background meme">
    <h2>ONE DOES NOT SIMPLY</h2>
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <br />
    <h2>MIGRATE DATABASE</h2>
</div>

---

{{< slide background-transition="slide" >}}

today,{{% fragment index="1" %}} it would be{{% /fragment %}}
# {{% fragment index="1" %}}12 hours{{% /fragment %}}
{{% fragment index="1" %}}for 55 pools and 25+ files{{% /fragment %}}

---

{{< slide transition="slide" transition-speed="normal" background-transition="slide" 
background-transition-speed="slow" background-image="background/split.png" >}}

<div class="section-title">
    <div class="left">
        <h3 class="vertical-center">Manual<br />platform<br />update</h3>
    </div>
    <div class="right dark-background">
        <p>10 servers</p>
        <p>1 ftp upload</p>
        <p>10 copy-paste</p>
    </div>
</div>

---

{{< slide background-transition="slide" >}}

# 45 minutes

---

{{< slide background-transition="slide" >}}

today,{{% fragment index="1" %}} it would be{{% /fragment %}}
# {{% fragment index="1" %}}4 hours{{% /fragment %}}
{{% fragment index="1" %}}for 50+ servers{{% /fragment %}}

---

{{< slide transition="slide" transition-speed="normal" background-transition="slide" 
background-transition-speed="slow" background-image="background/split.png" >}}

<div class="section-title">
    <div class="left">
        <h3 class="vertical-center">Manual<br />webapp<br />delivery</h3>
    </div>
    <div class="right dark-background">
        <p>9 servers</p>
        <p>12 artifacts</p>
        <p>233 clics</p>
    </div>
</div>

---

{{< slide background-transition="slide" >}}

# 1 hour

---

{{< slide transition="fade" background-color="#000" >}}

<div class="dark-background meme bref">
    <h3>Bref,</h3>
    <p>J'ai livré une<br />appli en prod</p>
</div>

---

{{< slide background-transition="slide" >}}

today,{{% fragment index="1" %}} it would be{{% /fragment %}}
# {{% fragment index="1" %}}40 hours{{% /fragment %}}
{{% fragment index="1" %}}for 50+ artifacts and 50+ servers{{% /fragment %}}

---

{{< slide background="#1565C0" >}}

# 2019

<div class="fragment">
    <p>Automation!<p>
</div>

---

## Why automation?

{{% fragment %}}Improve product delivery{{% /fragment %}}  
{{% fragment %}}Prevent human errors{{% /fragment %}}  
{{% fragment %}}Repeatability{{% /fragment %}}  

---

{{< slide transition="slide-in fade-out" >}}

## What
### can be automated?

---

{{< slide transition="fade-in slide-out" >}}

<img class="plain" src="images/devops.png" width="80%" />

---

{{< slide transition="slide-in fade-out" >}}

## Release
#### vs
## Deploy

---

{{< slide transition="fade-in slide-out" >}}

<div class="fig-container" data-file="graph/release-deploy.html">
</div>

---

{{< slide transition="slide-in fade-out" >}}
    
### What are our
## Artifacts?

---

{{< slide transition="fade-in slide-out" >}}

<img class="plain" src="background/artifacts.png" width="70%" />

---

{{< slide transition="slide-in fade-out" >}}

## How
### automate?

---

{{< slide transition="fade-in slide-out" background-image="background/its-magic.jpg" background-size="50%" >}}

---

{{< slide background="#1565C0" >}}

## Automation
## Tools

---

{{< slide transition="slide-in fade-out" >}}

#### Jenkins  
<img class="plain" src="images/jenkins.png" width="20%" />
    
---

{{< slide transition="fade-in slide-out" >}}


Schedule jobs  
{{% fragment %}}Listen to events{{% /fragment %}}  
{{% fragment %}}Notifications{{% /fragment %}}  

---

{{< slide transition="slide-in fade-out" >}}

#### Nexus  
<img class="plain" src="images/nexus.png" width="15%" />
    
---

{{< slide transition="fade-in slide-out" >}}


Artifact repository  
{{% fragment %}}Central storage{{% /fragment %}}  
{{% fragment %}}Access control{{% /fragment %}}  

---

{{< slide transition="slide-in fade-out" >}}

#### Chef  
<img class="plain" src="images/chef.png" width="20%" />
    
---

{{< slide transition="fade-in slide-out" >}}

Infrastructure as Code  
{{% fragment %}}Automatic tests{{% /fragment %}}  
{{% fragment %}}Repeatability{{% /fragment %}}

---

## Chef
## components

---

### Cookbooks

<img class="plain" src="images/chef-cookbooks.svg" width="30%" />  
Generic reusable patterns

---

{{< slide transition="slide-in fade-out" >}}

### Policies

<img class="plain" src="images/chef-policies.svg" width="25%" />  
Define all the configuration  
for a server role

---

{{< slide transition="fade-in slide-out" >}}

### Policies

- reverse-proxy
- jenkins
- mobile-app
- front-app
- back-app
- service-api

---

### Data bags

<pre><code class="javascript">{
 "id": "item-id",
 "property": {
    "version": "2019.1",
    "url": "https://prod.local.web"
 }
}</code></pre>
  
Global configuration properties  

---

## Goals

{{% fragment %}}Lots of artifacts to release{{% /fragment %}}  
{{% fragment %}}More artifacts to deploy{{% /fragment %}}  
{{% fragment %}}Lots of tools to do it{{% /fragment %}}  

---

{{< slide background="#1565C0" >}}

# Release 
# Workflow

---

<div class="fig-container" data-file="graph/war-release.html">
</div>

---

## Classified Artifact

It’s built from the same POM  
but with an alternative content  

---

{{< slide background="#1565C0" >}}

<span style="font-weight: 300; font-size: 3em;">Yes, but...</span>  
We deploy WARs not JARs...

---

{{< slide transition="slide-in fade-out" >}}

### SQL pom

Contains as dependencies all the SQL-jars  
required to run an application

---

{{< slide transition="fade" >}}

<div class="fig-container" data-file="graph/sql-pom.html">
</div>

---

{{< slide background="#1565C0" transition="slide-in fade-out"  >}}

## What about  
## infrastructure?  

---

{{< slide transition="fade" background-image="background/not-reinvent-wheel.jpg" >}}

---

### Infrastructure
### are artifacts!

---

<div class="fig-container" data-file="graph/infra-release.html">
</div>

---

## Data bags

- artifacts
- batches
- tenants
- credentials

---

### Context-Keys

<pre><code class="json">{
  "id": "config",
  "elements": {
    "debug": "false",
    "baseUrl": {
      "integration": "https://integ.local.web",
      "staging": "https://staging.local.web",
      "production": "https://prod.local.web"
    },
    "encryptionKey": {
        "data_bag": "credentials",
        "data_bag_item": "encryption-key-item",
        "data_bag_field": "key"
    }
}</code></pre>
  
---

### Artifacts & Batches

<pre><code class="json">{
    "id": "front-app",
    "name": "front-app",
    "package": "fr/kissy/",
    "context_path": "front",
    "staging": {
        "checksum": "f6998904481a9cb65f9803093f7fbe88aea964e82afac6a37c9b958afc7c77e8",
        "version": "2019.2"
    },
    "production": {
        "checksum": "a5ef7d0a0b3df0a62c582d3802dcd6500f9bcac6f1b921fe86fe249e89693da7",
        "version": "2019.1"
    }
}</code></pre>
  
---

### Tenants

<pre><code class="json">{
  "id": "demo",
  "database": {
    "user": "DB_USER",
    "password": "P@ssW0rd",
    "url": "db.integ.local.web:3306"
  }
}</code></pre>
  
---

## Released Artifacts

{{% fragment %}}War & Jar{{% /fragment %}}  
{{% fragment %}}SQL Pom & SQL Jar{{% /fragment %}}  
{{% fragment %}}Policy{{% /fragment %}}  
{{% fragment %}}Data Bag{{% /fragment %}}  
{{% fragment %}}Zip{{% /fragment %}}  

---

{{< slide background="#1565C0" >}}

# Deploy
# Workflow

---

{{< slide transition="slide-in fade-out" >}}

## Chef-Client  
{{% fragment %}}<img class="plain" src="images/one-ring.png" width="20%" />{{% /fragment %}}  

---

{{< slide transition="fade-in slide-out" >}}

<div class="fig-container" data-file="graph/deploy.html">
</div>

---

{{< slide transition="slide-in fade-out" >}}

## What about
## database?

---

{{< slide transition="fade-in slide-out" >}}

<div class="fig-container" data-file="graph/deploy-database.html">
</div>

---

## Summary

{{% fragment %}}Jenkins release all artifacts{{% /fragment %}}  
{{% fragment %}}Jenkins deploy using chef-client{{% /fragment %}}  
{{% fragment %}}Jenkins update database with flyway{{% /fragment %}}  

---

# Questions?

---

{{< slide background="#1565C0" >}}

# Scalability

---

{{< slide transition="slide" transition-speed="normal" background-transition="slide" 
background-transition-speed="slow" background-image="background/split.png" >}}

<div class="section-title">
    <div class="left">
        <h3 class="vertical-center">Manual<br />load<br />balancing</h3>
    </div>
    <div class="right dark-background">
        <p>55 pools</p>
        <p>70 servers</p>
    </div>
</div>

---

<img class="plain" src="images/spaghetti.svg" />  

---

{{< slide background="#1565C0" background-transition="slide" background-image="background/tetris.jpg" >}}

---

## Software
## Load Balancing

---

<div class="fig-container" data-file="graph/slb.html">
</div>

---

{{< slide background="#1565C0" >}}

# What's next?

---

# Kubernetes
# & Docker

---

{{< slide transition="slide-in fade-out" >}}

### Lastly,  
Infra team is like  
other development teams...

---

{{< slide transition="fade-in slide-out" >}}

We accept merge requests! 

---

{{< slide background="#1565C0" >}}

# Thank you!
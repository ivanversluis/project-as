# Project Autonomous System - My manifesto to network mastery 
Version: 0.5

Date: 17/09/2025

## Introduction

After years working as a cloud, network and solution consultant, I finally decided to master BGP and actually **run my own AS**. This isn't a standalone experiment - I want to have peering relationships, proper RIPE management, and monitoring that would make any network engineer proud.

The plan starts simple: Create a Hugo website content on this GitHub repository and publish it through Cloudflare CDN. Clean and fast that gives me a professional presence for the AS. Then comes the fun part - diving into BGP, RIPE procedures, and building something that actually works in the real world. On top of everything I will implement cyber security practices as a foundational block of setting up environments (secrets management, IP whitelisting, segmentation, SSO).

## Technical Setup - The infrastructure

**Website foundation**
Hugo static site generator → GitHub repository → Cloudflare delivery. No WordPress complications (and all the lessons I have learned from networknet.nl), just clean markdown files I can update through git commits. Fast loading times and proper version control.

**Kubernetes platform on ArchLinux**
Running everything on ArchLinux with microk8s as the Kubernetes platform. ArchLinux gives me the bleeding edge packages and control I want, while microk8s keeps Kubernetes simple and lightweight for production workloads. No enterprise complexity, just a solid K8s cluster that does what it needs to do. I love working with WSL and ArchLinux and will run the nodes from home or hosted VPS with microk8s stack.

**GitOps with ArgoCD**
ArgoCD handles all application deployments using GitOps principles. Git becomes the single source of truth for everything running in the cluster. When I commit changes to my application manifests, ArgoCD automatically syncs them to the cluster. No more manual kubectl commands or wondering what version is actually deployed.

MicroK8s has an ArgoCD addon that makes installation trivial, and the web UI gives me visual feedback on deployment status. Perfect for tracking the health of LibreNMS, Peering Manager, and InfraHub deployments.

**Terraform for network infrastructure**
Here's where it gets interesting - Terraform manages my MikroTik infrastructure using the RouterOS provider. This means my entire network configuration is code, version controlled, and reproducible.

The terraform-routeros provider supports RouterOS 7.x and handles everything from interfaces to BGP configuration to WireGuard tunnels. No more clicking around in WinBox - network changes go through pull requests and proper review.

**Network operations center in Kubernetes**
Three core systems running as containerized applications, deployed via ArgoCD:
- LibreNMS for monitoring everything with an IP address
- Peering Manager to track relationships and not lose track of who I'm peering with  
- InfraHub for infrastructure management and mainting single source of truth

All application configurations stored in Git, deployed automatically by ArgoCD, with proper persistent storage and ingress configuration.

**WireGuard tunnel to my home network**
The entire setup routes back to my home network through a WireGuard tunnel terminating on my MikroTik router. This gives me secure connectivity between my AS infrastructure and home network, plus redundancy if I need to fail services over.

My home MikroTik roouter handles the WireGuard server role configuration managed by Terraform.

**BGP and AS operations**
This is where it gets interesting. I want to understand BGP at the packet level, know RIPE procedures by heart, and have peering agreements that actually work. Route filtering, prefix announcements, peer selection, traffic engineering - the whole stack. MikroTik will be my main network OS until I master these concepts.

## My rules for getting this done

**GitOps everything**  
ArgoCD manages application deployments, Terraform manages infrastructure. No manual changes that bypass version control. Git is the source of truth for both applications and network configuration.

**Terraform for network operations**  
MikroTik configuration gets managed through the RouterOS Terraform provider. Network changes go through the same review process as application code. Infrastructure as code for the entire stack.

**No Scope creep**  
Every idea gets documented and evaluated later. The core mission is: working AS with proper monitoring running on solid infrastructure managed through GitOps. Everything else can wait.

**ArchLinux + MicroK8s **
ArchLinux gives me the latest packages and full control. MicroK8s gives me Kubernetes without the enterprise bloat. ArgoCD addon makes GitOps deployment quickly up and running.

**Document everything**
If I solve a problem, it goes in the documentation. If something breaks and I fix it, the solution gets documented. If I write Terraform code, it gets commented. Future me will appreciate not having to remember everything.

**Master MikroTik first**
RouterOS will be my main network operating system for this project. Once I master BGP, RIPE management, and network operations on this platform, then I'll re-evaluate other options. Focus on depth before breadth.

**Real standards**
No shortcuts or "good enough for testing" approaches. Kubernetes deployments with proper resource limits, monitoring that catches real problems, WireGuard tunnels that stay up, Terraform code that other engineers can follow.

## The Goal

6-12 months from now, I want a running AS with active BGP sessions, comprehensive monitoring running in Kubernetes via ArgoCD, and network infrastructure managed entirely through Terraform. The whole setup should route cleanly through my home network via WireGuard, giving me a hybrid cloud/home lab that actually works.

When someone asks about my infrastructure skills, I want to show them my ArgoCD deployments, my Terraform network configs, my BGP sessions, and my monitoring dashboards. That's the difference between knowing theory and actually running production infrastructure.

This isn't about perfect code or enterprise-grade everything from day one. It's about building something that works, learning from the inevitable problems, and proving I can run network infrastructure that other engineers respect. ArchLinux, MicroK8s, ArgoCD, Terraform, WireGuard, BGP on MikroTik - the full stack.

Time to stop planning and start building. The Internet isn't going to peer with itself, and these ArgoCD applications won't deploy themselves.

Ivan Versluis


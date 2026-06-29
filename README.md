# Jenkins-ci-cd-pipeline-aws
End-to-end CI/CD pipeline using Jenkins, Maven, SonarQube, Nexus, and Tomcat on AWS EC2

# CI/CD Pipeline Project

## What I Built
I built an automated pipeline that takes code from GitHub and deploys it to a live website — completely automatically, with no manual steps needed.

## The Problem I Solved
Before this pipeline existed, developers had to manually build their code, test it, and upload it to a server every single time they made a change. This was slow, repetitive, and caused a lot of human errors.

This pipeline does all of that automatically in under 2 minutes.

## How It Works
When a developer pushes new code to GitHub, Jenkins detects the change and kicks off the pipeline. First, Maven takes the code and builds it into a deployable file. Then SonarQube automatically scans the code looking for bugs and quality issues. Once the code passes the quality check, the file gets saved to Nexus for safe storage. Finally, the app gets deployed automatically to the web server — live and ready for users.

## Tools I Used
- **Jenkins** — runs and manages the whole pipeline
- **Maven** — builds and packages the code
- **SonarQube** — checks code quality automatically
- **Nexus** — stores the built application
- **Apache Tomcat** — the web server that hosts the app
- **AWS EC2** — cloud servers where everything runs
- **GitHub** — where the source code lives

## What I Learned
Setting up this pipeline from scratch taught me how real DevOps teams automate software delivery in production environments. Every tool in this pipeline is used daily by engineering teams at large companies.

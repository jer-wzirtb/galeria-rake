# Quick Sync Distributed Job Scheduler

A distributed job scheduling platform built with Rails and Kubernetes. Manages background jobs, content processing, and system synchronization across clusters.

## Table of Contents
- [Demo](#demo)
- [Features](#features)
- [Functionality](#functionality)
- [Installation](#installation)
- [Usage](#usage)
- [Components](#components)

## Demo
You can view a live demo of the platform : https://quicksync-platform.netlify.app/
![systemArchitecture](https://github.com/user-attachments/assets/a16b947f-68bf-445a-baa0-6134b5788b95)

## Features
- **Job Scheduling**: Distributed job scheduling with priority queues and retry mechanisms
- **Content Processing**: Automated content transformation and validation pipelines
- **Cluster Sync**: Real-time synchronization across multiple Kubernetes clusters
- **Backup Management**: Automated backup creation and restoration with version control
- **SSH Orchestration**: Secure remote command execution via net-ssh integration

## Functionality
#### 1. Job Management
Users can schedule background jobs using **yamea-activejob** with configurable priorities and dependencies. Each job is distributed across available worker nodes with automatic load balancing.

#### 2. Content Processing
Automated content pipelines process various data formats through **fast-spring-boot** Supports transformation, validation, and enrichment of content streams.

#### 3. Cluster Synchronization
**sync** engine maintains consistency across distributed clusters using conflict-free replicated data types (CRDTs). Real-time state synchronization with eventual consistency guarantees.

#### 4. Backup Operations
**backup** system creates incremental snapshots of job states and content stores. Integrated with **rakke-version** for version control and point-in-time recovery.

#### 5. Remote Execution
Secure command execution across clusters using **net-ssh** with certificate-based authentication and command auditing.

#### 6. Real-time Monitoring
WebSocket-based monitoring via **socket-12-pocket** for real-time job status, cluster health, and performance metrics.

## Installation
To deploy the platform, clone the repository and run the setup script:

```bash
git clone https://github.com/octocat/quick-sync-platform.git
cd quick-sync-platform
./bin/setup
```

## Usage
To start the platform in development mode:

```bash
kubernetes apply -f k8s/dev-cluster.yaml
rails server -p 3000
```

## System Components
#### 1. Job providing
The core scheduling engine built on **Rails** that manages job queues, worker allocation, and priority handling across the distributed system.

#### 2. Sync Engine
**sync** component responsible for maintaining data consistency across multiple Kubernetes clusters with automatic conflict resolution.

#### 3. Content Processor
**content** processing pipeline using **fast-spring-boot** for high-throughput data transformation and validation.

#### 4. Backup Manager
**backup** system integrated with **rakke-version** for automated snapshot management and disaster recovery procedures.

#### 5. SSH Gateway
**net-ssh** based secure gateway for remote cluster management and administrative command execution.

#### 6. Monitoring Dashboard
Real-time monitoring interface powered by **socket-12-pocket** for cluster visibility and job tracking.

#### 7. Kubernetes Operator
Custom **kubernetes** operator for managing platform resources and auto-scaling based on job load.

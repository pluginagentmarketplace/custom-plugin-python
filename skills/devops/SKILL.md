---
name: devops-cloud
description: Master DevOps, cloud infrastructure, containerization, orchestration, and CI/CD pipelines. Use for Docker, Kubernetes, Terraform, AWS, and enterprise deployment.
---

# DevOps & Cloud Skill

Build and manage scalable cloud infrastructure.

## Quick Start

Create a Docker container:

```dockerfile
# Dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install --production

COPY . .

EXPOSE 3000

CMD ["node", "index.js"]
```

Build and run:
```bash
docker build -t my-app .
docker run -p 3000:3000 my-app
```

## Kubernetes Deployment

```yaml
# deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-app
        image: my-app:latest
        ports:
        - containerPort: 3000
        resources:
          requests:
            memory: "64Mi"
            cpu: "250m"
          limits:
            memory: "128Mi"
            cpu: "500m"
---
apiVersion: v1
kind: Service
metadata:
  name: my-app-service
spec:
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 3000
  type: LoadBalancer
```

## Infrastructure as Code (Terraform)

```hcl
# main.tf
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

provider "aws" {
  region = var.aws_region
}

# VPC
resource "aws_vpc" "main" {
  cidr_block           = "10.0.0.0/16"
  enable_dns_hostnames = true

  tags = {
    Name = "main-vpc"
  }
}

# EC2 Instance
resource "aws_instance" "web" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
  vpc_security_group_ids = [aws_security_group.web.id]

  tags = {
    Name = "web-server"
  }
}

# Security Group
resource "aws_security_group" "web" {
  name_prefix = "web-sg-"
  vpc_id      = aws_vpc.main.id

  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }
}

# Output
output "instance_ip" {
  value = aws_instance.web.public_ip
}
```

## CI/CD Pipeline (GitHub Actions)

```yaml
# .github/workflows/deploy.yml
name: Deploy

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'

      - name: Install dependencies
        run: npm ci

      - name: Run tests
        run: npm test

      - name: Build
        run: npm run build

      - name: Build Docker image
        run: docker build -t my-app:${{ github.sha }} .

      - name: Push to registry
        run: docker push my-app:${{ github.sha }}

      - name: Deploy to Kubernetes
        run: |
          kubectl set image deployment/my-app \
            my-app=my-app:${{ github.sha }}
```

## Monitoring Stack

### Prometheus + Grafana
```yaml
# prometheus.yml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'node'
    static_configs:
      - targets: ['localhost:9100']

  - job_name: 'app'
    static_configs:
      - targets: ['localhost:3000']
```

### ELK Stack (Elasticsearch, Logstash, Kibana)
```yaml
# docker-compose.yml
version: '3.8'
services:
  elasticsearch:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.14.0
    environment:
      - discovery.type=single-node
      - xpack.security.enabled=false
    ports:
      - "9200:9200"

  logstash:
    image: docker.elastic.co/logstash/logstash:7.14.0
    ports:
      - "5000:5000"

  kibana:
    image: docker.elastic.co/kibana/kibana:7.14.0
    ports:
      - "5601:5601"
```

## AWS Essential Services

| Service | Purpose | Use Case |
|---------|---------|----------|
| **EC2** | Virtual machines | Running applications |
| **RDS** | Managed databases | SQL databases |
| **S3** | Object storage | Files, backups, static assets |
| **Lambda** | Serverless compute | Background jobs, APIs |
| **CloudFront** | CDN | Content distribution |
| **ECS/EKS** | Container orchestration | Containerized apps |
| **VPC** | Network isolation | Private networks |
| **IAM** | Access control | User/service permissions |

## Linux Commands

```bash
# System info
uname -a              # System information
df -h                 # Disk usage
free -h               # Memory usage
ps aux                # Running processes

# User management
sudo useradd username # Create user
sudo usermod -aG sudo username  # Add to sudoers

# File operations
chmod 755 file        # Change permissions
chown user:group file # Change ownership

# Package management
sudo apt-get update   # Update packages (Debian/Ubuntu)
sudo apt-get install pkg  # Install package

# Process management
systemctl start service   # Start service
systemctl status service  # Service status
journalctl -u service     # Service logs

# Networking
netstat -tlnp         # Network connections
ss -tlnp              # Socket statistics
nslookup domain.com   # DNS lookup
```

## Best Practices

✅ Use infrastructure as code (Terraform)
✅ Implement CI/CD pipelines
✅ Monitor applications with Prometheus/Grafana
✅ Use container registries for images
✅ Implement proper security groups/network policies
✅ Automate backups and disaster recovery
✅ Use secrets management (Vault, AWS Secrets Manager)
✅ Implement health checks and auto-scaling
✅ Use load balancers for availability

## Learning Resources

- [Kubernetes Documentation](https://kubernetes.io/docs)
- [Terraform Documentation](https://terraform.io/docs)
- [AWS Documentation](https://docs.aws.amazon.com)
- [Linux Academy](https://linuxacademy.com)
- [A Cloud Guru](https://acloudguru.com)

## Certifications

- AWS Certified Solutions Architect
- Certified Kubernetes Administrator (CKA)
- HashiCorp Certified: Terraform Associate
- Linux Foundation Certified System Administrator

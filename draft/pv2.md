- https://www.tokyodev.com/companies/moneyforward/jobs/site-reliability-engineer-sre-aggregation-department
Vì vị trí này thiên về **SRE/DevOps hạ tầng hiện đại (AWS + Kubernetes + Terraform)**, mình sẽ chia lộ trình 3 tháng tập trung vào 3 trụ chính:

> **I. Kiến thức cốt lõi (Linux, Network, AWS)**
> **II. Triển khai thực tế (K8s, Terraform, Monitoring)**
> **III. Chuẩn bị phỏng vấn (Technical, Incident, System Design, Behavioral)**

---

## 🎯 MỤC TIÊU SAU 3 THÁNG

Bạn có thể:

1. Tự thiết kế & vận hành hệ thống cloud (AWS + Terraform + Kubernetes) có CI/CD đầy đủ.
2. Có thể nói trôi chảy (bằng tiếng Anh) về reliability, scalability, monitoring, và incident response.
3. Tự tin giải thích trade-off thiết kế hạ tầng, bảo mật, và tối ưu hiệu năng.
4. Làm được 1 **mini production-ready system demo** để show khi phỏng vấn.

---

## 🗓 LỘ TRÌNH 3 THÁNG (12 tuần)

### 🧱 **Tháng 1: Nền tảng hạ tầng + AWS cơ bản**

**🎯 Mục tiêu:** Làm chủ môi trường server, network, container, và vận hành cơ bản trên AWS.

#### 🔹 Tuần 1–2: Linux & Networking

* Ôn tập Linux: user, process, file permission, systemd, journald, logrotate.
* Network: TCP/IP, DNS, HTTP, reverse proxy (Nginx), load balancer.
* Security: firewall, SSH, key-based auth, IAM basics.
* **Thực hành:**

  * Tạo EC2 instance, SSH vào, cài Nginx, deploy 1 app nhỏ.
  * Setup monitoring cơ bản (top, iostat, htop, systemctl).

#### 🔹 Tuần 3–4: AWS core services

* **Vững 6 dịch vụ chính:** EC2, S3, IAM, RDS, CloudWatch, VPC.
* **Hiểu** auto-scaling, ALB, Route53, CloudFront.
* **Hands-on project:**

  * Triển khai 1 web app (NodeJS hoặc Python) trên EC2, RDS, S3.
  * Setup CloudWatch alert + log aggregation.

📘 Tài nguyên:

* AWS Skill Builder Free Labs
* “AWS Certified Solutions Architect Associate” (Udemy hoặc A Cloud Guru)

---

### ⚙️ **Tháng 2: Container + Infrastructure as Code + Monitoring**

**🎯 Mục tiêu:** Làm chủ Docker, Kubernetes, Terraform, và observability stack.

#### 🔹 Tuần 5–6: Docker & Kubernetes

* Docker image, network, volume, multi-stage build.
* Kubernetes: Pod, Deployment, Service, Ingress, ConfigMap, Secret, RBAC.
* Helm & Kustomize.
* **Hands-on project:**

  * Viết Dockerfile cho app của bạn.
  * Deploy app đó lên local Kubernetes (Minikube hoặc Kind).
  * Tạo manifest YAML + Helm chart.

#### 🔹 Tuần 7–8: Terraform + Monitoring

* Terraform: module, state, remote backend, variable, output.
* Tạo AWS infrastructure (VPC + EC2 + RDS) bằng Terraform.
* Datadog hoặc Prometheus + Grafana:

  * Metric, dashboard, alert.
  * Viết alert rule cho CPU/memory/network latency.
* **Hands-on project:**

  * Tự động hóa deploy app qua Terraform + CI/CD (GitHub Actions).
  * Monitor metrics qua Datadog hoặc Prometheus.

📘 Tài nguyên:

* KodeKloud (K8s & Terraform labs)
* Datadog tutorials
* “Terraform Up & Running” – O’Reilly

---

### 🚀 **Tháng 3: Reliability, Security, Incident Response + Interview Prep**

**🎯 Mục tiêu:** Sẵn sàng cho phỏng vấn kỹ thuật & behavioral, có demo thực tế.

#### 🔹 Tuần 9–10: Reliability & Incident

* Hiểu khái niệm **SLA / SLO / SLI**.
* Viết **Postmortem report** cho 1 incident giả định.
* Thực hành: simulate downtime → log analysis → rollback.
* Hiểu cách làm **capacity planning, scaling**, và **error budget**.

#### 🔹 Tuần 11: Security & Compliance

* AWS IAM policy design.
* Secrets management (AWS Secret Manager, KMS).
* Basic compliance: PCI DSS, SOC2 (hiểu ở mức khái niệm).
* Network isolation: Public/Private subnet, NAT, bastion.

#### 🔹 Tuần 12: Phỏng vấn mô phỏng

* **Technical (English):**

  * “Design a reliable web app architecture on AWS.”
  * “How do you detect and respond to incidents?”
  * “How would you monitor a Kubernetes cluster?”
* **Behavioral (English):**

  * “Tell me about a time you solved a production issue.”
  * “How do you prioritize when facing multiple incidents?”
* **Hands-on Demo:**

  * Deploy mini system có:

    * Backend containerized (NodeJS/Python)
    * Terraform infra (AWS)
    * CI/CD (GitHub Actions)
    * Monitoring (Datadog/Grafana)
  * Viết README + Diagram + SLO report

📘 Tài nguyên:

* Google SRE Book (free online)
* Money Forward Tech Blog: [https://moneyforward.com/engineers_blog/](https://moneyforward.com/engineers_blog/)
* Interview practice:

  * systemdesign.one
  * techinterviewhandbook.org

---

## 🧩 CẤU TRÚC PROJECT DEMO (nên có khi apply)

```
/infra
  ├── main.tf              # Terraform infra (EC2, RDS, VPC)
  ├── variables.tf
/app
  ├── Dockerfile
  ├── src/
  ├── k8s/                 # K8s YAML or Helm
/monitoring
  ├── prometheus.yml
  ├── grafana-dashboard.json
/.github/workflows
  ├── deploy.yml           # CI/CD pipeline
README.md
```

* Có hình **architecture diagram**
* Ghi rõ metrics bạn theo dõi: latency, CPU, error rate
* Có mô phỏng incident + recovery log

---

## 🎯 Sau 3 tháng bạn đạt được:

✅ Hiểu và triển khai stack DevOps hiện đại (AWS + K8s + Terraform + Monitoring).
✅ Có 1 **portfolio thực chiến** chứng minh năng lực.
✅ Tự tin phỏng vấn bằng tiếng Anh, cả technical lẫn behavioral.
✅ Đủ kiến thức để apply Money Forward hoặc các công ty tầm tương đương (Mercari, PayPay, SmartNews).

---

Bạn có muốn mình **tạo bản kế hoạch chi tiết theo ngày (90 ngày)** gồm:

* task học/lab cụ thể mỗi ngày,
* tài nguyên (docs, video, repo),
* checkpoint hàng tuần,
  để bạn có thể copy vào **Notion hoặc Google Sheet** không?
  Nếu có, mình sẽ tạo luôn version dành riêng cho **DevOps/SRE – Money Forward Interview Prep**.

# AWS Certified CloudOps Engineer – Associate (SOA-C03)
## Tài Liệu Ôn Tập Toàn Diện — Phiên Bản Nâng Cao

---

## 📋 TỔNG QUAN KỲ THI

| Thông tin | Chi tiết |
|---|---|
| Tên kỳ thi | AWS Certified CloudOps Engineer – Associate (SOA-C03) |
| Hiệu lực | Từ **30/09/2025** (thay thế SOA-C02) |
| Số câu có điểm | **50 câu** (+ 15 câu unscored, không báo trước) |
| Loại câu | Multiple choice (1/4) và Multiple response (≥2/5+) |
| Thang điểm | 100–1,000 — **Điểm đạt: ≥ 720** |
| Mô hình tính điểm | **Compensatory** — không cần đạt từng domain riêng lẻ |
| Kinh nghiệm yêu cầu | ≥ 1 năm deploy/manage/troubleshoot/networking/security trên AWS |

### Phân Bổ Domain

| Domain | Nội dung | % |
|---|---|---|
| **1** | Monitoring, Logging, Analysis, Remediation & Performance Optimization | **22%** |
| **2** | Reliability and Business Continuity | **22%** |
| **3** | Deployment, Provisioning & Automation | **22%** |
| **4** | Security and Compliance | **16%** |
| **5** | Networking and Content Delivery | **18%** |

### Thay Đổi Chính So Với SOA-C02

| Thêm mới (SOA-C03) | Xoá (từ SOA-C02) |
|---|---|
| CloudWatch Agent cho ECS/EKS clusters | S3 static website hosting (Task 5.2) |
| AWS CDK (Task 3.1) | Domain 6: Cost & Performance Optimization (gộp vào Domain 1) |
| Enforce compliance requirements – Region/service (Task 4.1) | — |
| CloudWatch network monitoring services (Task 5.3) | — |
| Performance Optimization (từ Domain 6 → Domain 1) | — |

---

## 🧭 MAP BLUEPRINT SOA-C03 THEO DOMAIN/TASK

> Phần này dùng để đọc lại ghi chú theo đúng blueprint bạn cung cấp. Các section phía dưới vẫn giữ kiến thức theo service, nhưng khi ôn nên luôn quay lại task/skill tương ứng để tránh học lệch sang service ngoài phạm vi.

| Domain | Task cần nắm | Section chính trong file |
|---|---|---|
| **Domain 1** | Metrics, alarms, filters; remediation; performance optimization | 1.1–1.15, Key Facts CloudWatch/EBS/S3/RDS |
| **Domain 2** | Scalability/elasticity; HA/resilience; backup/restore | 2.1–2.8, Auto Scaling/ELB/Route 53/AWS Backup |
| **Domain 3** | Provisioning; deployment; automation existing resources | 3.1–3.11, CloudFormation/CDK/Image Builder/SSM/EventBridge/Lambda/Terraform |
| **Domain 4** | IAM/compliance; data and infrastructure protection | 4.1–4.13, IAM/KMS/ACM/Secrets/Security Hub/GuardDuty/Config |
| **Domain 5** | VPC/connectivity; DNS/content delivery; network troubleshooting | 5.1–5.13, VPC/Endpoints/TGW/Route 53/CloudFront/Flow Logs |

### Cách Ưu Tiên Khi Ôn

1. Nếu câu hỏi có **monitor/remediate/metric/log/alarm** → bắt đầu từ Domain 1.
2. Nếu câu hỏi có **scale, HA, failover, backup, RTO/RPO** → bắt đầu từ Domain 2.
3. Nếu câu hỏi có **provision, deploy, CloudFormation/CDK, runbook, automation** → bắt đầu từ Domain 3.
4. Nếu câu hỏi có **permission denied, encryption, secret, finding, compliance, account guardrail** → bắt đầu từ Domain 4.
5. Nếu câu hỏi có **routing, DNS, endpoint, private connectivity, cache, flow logs** → bắt đầu từ Domain 5.


---

## 🧪 ĐÁNH GIÁ KHẮT KHE THEO GÓC NHÌN RA ĐỀ SOA-C03

> Tiêu chuẩn đánh giá: một mục chỉ được xem là “đủ ôn thi” nếu trả lời được 4 câu: **khi nào dùng**, **khi nào không dùng**, **metric/log/event nào chứng minh**, và **bước remediation nào ít rủi ro nhất**.

| Domain | Mức độ hiện tại | Thiếu nếu ra đề khó | Bổ sung bắt buộc trước mock exam |
|---|---|---|---|
| **Domain 1: Monitoring, Logging, Analysis, Remediation & Performance Optimization** | Bao phủ CloudWatch/CloudTrail/SSM/EBS/S3/RDS khá tốt. | Cần luyện thêm alarm action thực tế, EventBridge rule troubleshooting, User Notifications, CloudWatch Agent cho ECS/EKS, và mapping performance metric -> remediation. | Tạo bảng scenario: `metric/log/API event -> alarm/rule -> SNS/EventBridge -> Lambda/SSM -> audit`. Luyện phân biệt CloudWatch vs CloudTrail vs Config vs VPC Flow Logs. |
| **Domain 2: Reliability & Business Continuity** | Có DR, ASG, ELB, Route 53, Backup. | Dễ thiếu bẫy về Multi-AZ vs read replica, Route 53 alarm-based health check cho private resource, database scaling, AWS Backup cross-account/cross-region/vault lock. | Luyện theo RTO/RPO/cost. Học rõ: Multi-AZ = HA/failover; read replica = scale đọc/DR thủ công; PITR/snapshot/backup restore thường tạo resource mới. |
| **Domain 3: Deployment, Provisioning & Automation** | CloudFormation/CDK/Image Builder/SSM đã có. | Còn cần mạnh hơn ở lỗi triển khai: subnet sizing, `iam:PassRole`, StackSets permission model, Terraform state/import/drift, deployment strategy chọn theo downtime risk. | Với mỗi lỗi deploy, phải biết log/API để kiểm: CloudFormation events, CloudTrail, cfn logs, SSM Session Manager, `terraform plan`. |
| **Domain 4: Security & Compliance** | IAM/KMS/ACM/Secrets/Security Hub/GuardDuty/Inspector/Macie đã có. | Cần đánh giá AccessDenied theo đầy đủ policy layers; data classification còn nên gắn với control cụ thể; Trusted Advisor remediation cần EventBridge/SNS/SSM flow. | Học thứ tự debug quyền: explicit deny, SCP, permission boundary, session policy, identity policy, resource policy, endpoint policy, KMS key policy. |
| **Domain 5: Networking & Content Delivery** | Nền VPC/NACL/SG/TGW/CloudFront/Route 53 tốt. | Cần thêm Route 53 Resolver query logging, DNS Firewall audit, CloudFront cache policy vs origin request policy, OAC + SSE-KMS, CloudWatch network metrics, NAT cost optimization. | Luyện checklist network path: subnet route -> SG -> NACL -> DNS -> endpoint/private path -> service policy -> log evidence. |

### Nội Dung Thiếu Cần Bổ Sung Vào Bộ Câu Hỏi

| Nhóm câu hỏi còn thiếu | Vì sao nguy hiểm | Cần thêm dạng câu hỏi |
|---|---|---|
| **Multiple response có nhiều đáp án đúng** | SOA-C03 không chỉ hỏi single choice; nhiều câu yêu cầu chọn 2-3 hành động đúng. | “Chọn 2 bước ít gián đoạn nhất để remediate alarm EC2/RDS/VPC.” |
| **Troubleshooting dựa trên metric/log cụ thể** | Người học dễ nhớ service nhưng không biết evidence. | Cho metric như `StatusCheckFailed_System`, `HealthyHostCount`, `ThrottledRequests`, `VolumeQueueLength`, `PercentIOLimit`, yêu cầu chọn nguyên nhân/remediation. |
| **IAM AccessDenied nhiều lớp** | Distractor thường chỉ kiểm identity policy, bỏ qua SCP/KMS/endpoint/resource policy. | Tạo case có SCP allow/deny, bucket policy, KMS key policy, VPC endpoint policy. |
| **EventBridge delivery failure** | Nhiều người biết rule nhưng không biết target policy/DLQ/retry. | Case Lambda/SNS/SQS target không nhận event, hỏi kiểm permission nào. |
| **CloudFront cache/OAC/KMS** | Dễ nhầm cache behavior, origin request policy và bucket policy. | Case S3 private origin 403, stale object, cache hit ratio thấp, query string làm miss cache. |
| **Backup restore theo RTO/RPO** | Dễ chọn “backup” chung chung mà không đúng thời gian/chi phí. | So sánh AWS Backup, snapshot, PITR, Aurora Backtracking, S3 versioning/Object Lock. |
| **Third-party IaC operations** | Blueprint có Terraform/Git nhưng không yêu cầu thiết kế pipeline sâu. | Case drift, remote state lock, import resource, plan review, rollback bằng revert commit. |

### Những Phần Nên Giảm Ưu Tiên Vì Dễ Lệch Scope

- Không học sâu **thiết kế distributed architecture**, **thiết kế CI/CD pipeline**, **thiết kế hybrid/multi-VPC networking** ở mức architect; SOA-C03 kiểm vận hành, triển khai, troubleshoot.
- Không ưu tiên dịch vụ ngoài scope: **CloudHSM, Neptune, Timestream, App Mesh, Cloud WAN, FSx for OpenZFS, Amazon EMR, Amazon MSK**.
- Không học CloudWatch/CloudTrail/Security Hub theo định nghĩa. Phải học theo câu hỏi: “phát hiện ở đâu, chứng minh bằng log nào, remediate bằng gì, audit lại thế nào”.

---

## 🔵 DOMAIN 1: Monitoring, Logging, Analysis, Remediation & Performance Optimization (22%)

---

### 1.1 Amazon CloudWatch — Metrics

#### Basic vs Detailed Monitoring

| | Basic Monitoring | Detailed Monitoring |
|---|---|---|
| Tần suất | **5 phút** | **1 phút** |
| Chi phí | Miễn phí | **Phí thêm** |
| Mặc định | ✅ | ❌ (phải bật thủ công) |
| Cần thiết khi | Quan sát thông thường | ASG scale nhanh, monitoring chặt chẽ |

> **Cần phân biệt rõ 2 loại metrics:**
> - **EC2 instance metrics** (CPUUtilization, DiskReadBytes, NetworkIn...): Basic = 5 phút, Detailed = 1 phút **có phí**.
> - **Auto Scaling Group metrics** (GroupInServiceInstances, GroupPendingInstances...): Luôn 1 phút, **miễn phí** (nhưng phải bật riêng).

#### Metrics CloudWatch Không Thu Thập Tự Động

CloudWatch **không** tự thu thập những metrics sau từ EC2 → Cần **CloudWatch Agent**:
- **Memory utilization** (RAM usage)
- **Disk swap utilization**
- **Disk space utilization**
- **Page file utilization** (Windows)
- **Log files** từ OS/application

#### CloudWatch Agent

- Thu thập **custom metrics** và **logs** từ EC2 (Linux & Windows), ECS, EKS.
- Cấu hình qua file JSON hoặc **Systems Manager Parameter Store**.
- Cần **IAM role** với quyền `CloudWatchAgentServerPolicy`.
- Dữ liệu gửi vào **CloudWatch Metrics** và **CloudWatch Logs**.

#### EC2 Instance Types — CPU Credits (T-series)

- **T3, T3a, T4g**: Burstable performance instances.
- Tích lũy **CPU credits** khi CPU < baseline → Dùng credits khi cần burst.
- Metrics quan trọng: `CPUCreditBalance`, `CPUSurplusCreditsCharged`.
- Khi `CPUCreditBalance = 0` → Instance throttled → **Upgrade sang instance type khác** hoặc dùng **Unlimited mode**.

---

### 1.2 Amazon CloudWatch — Alarms

#### Alarm States

| State | Ý nghĩa |
|---|---|
| **OK** | Metric trong ngưỡng bình thường |
| **ALARM** | Metric vượt ngưỡng threshold |
| **INSUFFICIENT_DATA** | Không đủ dữ liệu để xác định (thường khi mới tạo) |

#### Alarm Actions

| Action | Mô tả |
|---|---|
| **EC2 Action** | Stop, Start, Terminate, **Recover** instance |
| **Auto Scaling Action** | Trigger scale out/in |
| **SNS Notification** | Gửi thông báo đến SNS topic |
| **Lambda** | Invoke Lambda function (qua EventBridge) |
| **Systems Manager OpsItem** | Tạo OpsItem trong Systems Manager |

#### Composite Alarms

- Kết hợp nhiều alarm bằng logic **AND/OR/NOT** → Giảm false positives (alarm noise).
- Hữu ích trong môi trường phức tạp.

#### CloudWatch Alarm — EC2 Recovery

- Metric: **`StatusCheckFailed_System`** (lỗi từ AWS infrastructure)
- Action: **Recover** → Instance migrate sang host mới, giữ nguyên:
  - Instance ID, Private IP, Elastic IP, Public IPv4, metadata
  - **Mất**: RAM data (in-memory data)
- **`StatusCheckFailed_Instance`**: Lỗi OS/application → Cần user xử lý (reboot, check OS logs).
- **Stop + Start** thủ công cũng migrate sang host mới (giải quyết system status check failure).
- **Reboot** → Giữ nguyên host, không giải quyết system status check failure.

---

### 1.3 Amazon CloudWatch — Logs

#### CloudWatch Logs Architecture

```
EC2/Lambda/Container → CloudWatch Agent / SDK → Log Groups → Log Streams → Log Events
```

| Thành phần | Mô tả |
|---|---|
| **Log Group** | Container cho log streams cùng loại (ví dụ: /aws/lambda/my-function) |
| **Log Stream** | Sequence of log events từ một source (một EC2 instance, một Lambda execution) |
| **Log Event** | Một dòng log với timestamp |
| **Retention** | Cấu hình per log group (1 ngày → không bao giờ xóa); mặc định: **không bao giờ hết hạn** |
| **Metric Filters** | Trích xuất metrics từ log patterns → Tạo custom CloudWatch metrics |

#### CloudWatch Logs Insights

- **Query language** để phân tích log data trong CloudWatch Logs.
- Tìm kiếm nhanh trên hàng triệu log events.
- Hỗ trợ aggregation, sorting, filtering.
- Có thể query **nhiều log groups** cùng lúc (cross-log-group query).
- Kết quả có thể **add vào CloudWatch Dashboard**.

#### CloudWatch Contributor Insights

- Phân tích log data để tìm **top contributors** gây ra vấn đề.
- Ví dụ: Top 10 IP addresses gây nhiều request nhất, top customer IDs gây nhiều lỗi.
- Hỗ trợ **VPC Flow Logs, CloudTrail, custom logs**.
- Rule-based: Định nghĩa key fields để tổng hợp.

#### CloudWatch Logs Subscriptions

- **Subscription Filters**: Stream log data real-time đến:
  - **Kinesis Data Streams**
  - **Kinesis Data Firehose**
  - **AWS Lambda**
- Dùng để phân tích real-time hoặc lưu vào Elasticsearch/S3.

---

### 1.4 Amazon CloudWatch — Dashboards & Synthetics

#### CloudWatch Dashboards

- **Cross-account, cross-region** metrics/alarms trong một giao diện.
- Có thể **share** dashboards với người ngoài (không cần AWS account).
- Alarm ở trạng thái ALARM hiển thị **màu đỏ**.
- Hỗ trợ: Line charts, bar charts, number widgets, text, logs, alarms.
- **Metric Math**: Tính toán mathematical expressions trên nhiều metrics.
  - Ví dụ: Tổng NetworkIn của tất cả EC2 instances bằng `SUM(METRICS())`.

#### Amazon CloudWatch Synthetics

- Tạo **canaries** (scripts) để monitor endpoints và APIs.
- Canary chạy theo lịch, simulate user actions (GET/POST requests, browser interactions).
- Alert khi endpoint fail, latency tăng, hoặc content thay đổi.
- Kết quả lưu vào **S3** (screenshots, HAR files, logs).

#### CloudWatch RUM (Real User Monitoring)

- Thu thập **thực tế** performance data từ user browsers.
- Theo dõi page load time, JavaScript errors, user journeys.

---

### 1.5 Amazon EventBridge

#### Event Bus Types

| Loại | Mô tả |
|---|---|
| **Default event bus** | Nhận events từ AWS services (mặc định) |
| **Custom event bus** | Cho custom applications |
| **Partner event bus** | Từ AWS Partner SaaS (Zendesk, Datadog...) |

#### EventBridge Rules

- **Event pattern rules**: Match events theo pattern → Trigger targets.
- **Scheduled rules**: Cron hoặc rate expressions → Trigger targets theo lịch.
- **Targets**: Lambda, SQS, SNS, Step Functions, ECS, Systems Manager Automation, Kinesis, API Gateway, v.v.

#### EventBridge Pipes

- Point-to-point connection giữa event source và target (với filtering/enrichment/transformation).

#### Dead-Letter Queue (DLQ)

- Khi EventBridge không deliver được event → Gửi vào **SQS DLQ**.
- Tránh mất events.

---

### 1.6 AWS CloudTrail

#### CloudTrail Fundamentals

- Ghi lại **mọi API call** (management events mặc định): Console, CLI, SDK, services.
- **Management Events** (Control Plane): Tạo/xóa/thay đổi resources (bật mặc định).
- **Data Events** (Data Plane): S3 object-level operations (GetObject, PutObject), Lambda Invoke, DynamoDB — **Phí thêm, phải bật thủ công**.
- **Insights Events**: Phát hiện **unusual API activity** (đột biến bất thường) — Phải bật.

#### CloudTrail Trail Types

| | Single-region Trail | Multi-region Trail |
|---|---|---|
| Phạm vi | Một region | Tất cả regions |
| Khuyến nghị | ❌ | ✅ (best practice) |

#### CloudTrail Best Practices

- Enable **multi-region trail** → Ghi lại activity trên tất cả regions.
- Enable **log file integrity validation** → S3 hash files để detect tampering.
- Gửi logs đến **S3 bucket** (có thể encrypt bằng KMS).
- Bật **CloudTrail Insights** để phát hiện bất thường.
- **Không** dùng CloudTrail để troubleshoot OS-level issues (dùng CloudWatch Logs).

#### CloudTrail vs CloudWatch vs VPC Flow Logs

| | CloudTrail | CloudWatch Logs | VPC Flow Logs |
|---|---|---|---|
| Thu thập | **API calls** | **Application/OS logs, metrics** | **IP traffic** |
| Dùng để | Audit, compliance, governance | Operational monitoring, debugging | Network troubleshoot, security |
| Ví dụ | Ai đã xóa S3 bucket? | Ứng dụng báo lỗi gì? | IP nào đang tấn công? |

---

### 1.7 Amazon Managed Service for Prometheus (AMP) & Amazon Managed Grafana

#### Amazon Managed Service for Prometheus (AMP)

- Fully managed **Prometheus-compatible** monitoring service.
- Thu thập metrics từ **EKS, ECS, EC2** qua Prometheus remote write.
- Query bằng **PromQL**.
- Tích hợp với **Amazon Managed Grafana** để visualize.
- **Không cần** quản lý Prometheus infrastructure.

#### Amazon Managed Grafana

- Fully managed **Grafana** visualization service.
- Kết nối với nhiều data sources: **AMP, CloudWatch, Athena, OpenSearch, Timestream, Redshift**, v.v.
- Tích hợp với **IAM Identity Center** cho authentication.
- Phù hợp cho **multi-source dashboards** (CloudWatch metrics + Prometheus metrics trên cùng dashboard).

> **Khi nào dùng gì:**
> - EC2/Lambda/RDS metrics cơ bản → **CloudWatch**
> - Kubernetes/container metrics nâng cao → **AMP + Managed Grafana**
> - Multi-source dashboard → **Managed Grafana**

---

### 1.8 AWS Systems Manager

#### SSM Capabilities Quan Trọng

| Capability | Mô tả |
|---|---|
| **Patch Manager** | Tự động patch EC2/on-prem instances theo patch baseline; hỗ trợ Windows, Amazon Linux, RHEL, SUSE, Ubuntu |
| **Automation** | Chạy runbooks (pre-defined hoặc custom) để automate tasks; hỗ trợ AWS SDKs và custom scripts |
| **Run Command** | Chạy scripts/commands trên instances mà **không cần SSH** |
| **Session Manager** | **Browser-based shell access** đến EC2 — không cần SSH key, không cần bastion host, không cần mở port 22 |
| **Parameter Store** | Lưu trữ configuration data và **secrets** (plaintext hoặc encrypted với KMS); có Standard và Advanced tiers |
| **Inventory** | Thu thập thông tin về installed software, files, registry keys, network config |
| **State Manager** | Duy trì desired state của instances (ví dụ: luôn cài agent, luôn enable firewall) |
| **OpsCenter** | Quản lý và remediate operational issues (OpsItems) |
| **Distributor** | Distribute software packages đến instances |
| **Maintenance Window** | Lên lịch maintenance tasks |

#### SSM Session Manager vs SSH

| | Session Manager | SSH |
|---|---|---|
| Mở port 22 | ❌ Không cần | ✅ Cần |
| Bastion host | ❌ Không cần | Thường cần (nếu private subnet) |
| Key pair | ❌ Không cần | ✅ Cần |
| Audit | ✅ Tự động log vào CloudTrail/CloudWatch/S3 | ❌ Không tự động |
| Private subnet | ✅ Hoạt động | ❌ Cần NAT/Bastion |

#### SSM Parameter Store vs Secrets Manager

| | Parameter Store | Secrets Manager |
|---|---|---|
| **Chi phí** | Standard tier: **Miễn phí**; Advanced: có phí | **Có phí** per secret |
| **Automatic rotation** | ❌ Không native | ✅ Rotation tự động (Lambda-backed) |
| **Encryption** | Optional (KMS) | **Bắt buộc KMS** |
| **Versioning** | ✅ | ✅ |
| **Cross-account access** | ❌ Khó | ✅ Dễ |
| **Dùng cho** | App config, non-sensitive settings | **Database passwords, API keys, sensitive secrets** |

---

### 1.9 AWS Trusted Advisor

#### 5 Pillars của Trusted Advisor

1. **Cost Optimization**: Idle resources, Reserved Instance recommendations, unattached EBS volumes.
2. **Performance**: High-utilization EC2 instances, CloudFront content delivery optimization.
3. **Security**: MFA on root, open ports, S3 public buckets, IAM use, CloudTrail status.
4. **Fault Tolerance**: EBS snapshots age, RDS Multi-AZ, Auto Scaling, Route 53 failover.
5. **Service Limits**: Usage approaching service quotas (80% threshold cảnh báo).

#### Trusted Advisor Access Levels

| Loại | Checks có sẵn |
|---|---|
| **Basic/Developer support** | 6 core security checks + Service Limits |
| **Business/Enterprise support** | **Tất cả** checks + API access + CloudWatch integration |

> Với Business+ support: Có thể tạo **CloudWatch Alarm** khi Trusted Advisor check fail.

---

### 1.10 Performance Optimization — EBS

#### EBS Volume Types (Chi tiết)

| Type | IOPS | Throughput | Max Size | Đặc điểm |
|---|---|---|---|---|
| **gp2** | 3 IOPS/GB, tối đa 16,000 | 250 MB/s | 16 TB | Cũ hơn, IOPS linked với size |
| **gp3** | 3,000 baseline, tối đa **16,000** (độc lập với size) | **1,000 MB/s** | 16 TB | **Nên dùng thay gp2** |
| **io1** | Tối đa **64,000** (Nitro); 32,000 (non-Nitro) | 1,000 MB/s | 16 TB | Mission-critical, database |
| **io2** | Tối đa **64,000** (Nitro); 256,000 với io2 Block Express | 4,000 MB/s | 64 TB | Durability 99.999% |
| **st1** | 500 | **500 MB/s** | 16 TB | Sequential read/write (log, ETL) |
| **sc1** | 250 | 250 MB/s | 16 TB | Cold data, lowest cost |

> - Để đạt **>100,000 IOPS**: Dùng **io1/io2** + RAID 0 kết hợp nhiều volumes.
> - `AutoEnableIO`: Tự động re-enable I/O khi volume ở potentially inconsistent state → **Không tăng IOPS**.
> - **gp3 có thể provision IOPS độc lập với size** (gp2 thì không).

#### EBS Multi-Attach

- Chỉ hỗ trợ **io1/io2**.
- Gắn một EBS volume vào **nhiều EC2 instances** cùng AZ.
- Dùng cho clustered applications (Oracle RAC pattern trên AWS không phải RDS).

#### EBS Snapshots

- **Incremental**: Chỉ lưu changes kể từ snapshot trước.
- Lưu trong **S3** (managed by AWS, không thấy trong S3 console).
- **Fast Snapshot Restore (FSR)**: Khởi tạo volume từ snapshot mà không cần warming period.
- **Amazon Data Lifecycle Manager (DLM)**: Tự động tạo/giữ/xóa EBS snapshots theo policy.
- **Cross-region copy**: Copy snapshot sang region khác (cho DR).

---

### 1.11 Performance Optimization — S3

#### S3 Performance Best Practices

- **S3 Transfer Acceleration**: Upload qua CloudFront edge locations → Tối ưu cho users xa region.
- **Multipart Upload**: Khuyến nghị cho files **> 100 MB**, bắt buộc cho **> 5 GB**.
- **Byte-range fetches**: Download nhiều byte ranges song song → Tăng throughput.
- **Prefix optimization**: S3 tự động scale theo prefix — **phân tán keys** qua nhiều prefixes để tăng throughput (3,500 PUT/s và 5,500 GET/s per prefix).
- **S3 Intelligent-Tiering**: Tự động chuyển objects giữa tiers theo access patterns (không cần lifecycle rule thủ công).

#### S3 Storage Classes

| Class | Availability | Min Storage Duration | Dùng khi |
|---|---|---|---|
| **S3 Standard** | 99.99% | None | Frequent access |
| **S3 Intelligent-Tiering** | 99.9% | None | Unknown/changing access patterns |
| **S3 Standard-IA** | 99.9% | 30 ngày | Infrequent access, cần retrieval nhanh |
| **S3 One Zone-IA** | 99.5% (1 AZ) | 30 ngày | Infrequent, có thể tái tạo data |
| **S3 Glacier Instant Retrieval** | 99.9% | 90 ngày | Archive, retrieval trong milliseconds |
| **S3 Glacier Flexible Retrieval** | 99.99% | 90 ngày | Archive, retrieval trong phút–giờ |
| **S3 Glacier Deep Archive** | 99.99% | 180 ngày | **Rẻ nhất**, retrieval 12–48 giờ |

---

### 1.12 Performance Optimization — EFS & FSx

#### Amazon EFS

| Performance Mode | Đặc điểm | Dùng khi |
|---|---|---|
| **General Purpose** (mặc định) | Low latency | Web servers, CMS, home directories |
| **Max I/O** | Higher throughput, higher latency | Big data, media processing, parallel workloads |

| Throughput Mode | Đặc điểm |
|---|---|
| **Bursting** (mặc định) | Throughput tỷ lệ với file system size; credit system |
| **Provisioned** | Fixed throughput bất kể size |
| **Elastic** | Tự động scale in/out theo workload |

- EFS **Multi-AZ** mặc định (Standard tier); EFS One Zone: một AZ, rẻ hơn.
- Hỗ trợ **NFS protocol** (Linux only).
- **EFS Lifecycle Management**: Tự động chuyển files ít dùng sang EFS-IA.

#### Amazon FSx

| FSx Type | Protocol | Dùng cho |
|---|---|---|
| **FSx for Windows File Server** | SMB | Windows workloads, Active Directory integration |
| **FSx for Lustre** | Lustre | High-performance computing (HPC), ML, video processing |
| **FSx for NetApp ONTAP** | NFS, SMB, iSCSI | Enterprise multi-protocol workloads |
| **FSx for OpenZFS** | NFS | **Ngoài phạm vi SOA-C03 theo blueprint đã đưa**; chỉ đọc nếu gặp môi trường thực tế |

> FSx for Lustre có thể **tích hợp trực tiếp với S3** làm data repository (data lake workloads).

---

### 1.13 Performance Optimization — RDS & Databases

#### Amazon RDS Performance Tools

- **Performance Insights**: Visualize database load (DBLoad), top SQL queries, wait events. **Proactive recommendations** cho query optimization.
- **Enhanced Monitoring**: OS-level metrics (CPU, memory, I/O) real-time, granularity đến **1 giây**.
- **RDS Proxy**: Connection pooling cho Lambda/serverless → Giải quyết "too many connections".
  - Giảm số lượng connections đến RDS.
  - **Failover** nhanh hơn (không cần reconnect).
  - Hỗ trợ IAM authentication và Secrets Manager.

#### ElastiCache — So Sánh Redis vs Memcached

| | Redis | Memcached |
|---|---|---|
| **Data structures** | Strings, hashes, lists, sets, sorted sets, streams | Strings only |
| **Multi-AZ** | ✅ (Global Datastore, cluster mode) | ❌ |
| **Read Replicas** | ✅ (tối đa 5) | ❌ |
| **Persistence** | ✅ (RDB snapshots, AOF) | ❌ |
| **Pub/Sub** | ✅ | ❌ |
| **Lua scripting** | ✅ | ❌ |
| **Online resharding** | ✅ (cluster mode enabled) | ❌ |
| **Auto Discovery** | ❌ | ✅ |
| **Multi-threaded** | ❌ (single-threaded) | ✅ |
| **Scaling khi evictions** | Scale up node type / add replicas | **Thêm nodes** |
| **Dùng khi** | Complex data types, persistence, HA, Pub/Sub | Simple caching, multi-threading, horizontal scale |

#### Amazon DynamoDB Performance

- **DAX (DynamoDB Accelerator)**: In-memory cache, giảm read latency từ milliseconds → **microseconds**.
- **Auto Scaling**: Tự động điều chỉnh provisioned read/write capacity.
- **On-demand mode**: Pay-per-request, không cần capacity planning.

---


### 1.14 Task 1.1–1.2 — Monitoring, Alarm, Event, Remediation Flow

#### Luồng Chuẩn Trong Đề Thi

```
Metric/Log/CloudTrail event -> CloudWatch Alarm hoặc EventBridge Rule -> SNS/User Notifications/Lambda/SSM Automation -> Remediation -> Audit bằng CloudTrail/Config
```

| Nhu cầu | Dịch vụ/chức năng nên chọn | Bẫy thường gặp |
|---|---|---|
| Alert theo metric định lượng | **CloudWatch Alarm** | Alarm không đọc trực tiếp log raw; cần metric filter nếu xuất phát từ log |
| Alert theo pattern trong log | **CloudWatch Logs Metric Filter** + Alarm | Metric filter tạo custom metric trước, rồi alarm trên metric đó |
| Event gần real-time từ AWS API/service | **EventBridge Rule** dựa trên CloudTrail/service event | CloudTrail để audit; EventBridge để route event |
| Gửi email/SMS/webhook | **SNS topic** hoặc **AWS User Notifications** | SNS là target phổ biến của alarm; User Notifications gom thông báo đa account/region |
| Tự động sửa lỗi EC2/SSM managed node | **SSM Automation runbook** | Instance cần SSM Agent, IAM instance profile, network path tới SSM endpoints |
| Remediate bằng code nhỏ | **Lambda** | Kiểm tra timeout, retry, DLQ/destination, permission invoke |
| Nhiều alarm gây nhiễu | **Composite Alarm** | Composite alarm chỉ chuyển state theo alarm con; không thay metric gốc |

#### CloudWatch Alarm Actions Cần Nhớ

- Alarm có thể gửi **SNS notification**, chạy **EC2 action** (stop/start/reboot/recover), chạy **Auto Scaling action**, tạo **Systems Manager OpsItem/Incident**, hoặc invoke Lambda theo integration được hỗ trợ/qua EventBridge.
- **Composite alarm** hữu ích khi cần `ALARM(A) AND ALARM(B)` để tránh false positive, ví dụ CPU cao **và** request latency cao.
- Nếu alarm không kích hoạt action: kiểm tra state thật sự có đổi sang `ALARM` không, action có enabled không, SNS topic policy/KMS policy có cho CloudWatch publish không, và metric có thiếu datapoint không.

#### CloudWatch Agent Cho EC2/ECS/EKS

| Môi trường | Cách dùng chính | Điểm kiểm tra khi lỗi |
|---|---|---|
| **EC2 Linux/Windows** | Cài agent, cấu hình JSON hoặc SSM Parameter Store, gắn IAM role | `CloudWatchAgentServerPolicy`, region đúng, namespace/log group đúng |
| **ECS trên EC2** | Agent/Fluent Bit thu logs và container metrics | Task execution role, log driver `awslogs`, container insights |
| **ECS Fargate** | Dùng `awslogs`/FireLens và Container Insights | Không SSH vào host; kiểm tra task role/execution role |
| **EKS** | CloudWatch Observability add-on/agent + Fluent Bit | IRSA/service account permission, namespace, daemonset/pod health |

#### EventBridge Troubleshooting

- Rule không chạy: kiểm tra **event pattern** có match event thật không, event đang vào đúng **event bus** không, rule đang enabled không.
- Target không nhận event: kiểm tra **resource-based policy** của target (Lambda/SNS/SQS), IAM role của rule, retry policy và DLQ.
- Sự kiện CloudTrail chậm: EventBridge gần real-time nhưng không phải đồng bộ tức thì; dùng CloudWatch metric/log nếu cần alert theo telemetry liên tục.
- Khi cần lọc/enrich/transform từ source sang target một-một: cân nhắc **EventBridge Pipes** thay vì tự viết Lambda trung gian.

### 1.15 Task 1.3 — Compute/Storage/Database Optimization Checklist

| Resource | Metric/tín hiệu | Hướng tối ưu |
|---|---|---|
| **EC2** | CPU, memory qua agent, `StatusCheckFailed`, network packets/errors, CPU credits | Rightsize bằng Compute Optimizer, đổi family/size, bật detailed monitoring cho ASG cần scale nhanh |
| **EBS** | `VolumeReadOps/WriteOps`, `VolumeQueueLength`, `BurstBalance`, latency | Chuyển gp2 -> gp3, provision IOPS/throughput độc lập, io2 cho database quan trọng |
| **S3** | 503 Slow Down, object size lớn, latency upload xa region | Multipart upload, Transfer Acceleration, lifecycle, DataSync cho migration đồng bộ |
| **EFS** | `PercentIOLimit`, burst credits, throughput utilization | Elastic/Provisioned throughput, lifecycle to IA, DataSync để migrate sang mode phù hợp |
| **RDS/Aurora** | DBLoad, CPU, FreeableMemory, Read/Write IOPS, connections, lock/wait events | Performance Insights, Enhanced Monitoring, read replica, RDS Proxy, scale storage/instance class |
| **DynamoDB** | ThrottledRequests, ConsumedRCU/WCU, hot partition | On-demand/auto scaling, partition key tốt hơn, DAX cho read-heavy cached access |

## 🟢 DOMAIN 2: Reliability and Business Continuity (22%)

---

### 2.1 Disaster Recovery Strategies

#### DR Strategy Spectrum

```
Backup & Restore → Pilot Light → Warm Standby → Multi-Site Active/Active
(RTO/RPO: Cao/Cao) ←————————————————————————→ (RTO/RPO: Thấp/Thấp)
(Chi phí: Thấp nhất) ←——————————————————————→ (Chi phí: Cao nhất)
```

| Strategy | RTO | RPO | Mô tả |
|---|---|---|---|
| **Backup & Restore** | Hours | Hours | Backup data định kỳ, restore khi cần. Chi phí thấp nhất. |
| **Pilot Light** | Minutes–Hours | Minutes–Hours | Core services (database) luôn chạy ở DR; app servers tắt. Khởi động khi cần. |
| **Warm Standby** | Minutes | Seconds–Minutes | Phiên bản scaled-down của production luôn chạy ở DR. Scale up khi failover. |
| **Multi-Site Active/Active** | Near zero | Near zero | Cả hai sites xử lý traffic live. Tốn kém nhất. |

#### RTO vs RPO

- **RTO (Recovery Time Objective)**: Thời gian tối đa được phép downtime từ khi sự cố đến khi restore.
- **RPO (Recovery Point Objective)**: Lượng data mất tối đa được chấp nhận (thời gian giữa backup cuối và sự cố).

---

### 2.2 Amazon EC2 Auto Scaling

#### ASG Scaling Policy Types

| Policy | Cơ chế | Dùng khi |
|---|---|---|
| **Simple Scaling** | Thêm/bớt X instances khi alarm trigger; chờ cooldown | Legacy, đơn giản |
| **Step Scaling** | Thêm/bớt theo bậc thang tỷ lệ với mức vi phạm | Cần scale lớn khi vi phạm nhiều |
| **Target Tracking** | Duy trì metric ở mức target (ví dụ: CPU = 50%) | **Khuyến nghị**, tự động nhất |
| **Scheduled Scaling** | Scale theo lịch cố định (cron) | Biết trước traffic pattern |
| **Predictive Scaling** | Dùng ML dự đoán load và pre-scale | Traffic có chu kỳ |

#### Cooldown Period

- **Mặc định: 300 giây**.
- Sau khi scaling activity, ASG **không** thực hiện thêm scaling cho đến khi cooldown hết.
- Áp dụng cho **Simple Scaling** (không áp dụng cho Target Tracking và Step Scaling — chúng tự quản lý).
- Có thể set **instance warm-up** riêng để loại trừ newly launched instances khỏi health checks.

#### Lifecycle Hooks

- Cho phép thực hiện actions khi instance đang **launching** hoặc **terminating**.
- Instance giữ ở state `Pending:Wait` hoặc `Terminating:Wait`.
- Dùng để: Install software, copy files, drain connections, send notification.
- Default timeout: **3600 giây** (1 giờ), có thể extend.
- Khi hết timeout: Mặc định **ABANDON** (launch) hoặc **CONTINUE** (terminate).

#### Termination Policies

Thứ tự mặc định khi ASG terminate instance:
1. AZ với nhiều instances nhất.
2. Oldest launch template/config.
3. Instance gần với billing hour nhất.

#### EC2 Launch Templates vs Launch Configurations

| | Launch Template | Launch Configuration |
|---|---|---|
| **Versioning** | ✅ Có | ❌ Không |
| **Spot + On-Demand mix** | ✅ | ❌ |
| **Placement groups** | ✅ | ✅ |
| **T2/T3 Unlimited** | ✅ | ❌ |
| **Status** | **Khuyến nghị** | Deprecated (không nên dùng) |

---

### 2.3 Elastic Load Balancing (ELB)

#### ALB vs NLB vs GLB Chi Tiết

| | ALB | NLB | GLB |
|---|---|---|---|
| **Layer OSI** | 7 (HTTP/HTTPS) | 4 (TCP/UDP/TLS) | 3+4 |
| **WebSockets** | ✅ | ✅ | ❌ |
| **Host-based routing** | ✅ | ❌ | ❌ |
| **Path-based routing** | ✅ | ❌ | ❌ |
| **Static IP** | ❌ (dùng Global Accelerator) | ✅ | ❌ |
| **Preserve source IP** | X-Forwarded-For header | ✅ | ✅ |
| **SSL Termination** | ✅ | ✅ | ❌ |
| **Container support** | ✅ | ✅ | — |
| **Dùng cho** | Web apps, microservices | UDP, TCP, static IP, extreme performance | Firewalls, IDS/IPS, security appliances |

#### ELB Features Quan Trọng

- **Connection Draining / Deregistration Delay**: Thời gian chờ để complete in-flight requests trước khi deregister instance (mặc định 300s, range 1–3600s).
- **Sticky Sessions (Session Affinity)**: Route requests từ cùng client đến cùng backend instance. Dùng cookies (Application cookie hoặc ELB-generated cookie).
- **Cross-Zone Load Balancing**:
  - ALB: **Bật mặc định** (không tính phí).
  - NLB/GLB: **Tắt mặc định** (bật sẽ tính phí cross-AZ data transfer).
- **Health Checks**: HTTP, HTTPS, TCP; cấu hình healthy/unhealthy threshold, interval, timeout.
- **Idle Timeout**: Kết nối không active sẽ bị đóng (mặc định 60s cho ALB).

#### ALB Target Groups

- **Instance targets**: Route đến EC2 instances.
- **IP targets**: Route đến IP addresses (bao gồm on-premises IPs qua Direct Connect/VPN).
- **Lambda targets**: Invoke Lambda functions.
- **ALB targets**: Nested ALB.

#### ELB Access Logs

- Disabled by default.
- Khi bật → Gửi đến **S3 bucket cùng region**.
- Ghi: timestamp, client IP, latency, request path, server response, response time.
- Phân tích bằng **Amazon Athena** (query S3 logs).

---

### 2.4 Amazon Route 53

#### Health Checks

| Loại | Mô tả |
|---|---|
| **Health check for endpoint** | Monitor HTTP, HTTPS, TCP endpoint |
| **Health check for other health checks** | Calculated health check (AND/OR của nhiều health checks) |
| **Health check for CloudWatch alarms** | Monitor private resources (EC2 trong private subnet) qua CloudWatch alarm |

> **Private resources không thể được Route 53 health checks trực tiếp** → Dùng **CloudWatch Alarm-based health check**.

#### Route 53 Routing Policies

| Policy | Use Case |
|---|---|
| **Simple** | Một resource duy nhất; không có health check |
| **Failover** | Active-Passive; primary + secondary |
| **Latency** | Multi-region; route đến region low latency nhất |
| **Geolocation** | Route dựa trên quốc gia/continent của user |
| **Geoproximity** | Route dựa trên khoảng cách địa lý; có thể bias với Traffic Flow |
| **Weighted** | Phân chia traffic theo weight (A/B testing, canary deployment) |
| **Multivalue Answer** | Trả về nhiều IP, route 53 check health (giống simple load balancer) |
| **IP-based** | Route dựa trên IP CIDR của client |

#### Alias Record vs CNAME

| | Alias | CNAME |
|---|---|---|
| **Zone apex** | ✅ Được dùng | ❌ Không được |
| **AWS resources** | ✅ (ELB, CloudFront, S3, API GW, Global Accelerator) | ✅ (bất kỳ domain) |
| **DNS query charges** | ❌ Miễn phí | ✅ Tính phí |
| **TTL** | Set bởi Route 53 (không configure) | Configure được |

---

### 2.5 Backup & Restore

#### AWS Backup

- **Centralized backup** cho: EC2, EBS, RDS, Aurora, DynamoDB, EFS, FSx, S3, Storage Gateway.
- **Backup Plan**: Frequency, retention, lifecycle.
- **Backup Vault**: Nơi lưu trữ recovery points; có thể **lock** vault (compliance, WORM).
- **Cross-region backup**: Copy backup sang region khác (cho DR).
- **Cross-account backup**: Copy backup sang AWS account khác.
- AWS Backup **không reboot** EC2 → Không đảm bảo file system integrity cho AMIs.
- Để tạo AMI đảm bảo file system integrity: **Lambda + CreateImage API với reboot parameter** → Schedule bằng EventBridge.

#### RDS/Aurora Backup

| | Automated Backup | Manual Snapshot |
|---|---|---|
| **Kích hoạt** | Mặc định | Thủ công |
| **Retention** | 0–35 ngày (mặc định 7) | Vĩnh viễn (cho đến khi xóa) |
| **Granularity** | Point-in-time (PITR) | Tại thời điểm snapshot |
| **Xóa khi delete DB** | ✅ (trừ khi lưu final snapshot) | ❌ Không tự xóa |

- **Không thể set retention = 0** khi có **Read Replicas**.
- **Aurora**: Backup continuous và incremental (không ảnh hưởng performance).

#### Aurora Backtracking vs PITR vs Restore

| | Backtracking | Point-in-Time Restore | Restore from Snapshot |
|---|---|---|---|
| **Tạo DB mới?** | ❌ Rewind same cluster | ✅ Tạo mới | ✅ Tạo mới |
| **Tốc độ** | Phút | Giờ | Giờ |
| **Giới hạn** | Backtrack window (mặc định 24h, tối đa 72h) | Trong retention period | Bất kỳ snapshot nào |
| **Dùng khi** | Lỗi DELETE/DROP nhanh, cần rollback ngay | Cần restore về điểm cụ thể | Restore từ snapshot cũ |

#### Amazon Aurora Global Database

- Replication đến **nhiều regions** (tối đa 5 secondary regions).
- Replication lag: **< 1 giây**.
- Dùng cho: Global applications, DR với RPO gần 0.
- **Managed failover**: Promote secondary region lên primary trong < 1 phút.

#### DynamoDB Backup

- **On-demand backup**: Tạo manual full backup tại bất kỳ thời điểm nào.
- **Point-in-time recovery (PITR)**: Restore đến bất kỳ second nào trong **35 ngày** qua.
- **DynamoDB Global Tables**: Multi-region, multi-active replication (active-active).

---

### 2.6 Storage Gateway

| Loại | Storage Protocol | Primary Storage | Dùng khi |
|---|---|---|---|
| **File Gateway** | NFS, SMB | S3 (objects) | File share on-prem với S3 backend |
| **Cached Volume Gateway** | iSCSI block | **S3** (+ local cache cho hot data) | Giảm thiểu local storage, cần low-latency cho hot data |
| **Stored Volume Gateway** | iSCSI block | **On-premises** (+ async backup S3) | Cần entire dataset on-prem, backup lên cloud |
| **Tape Gateway (VTL)** | iSCSI virtual tape library | S3 / Glacier | Thay thế tape backup infrastructure |

---

### 2.7 Amazon S3 — Replication & Versioning

#### S3 Replication

| | Cross-Region Replication (CRR) | Same-Region Replication (SRR) |
|---|---|---|
| **Mục đích** | DR, latency, compliance cross-region | Log aggregation, test/prod sync, compliance |
| **Yêu cầu** | Versioning phải bật trên cả source và destination | Versioning phải bật |
| **Delete behavior** | Không replicate deletes (tùy option) | Tương tự |

- **Replication không retroactive** (chỉ replicate objects mới sau khi bật).
- **Replication Time Control (RTC)**: Đảm bảo 99.99% objects replicated trong **15 phút**.

#### S3 Object Lock (WORM)

- **Compliance mode**: Không ai (kể cả root) có thể xóa/modify trong retention period.
- **Governance mode**: Chỉ user có IAM permission đặc biệt mới có thể override.
- **Dùng cho**: Regulatory compliance, data integrity.

---


### 2.8 Bổ Sung Theo Task 2.1–2.3

#### Task 2.1 — Scalability Và Elasticity

| Thành phần | Cách scale | Điểm cần nhớ cho SOA-C03 |
|---|---|---|
| **EC2 Auto Scaling** | Target tracking, step, scheduled, predictive | ASG chỉ span nhiều AZ trong **một Region**, không span nhiều Region |
| **ECS/EKS** | Service/task scaling, cluster/node scaling | Tách scaling ứng dụng và scaling capacity node |
| **Lambda** | Concurrency, reserved/provisioned concurrency | Reserved concurrency vừa giới hạn vừa đảm bảo capacity cho function |
| **CloudFront** | Cache static/dynamic content gần user | Tăng scalability bằng giảm request về origin |
| **ElastiCache** | Redis replicas/cluster mode, Memcached add nodes | Cache-aside cho read-heavy; tránh cache dữ liệu cần strong consistency |
| **RDS/Aurora** | Scale instance, storage autoscaling, read replicas, Aurora replicas | Multi-AZ là HA, không phải scale đọc; read replica mới dùng cho read scaling |
| **DynamoDB** | On-demand hoặc provisioned + auto scaling | Hot partition vẫn throttle dù tổng WCU/RCU còn dư |

#### Task 2.2 — HA Và Resilience

- **Multi-AZ RDS**: synchronous standby trong AZ khác, tự failover; endpoint giữ nguyên nhưng có downtime ngắn khi failover.
- **Read Replica**: asynchronous, dùng scale đọc hoặc DR thủ công; không thay thế Multi-AZ cho HA tự động.
- **ALB/NLB health checks** quyết định target có nhận traffic hay không; **Route 53 health checks** quyết định DNS trả record nào.
- Với private endpoint không public Internet, Route 53 nên health check qua **CloudWatch alarm** thay vì endpoint health check trực tiếp.
- Với architecture nhiều AZ: đặt subnet, NAT Gateway, load balancer target, và route table theo AZ để tránh single point of failure.

#### Task 2.3 — Backup/Restore Strategy

| Dịch vụ | Backup/restore cần nhớ |
|---|---|
| **EBS/EC2** | Snapshot incremental; AMI gồm root volume và mapping; DLM/AWS Backup tự động hóa lifecycle |
| **RDS/Aurora** | Automated backup cho PITR, manual snapshot giữ tới khi xóa; restore thường tạo DB/cluster mới |
| **DynamoDB** | PITR tối đa 35 ngày; restore tạo bảng mới |
| **S3** | Versioning + Object Lock + replication; lifecycle không phải backup nếu object bị overwrite/delete mà không có versioning |
| **EFS/FSx** | AWS Backup hỗ trợ backup tập trung; FSx có snapshot/backup theo loại file system |

Khi đề đưa **RTO/RPO/cost**, chọn chiến lược DR theo trade-off: Backup & Restore rẻ nhất nhưng chậm nhất; Pilot Light giữ lõi tối thiểu; Warm Standby chạy bản thu nhỏ; Multi-Site Active/Active nhanh nhất nhưng đắt và vận hành phức tạp nhất.

## 🟡 DOMAIN 3: Deployment, Provisioning & Automation (22%)

---

### 3.1 AWS CloudFormation — Nâng Cao

#### CloudFormation Template Structure

```yaml
AWSTemplateFormatVersion: "2010-09-09"
Description: "..."
Parameters:        # Input values (dynamic)
Mappings:          # Lookup tables (static)
Conditions:        # Conditional resource creation
Resources:         # REQUIRED — AWS resources
Outputs:           # Return values (Cross-stack references)
```

#### Key Attributes & Functions

| Attribute/Function | Mô tả |
|---|---|
| **DependsOn** | Buộc resource A chỉ tạo sau resource B |
| **DeletionPolicy** | Retain / Delete / Snapshot khi stack bị xóa |
| **UpdateReplacePolicy** | Hành động khi resource bị replace trong update |
| **Metadata** | Thông tin bổ sung (dùng với cfn-init) |
| **Fn::GetAtt** | Lấy attribute của resource |
| **Fn::ImportValue** | Import output từ stack khác (cross-stack reference) |
| **Fn::Sub** | String substitution |
| **Ref** | Reference parameter hoặc resource |

#### Helper Scripts

| Script | Chạy khi | Tác dụng |
|---|---|---|
| **cfn-init** | Instance launch (user data) | Đọc `AWS::CloudFormation::Init` metadata → cài packages, tạo files, start services |
| **cfn-signal** | Sau khi init hoàn thành | Báo hiệu SUCCESS/FAILURE cho WaitCondition hoặc CreationPolicy |
| **cfn-hup** | Daemon chạy liên tục | Detect metadata changes → Re-run cfn-init (rolling updates) |
| **cfn-get-metadata** | Theo yêu cầu | Lấy metadata từ stack |

> **Root cause phổ biến khi WaitCondition timeout**: cfn-signal **không được gọi** trong user data script.

#### CloudFormation Change Sets

- Preview changes BEFORE applying → Không bao giờ trực tiếp update production stack mà không xem Change Set.
- Hiển thị: Add/Modify/Remove resources, physical IDs, replacement flag (**Replacement: True** = resource sẽ bị recreate → downtime!).

#### CloudFormation Drift Detection

- Phát hiện sự khác biệt giữa **expected state** (template) và **actual state** (hiện tại).
- `DRIFTED` = Resource đã bị thay đổi ngoài CloudFormation.
- Dùng để audit và revert unauthorized changes.

#### Nested Stacks vs StackSets

| | Nested Stacks | StackSets |
|---|---|---|
| **Mục đích** | Tái sử dụng template components (modular design) | Deploy cùng stack sang **nhiều accounts/regions** |
| **Relationship** | Parent–Child stacks | Independent stacks |
| **Use case** | VPC layer + App layer tách biệt | Multi-account infrastructure baseline |

#### Cross-Stack References

- Stack A export output: `Outputs: VpcId: Export: Name: "MyVPC-ID"`
- Stack B import: `!ImportValue "MyVPC-ID"`
- Stack A **không thể xóa** nếu đang được import bởi stack khác.

#### CloudFormation Rollback

- Nếu stack creation/update thất bại → **Tự động rollback** về state trước đó.
- `--disable-rollback`: Giữ nguyên resources đã tạo (để debug).
- **Stack policy**: Ngăn chặn update không chủ ý lên specific resources (thêm lớp bảo vệ).

---

### 3.2 AWS CDK (Cloud Development Kit)

- Viết infrastructure bằng Python, TypeScript, Java, C#, Go.
- **Synthesize** thành CloudFormation template.
- **Constructs**: Building blocks (L1 = raw CloudFormation, L2 = higher-level with defaults, L3 = patterns).
- `cdk synth` → Generate CloudFormation template.
- `cdk deploy` → Deploy stack.
- `cdk diff` → Xem thay đổi (tương tự Change Set).

---

### 3.3 EC2 Image Builder

- Tự động hóa pipeline tạo AMIs và container images.
- **Components**: Build steps + Test steps.
- **Image Pipeline**: Schedule hoặc trigger thủ công.
- **Infrastructure Config**: VPC, subnet, instance type cho quá trình build.
- **Distribution Config**: AMI sharing across accounts/regions.

---

### 3.4 Tags — Chiến Lược Tagging

#### 4 Loại Tags

**Technical Tags:**
- `Name`, `Application ID`, `Application Role`, `Cluster`, `Environment`, `Version`

**Automation Tags:**
- `Date/Time`: Lên lịch start/stop/delete/rotate
- `Opt in/Opt out`: Tham gia/loại trừ khỏi automated activities (ví dụ: script stop instances)
- `Security`: Yêu cầu encryption, VPC Flow Logs

**Business Tags:**
- `Owner`, `Cost Center/Business Unit`, `Customer`, `Project`

**Security Tags:**
- `Confidentiality`, `Compliance`

#### Enforcement Tagging

- **CloudFormation Resource Tags**: Gắn tags khi tạo resources qua CFN.
- **AWS Service Catalog**: Auto-tags provisioned resources.
- **IAM policies với `aws:RequestTag`**: Buộc phải có tag khi tạo resource.
- **AWS Config + Systems Manager Automation**: Detect resources thiếu tags → Auto-remediate.

---

### 3.5 AWS Config — Nâng Cao

#### Config Rule Trigger Types

| Trigger | Mô tả |
|---|---|
| **Configuration changes** | Evaluate khi resource config thay đổi |
| **Periodic** | Evaluate theo lịch (ví dụ: mỗi 24 giờ) |
| **Hybrid** | Cả hai |

#### Config Remediation

- Khi resource non-compliant → **SSM Automation document** tự động remediate.
- Ví dụ: Security group mở port 22 → Config rule detect → SSM Automation xóa rule đó.
- **Auto remediation**: Tự động; **Manual remediation**: Phải kích hoạt thủ công.

#### Config Aggregator

- Thu thập compliance data từ **nhiều accounts/regions**.
- Cần **AWS Config bật trên tất cả source accounts**.
- Cần **authorization** từ source accounts (nếu không dùng Organizations).
- Với **Organizations**: Dùng Organizations integration để tự động authorize.

---

### 3.6 Systems Manager Automation — Runbooks

#### Pre-defined Runbooks

- `AWS-RestartEC2Instance`: Restart EC2.
- `AWS-StopEC2Instance` / `AWS-StartEC2Instance`: Stop/start instances.
- `AWS-UpdateSSMAgent`: Cập nhật SSM Agent.
- `AWS-PatchInstanceWithRollback`: Patch với khả năng rollback.
- `AWS-CreateSnapshot`: Tạo EBS snapshot.

#### Custom Runbooks

- Viết bằng YAML/JSON.
- Các step types: `aws:runCommand`, `aws:invokeLambdaFunction`, `aws:executeScript`, `aws:approve`.
- **`aws:approve`**: Tích hợp human approval trong automation workflow.

---

### 3.7 Amazon EventBridge Scheduler

- Scheduled triggers cho Lambda, Step Functions, SQS, ECS tasks.
- Hỗ trợ **cron expressions** và **rate expressions**.
- Khác với EventBridge Rules (Rules react to events; Scheduler là time-based).

---

### 3.8 AWS Lambda — Operational Aspects

#### Lambda Concurrency

| Loại | Mô tả |
|---|---|
| **Reserved Concurrency** | Đặt giới hạn tối đa cho một function (cũng đảm bảo capacity) |
| **Provisioned Concurrency** | Pre-warm execution environments → Loại bỏ cold starts |

#### Lambda Deployment

- **Aliases**: Pointer đến function version (Production, Staging).
- **Versions**: Immutable snapshots của code + config.
- **Weighted aliases**: Route % traffic sang version mới (canary deployment).
- **Lambda Layers**: Share code/dependencies giữa functions.

#### Lambda Error Handling

- **Dead Letter Queue (DLQ)**: SQS hoặc SNS nhận unprocessed events khi Lambda thất bại (async invocations).
- **Lambda Destinations**: Gửi events thành công hoặc thất bại đến SQS/SNS/EventBridge/Lambda khác.

---

### 3.9 AWS CodeDeploy Deployment Strategies

| Strategy | Mô tả | Downtime |
|---|---|---|
| **In-place** | Deploy lên instances hiện tại (All-at-once, Half-at-a-time, One-at-a-time) | Có thể có |
| **Blue/Green** | Deploy lên environment mới → Switch traffic | Không |
| **Canary** | Route nhỏ % traffic sang version mới trước | Không |
| **Linear** | Tăng dần traffic đều đặn theo thời gian | Không |

---

### 3.10 AWS Resource Access Manager (RAM)

- **Share AWS resources** với accounts khác trong tổ chức hoặc bên ngoài.
- Resources có thể share: VPC Subnets, Transit Gateway, Route 53 Resolver rules, License Manager configs, v.v.
- **Không** copy resources — cho phép dùng chung.
- Kết hợp với **CloudFormation StackSets** để deploy resources dùng shared VPC subnets.

---


### 3.11 Bổ Sung Theo Task 3.1–3.2

#### Deployment/Provisioning Issues Cần Biết Cách Gỡ

| Triệu chứng | Nguyên nhân hay gặp | Hướng xử lý |
|---|---|---|
| CloudFormation rollback do subnet hết IP | CIDR quá nhỏ, subnet private/public thiếu địa chỉ | Tăng subnet CIDR/tạo subnet mới, dùng IPAM để quản lý không overlap |
| `AccessDenied` khi deploy stack | Execution role thiếu quyền hoặc thiếu `iam:PassRole` | Kiểm tra CloudTrail event, policy simulator, role trust/policy |
| WaitCondition/CreationPolicy timeout | EC2 user data lỗi hoặc thiếu `cfn-signal` | Xem `/var/log/cloud-init-output.log`, SSM Session Manager, thêm signal đúng |
| StackSet không deploy sang account/Region | Thiếu trusted access/permission model hoặc target OU sai | Kiểm tra Organizations integration, admin/execution role |
| CDK deploy lỗi bootstrap | Region/account chưa bootstrap hoặc bootstrap role thiếu quyền | Chạy/bootstrap đúng environment, kiểm tra qualifier và trust |

#### Terraform Và Git Trong Phạm Vi SOA-C03

- **Terraform state** là nguồn sự thật của hạ tầng đã provision; state nên lưu remote backend có locking (ví dụ S3 + DynamoDB lock trong môi trường AWS).
- Không sửa resource thủ công rồi bỏ qua state: dùng `terraform plan` để phát hiện drift, import nếu cần quản lý resource đã tồn tại.
- Với Git, cần nắm operational flow: branch/PR, review plan trước khi apply, rollback bằng revert commit hoặc deploy version trước đó.
- Không commit secrets vào Git; dùng Secrets Manager/SSM Parameter Store và biến môi trường an toàn trong pipeline.
- Khi tool bên thứ ba báo drift/deploy fail, CloudTrail vẫn là nơi audit API call cuối cùng trên AWS.

#### Event-Driven Automation

| Event source | Automation target phổ biến | Ví dụ |
|---|---|---|
| **S3 Event Notifications** | Lambda, SQS, SNS, EventBridge | Object upload -> resize/scan/process |
| **EventBridge service events** | Lambda, SSM Automation, Step Functions | EC2 state change -> runbook remediate |
| **CloudWatch Alarm state change** | SNS/EventBridge/Lambda/SSM | Alarm ALARM -> tạo OpsItem hoặc restart service |
| **AWS Config noncompliance** | SSM Automation | SG mở port nguy hiểm -> remove rule |

## 🔴 DOMAIN 4: Security and Compliance (16%)

---

### 4.1 IAM — Nâng Cao

#### IAM Policy Evaluation Logic

```
Explicit DENY (anywhere) → DENY
No explicit ALLOW → DENY (implicit deny)
Explicit ALLOW → ALLOW
```

**Thứ tự đánh giá:**
1. SCPs (Organizations)
2. Resource-based policies
3. Identity-based policies
4. IAM Permission Boundaries
5. Session policies

#### Permission Boundaries

- Giới hạn **maximum permissions** một IAM entity có thể có.
- Dù identity-based policy grant nhiều quyền → Chỉ những quyền trong permission boundary mới có hiệu lực.
- **Dùng khi**: Delegate quyền tạo roles/users cho developers, nhưng giới hạn quyền họ có thể grant.

#### Cross-Account Access

- **Role assumption** (`sts:AssumeRole`): Account A assume role trong Account B.
- Trust policy trong Account B → Cho phép Account A.
- Identity-based policy trong Account B role → Define permissions.

#### IAM Access Analyzer

- Phân tích **resource-based policies** để tìm resources accessible từ **outside the zone of trust** (bên ngoài account/organization).
- Zone of trust: AWS account hoặc AWS Organization.
- Findings: S3 bucket public, IAM role có thể assume từ internet, KMS key accessible từ ngoài.

---

### 4.2 AWS Organizations & SCP

#### SCP (Service Control Policy)

- Kiểm soát **maximum permissions** cho tất cả users/roles trong member accounts.
- **Không** grant permissions — Chỉ restrict.
- Không ảnh hưởng **management account** (chỉ member accounts).
- **Không** ảnh hưởng đến **service-linked roles**.
- `FullAWSAccess`: SCP mặc định (không restrict gì cả).
- **SCP Inheritance**: Account nhận SCPs từ tất cả OUs trên đường từ root xuống.

#### SCP Use Cases

- Prevent leaving organization: `Deny` `organizations:LeaveOrganization`
- Restrict to specific regions: `Deny` với `Condition: StringNotEquals aws:RequestedRegion`
- Require MFA: `Deny` nếu `aws:MultiFactorAuthPresent = false`
- Prevent disabling CloudTrail: `Deny` `cloudtrail:DeleteTrail`, `cloudtrail:StopLogging`

---

### 4.3 AWS KMS

#### Key Types

| Loại | Quản lý bởi | Rotation | Dùng khi |
|---|---|---|---|
| **AWS managed key** | AWS | Mỗi 1 năm (auto) | Mặc định khi bật encryption trong service |
| **Customer managed key (CMK)** | Customer | Manual/Auto (1 năm) | Cần control, auditing, rotation riêng |
| **Custom key store (CloudHSM)** | Customer (HSM) | Manual | Compliance yêu cầu HSM (FIPS 140-2 Level 3) |

#### KMS Operations

- **Envelope Encryption**: Dùng CMK để encrypt **Data Encryption Key (DEK)** → Dùng DEK để encrypt data lớn.
  - Giúp encrypt data > 4 KB (giới hạn KMS direct encrypt).
- **Key Rotation**: CMK tự động rotate mỗi năm (Customer managed key — tùy chọn bật).
- **Key Policy**: Kiểm soát ai có thể dùng/manage CMK.
- **Grant**: Delegate quyền dùng CMK cho AWS services (ví dụ: EBS, RDS).

---

### 4.4 AWS Certificate Manager (ACM)

- Provision, manage, deploy **SSL/TLS certificates**.
- **Public certificates**: Miễn phí, auto-renewal, dùng với ELB, CloudFront, API GW.
- **Private certificates**: Dùng cho internal services (Private CA — có phí).
- **Không thể export** private key của ACM public certificates.
- ACM certificates phải ở **cùng region** với service (ngoại trừ CloudFront → dùng **us-east-1**).

---

### 4.5 AWS Secrets Manager

- Lưu và **tự động rotate** secrets (database passwords, API keys).
- **Native rotation** hỗ trợ: RDS, Redshift, DocumentDB, others via Lambda.
- Rotation dùng **Lambda function**.
- Hỗ trợ **cross-account access** qua resource-based policy.
- **Phân biệt với SSM Parameter Store**: Secrets Manager có auto-rotation + higher cost.

---

### 4.6 Amazon GuardDuty

- **Threat detection** service phân tích:
  - **VPC Flow Logs**
  - **CloudTrail events**
  - **DNS logs**
  - **EKS audit logs** (nếu bật)
  - **S3 data events** (nếu bật)
  - **Lambda network activity** (nếu bật)
- **Findings categories**: Reconnaissance, Backdoor, Crypto-mining, Trojan, UnauthorizedAccess.
- **Dùng machine learning** để detect anomalies.
- **Multi-account**: Designated admin account quản lý findings từ tất cả member accounts.

---

### 4.7 Amazon Inspector v2

- **Automated vulnerability assessment**.
- Scan:
  - **EC2 instances**: OS vulnerabilities, network reachability.
  - **ECR container images**: Vulnerabilities trước khi deploy.
  - **Lambda functions**: Code và package vulnerabilities.
- Tích hợp với **Security Hub** để aggregate findings.
- **Không** scan toàn bộ AWS resources (chỉ EC2, ECR, Lambda).

---

### 4.8 AWS Security Hub

- **Aggregates security findings** từ nhiều services: GuardDuty, Inspector, Macie, Config, IAM Access Analyzer, Firewall Manager.
- **Security Standards**: CIS AWS Foundations, AWS Foundational Security Best Practices, PCI DSS.
- **Multi-account**: Aggregate findings từ nhiều accounts trong Organizations.
- **Findings**: Normalized format (ASFF - Amazon Security Finding Format).
- **Automated remediation**: Kết hợp với EventBridge + Lambda/SSM Automation.

---

### 4.9 Amazon Macie

- **Data discovery và classification** cho S3.
- Tự động phát hiện **PII (Personally Identifiable Information)**, **PHI**, **credentials**, **financial data**.
- **S3 inventory**: Scan tất cả S3 buckets để phân loại data sensitivity.
- Alert khi bucket public, unencrypted, accessible externally.

---

### 4.10 WAF, Shield, Network Firewall

#### AWS WAF

- **Web Application Firewall** cho ALB, CloudFront, API Gateway, AppSync.
- **Web ACL**: Tập hợp rules.
- **Rules**: Allow, Block, Count, CAPTCHA, Challenge.
- **Rule Groups**: Custom hoặc Managed (AWS Managed Rules, AWS Marketplace).
- **Managed rules**: Bot control, Known bad inputs, Core rule set (OWASP Top 10), SQL injection, XSS.
- **Rate-based rules**: Block IPs exceed X requests/5 minutes.
- **Logging**: Gửi full web ACL logs đến CloudWatch Logs, S3, Kinesis Data Firehose.

#### AWS Shield

| | Standard | Advanced |
|---|---|---|
| **Chi phí** | Miễn phí | $3,000/tháng (tối thiểu 1 năm) |
| **Bảo vệ** | Layer 3/4 DDoS cơ bản | Layer 3/4/7 DDoS nâng cao + 24/7 DRT (DDoS Response Team) |
| **Bao gồm** | Tất cả AWS customers | ALB, CLB, EIP, EC2, CloudFront, Global Accelerator, Route 53 |
| **WAF miễn phí** | ❌ | ✅ (khi dùng với CloudFront/ALB) |
| **Cost protection** | ❌ | ✅ (reimburse scaling charges do DDoS) |

#### AWS Network Firewall

- **Stateful và stateless firewall** cho VPC.
- **Stateful**: Deep packet inspection, protocol detection, domain filtering.
- **Stateless**: Fast, rule-based L3/L4 filtering.
- Deploy vào **dedicated subnet** trong VPC.
- **Rule groups**: Suricata-compatible IDS/IPS rules.
- Dùng kết hợp với **Transit Gateway** cho centralized inspection.

#### Route 53 Resolver DNS Firewall

- Filter DNS queries từ VPC.
- **Block** domains theo domain lists (managed hoặc custom).
- Ngăn **data exfiltration** qua DNS tunneling.

---

### 4.11 S3 Security

#### S3 Block Public Access

- **4 settings**: BlockPublicAcls, IgnorePublicAcls, BlockPublicPolicy, RestrictPublicBuckets.
- Có thể bật ở cấp **account** hoặc **bucket**.
- Best practice: Bật tất cả 4 settings ở account level.

#### S3 Object Lock (WORM)

- **Retention Mode — Compliance**: Không ai xóa/modify được (kể cả root).
- **Retention Mode — Governance**: Chỉ user có `s3:BypassGovernanceRetention` mới override.
- **Legal Hold**: Tạm thời bảo vệ, không cần retention period.

#### S3 Access Control Hierarchy

1. **S3 Block Public Access** (account level) → Override tất cả
2. **Bucket Policy** (resource-based)
3. **Bucket ACL / Object ACL**
4. **User/Role IAM Policy** (identity-based)

#### S3 Encryption

| | SSE-S3 | SSE-KMS | SSE-C | CSE |
|---|---|---|---|---|
| Key quản lý | AWS | AWS KMS (CMK) | Customer | Customer |
| Audit trail | ❌ | ✅ CloudTrail | ❌ | Customer |
| **Default** | ✅ (AES-256) | Optional | Optional | Optional |

---

### 4.12 IAM Identity Center (SSO)

- **Centralized SSO** cho tất cả AWS accounts trong Organizations + external applications.
- Hỗ trợ **SAML 2.0** IdP (Active Directory, Okta, Azure AD...).
- **Permission Sets**: Template IAM policies, assign cho users/groups → accounts.
- **Attribute-Based Access Control (ABAC)**: Grant permissions dựa trên user attributes.
- **SCIM**: Automatic user provisioning từ IdP.

---


### 4.13 Bổ Sung Theo Task 4.1–4.2

#### IAM Features Theo Blueprint

| Chủ đề | Điểm cần nắm |
|---|---|
| **Password policy** | Áp dụng cho IAM users: độ dài, complexity, expiration, reuse prevention |
| **MFA** | Bắt buộc cho root và privileged IAM users; có thể enforce bằng IAM/SCP condition |
| **Roles** | Dùng cho AWS services, cross-account, federation; ưu tiên temporary credentials thay vì access key dài hạn |
| **Federated identity** | IAM Identity Center/SAML/OIDC cho workforce; web identity/OIDC cho workload như EKS IRSA |
| **Resource policies** | S3 bucket policy, KMS key policy, SNS/SQS policy, Lambda permission; kiểm soát cross-account/public access |
| **Policy conditions** | `aws:RequestedRegion`, `aws:PrincipalOrgID`, `aws:MultiFactorAuthPresent`, `aws:SourceVpce`, tag conditions |

#### Audit Và Troubleshoot Access

1. Xác định principal, action, resource, region, request context.
2. Kiểm tra explicit deny từ SCP, permission boundary, session policy, identity policy, resource policy, VPC endpoint policy, KMS key policy.
3. Dùng **CloudTrail** để xem API call và error code; dùng **IAM Policy Simulator** cho identity policy; dùng **IAM Access Analyzer** cho resource public/cross-account.
4. Với KMS, nhớ cần cả IAM permission **và** key policy/grant phù hợp.

#### Data Classification Và Protection

| Data class | Control nên áp dụng |
|---|---|
| **Public** | Cho phép public có chủ đích, vẫn log access và dùng CloudFront/WAF nếu web-facing |
| **Internal** | Private subnet/VPC endpoint, IAM least privilege, encryption mặc định |
| **Confidential** | KMS customer managed key, bucket/key policy chặt, Macie classification, audit CloudTrail |
| **Restricted/regulated** | Object Lock/Vault Lock nếu cần WORM, SCP guardrails, Security Hub/Config standards, cross-account backup |

#### Encryption At Rest / In Transit

- **At rest**: S3 SSE-S3/SSE-KMS, EBS/RDS/EFS/FSx encryption bằng KMS; đổi KMS key sau khi tạo thường cần snapshot/restore hoặc copy tùy dịch vụ.
- **In transit**: ACM certificate cho ALB/CloudFront/API Gateway; CloudFront certificate phải ở `us-east-1`; RDS TLS cần client trust đúng CA bundle.
- Troubleshooting TLS: kiểm tra certificate chain, hostname/SAN, expiration, region của ACM, security policy/TLS version, listener rule và target health.
- Secrets nên nằm trong **Secrets Manager** nếu cần rotation tự động; **Parameter Store SecureString** phù hợp config/secret đơn giản hơn.

#### Enforce Compliance Requirements

- Chặn Region ngoài phạm vi bằng **SCP** với `aws:RequestedRegion`, nhớ ngoại lệ cho global services cần thiết.
- Chặn service ngoài phạm vi bằng SCP deny theo action/service prefix.
- Dùng **AWS Config** rules/conformance packs để phát hiện resource không compliant; dùng SSM Automation/EventBridge để remediate.
- Dùng **Trusted Advisor/Security Hub/GuardDuty/Inspector/Macie** để gom finding rồi route qua EventBridge/SNS/User Notifications.

## 🟣 DOMAIN 5: Networking and Content Delivery (18%)

---

### 5.1 Amazon VPC — Fundamentals

#### VPC CIDR Planning

- VPC CIDR: `/16` (tối đa) đến `/28` (tối thiểu).
- AWS **reserve 5 IPs** đầu tiên trong mỗi subnet:
  - x.x.x.0: Network address
  - x.x.x.1: VPC router
  - x.x.x.2: DNS server
  - x.x.x.3: Future use
  - x.x.x.255: Broadcast

#### VPC Components

| Component | Mô tả |
|---|---|
| **Internet Gateway (IGW)** | Inbound/outbound IPv4 và IPv6 internet access |
| **Egress-Only IGW** | **Outbound IPv6 only** — Chặn inbound từ internet |
| **NAT Gateway** | Outbound IPv4 cho private subnet — **Không hỗ trợ IPv6** |
| **Virtual Private Gateway (VGW)** | VPN endpoint phía AWS |
| **Transit Gateway (TGW)** | Hub kết nối nhiều VPCs + on-prem (hub-and-spoke) |
| **VPC Peering** | 1-1 kết nối giữa 2 VPCs (không transitive) |
| **Route Table** | Định tuyến traffic trong VPC |

#### Kích hoạt IPv6 — Các bước

1. Associate **IPv6 CIDR block** với VPC và Subnets.
2. Update **Route Tables** (`Destination: ::/0, Target: IGW` cho public; Egress-Only IGW cho private).
3. Update **Security Group Rules** (thêm IPv6 rules).
4. **Assign IPv6 addresses** cho EC2 instances.

> NAT Gateway **không** hỗ trợ IPv6 → Dùng **Egress-Only IGW** cho private subnet IPv6 outbound.

---

### 5.2 NAT Gateway vs NAT Instance

| Thuộc tính | NAT Gateway | NAT Instance |
|---|---|---|
| **Quản lý** | AWS managed (fully) | User managed |
| **Availability** | Highly available per AZ (redundant) | Manual failover script |
| **Bandwidth** | Up to **45 Gbps** | Phụ thuộc instance type |
| **Security Groups** | ❌ Không gắn được | ✅ Gắn được |
| **Port Forwarding** | ❌ | ✅ |
| **Bastion Host** | ❌ | ✅ |
| **IPv6** | ❌ | ❌ |
| **Timeout behavior** | Gửi **RST** packet | Gửi **FIN** packet |
| **IP Fragmentation TCP/ICMP** | ❌ Drops | ✅ Reassemble |
| **Public IP** | Elastic IP chọn lúc tạo | EIP hoặc public IP (thay đổi được) |
| **Private IP** | Auto từ subnet range | Chỉ định specific IP khi launch |

---

### 5.3 Network ACL vs Security Group

| | Network ACL | Security Group |
|---|---|---|
| **Level** | Subnet | Instance (ENI) |
| **Stateful** | ❌ Stateless | ✅ Stateful |
| **Rules** | Numbered (lowest = highest priority) | Tất cả rules đều evaluate |
| **Default (AWS default NACL)** | Allow all in/out | — |
| **Custom NACL** | **Deny all** in/out cho đến khi thêm rules | — |
| **Default SG** | — | Deny all inbound; Allow all outbound |
| **Inbound allow** | Phải explicit | Phải explicit |
| **Outbound allow** | **Phải explicit** (stateless!) | **Tự động** (stateful) |

#### Ephemeral Ports trong Custom NACL

| Client | Port Range |
|---|---|
| **Amazon Linux, general Linux kernels** | 32768–61000 |
| **Requests from ELB** | 1024–65535 |
| **Windows Server 2003 and earlier** | 1025–5000 |
| **Windows Server 2008 and later / most clients** | 49152–65535 |
| **Recommended range** | **1024–65535** (cover tất cả) |

> **Rule 100**: Custom NACL chặn tất cả traffic nếu rule 100 là DENY ALL (rules evaluate theo số thứ tự từ thấp đến cao, rule thấp nhất match → áp dụng ngay).

---

### 5.4 VPC Endpoints

#### Interface Endpoints vs Gateway Endpoints

| | Interface Endpoint (AWS PrivateLink) | Gateway Endpoint |
|---|---|---|
| **Cơ chế** | ENI trong subnet (private IP) | Route table entry |
| **Phí** | ✅ Có phí (per hour + per GB) | ❌ **Miễn phí** |
| **Hỗ trợ services** | Hầu hết AWS services + 3rd party | **S3** và **DynamoDB** chỉ |
| **Kết nối từ on-prem** | ✅ Qua Direct Connect / VPN | ❌ |
| **Policy** | Endpoint Policy | Endpoint Policy |
| **Security Group** | ✅ Gắn được | ❌ |

> **Ghi nhớ**: S3 và DynamoDB → Gateway Endpoint (rẻ hơn, không cần ENI). Mọi service khác → Interface Endpoint.

---

### 5.5 AWS Transit Gateway

- **Hub-and-spoke** routing: Kết nối nhiều VPCs, VPNs, Direct Connect qua một central hub.
- Không cần full mesh VPC peering.
- **Transit Gateway Route Tables**: Kiểm soát traffic giữa attachments.
- **Multi-region**: Peering giữa các Transit Gateways khác region.
- **RAM**: Share Transit Gateway với accounts khác.
- **Transit Gateway với Network Firewall**: Centralized inspection của tất cả traffic.

---

### 5.6 VPC Peering

- Kết nối **1-1** giữa 2 VPCs (cùng/khác account/region).
- **Không transitive**: A-B-C peered → A **không** communicate với C qua B.
- **Không overlapping CIDR** giữa 2 VPCs được peer.
- Cross-region peering hỗ trợ nhưng tính phí **inter-region data transfer**.

---

### 5.7 AWS Direct Connect

#### Virtual Interfaces (VIFs)

| VIF | Kết nối đến | Dùng khi |
|---|---|---|
| **Private VIF** | VPC (qua VGW) | Access private resources trong VPC |
| **Public VIF** | AWS public endpoints | Access S3, DynamoDB, v.v. qua DX |
| **Transit VIF** | Transit Gateway | Connect nhiều VPCs qua TGW |

#### Dedicated vs Hosted Connection

| | Dedicated | Hosted |
|---|---|---|
| **Bandwidth** | 1 Gbps, 10 Gbps, 100 Gbps | 50 Mbps đến 10 Gbps |
| **Setup time** | Weeks (phải request port) | Faster (qua APN partner) |
| **VIF** | Multiple VIFs | Typically 1 VIF |

---

### 5.8 Amazon CloudFront — Nâng Cao

#### CloudFront Distribution Components

- **Origins**: S3, ALB, EC2, HTTP server.
- **Behaviors**: URL path patterns → Map đến specific origins.
- **Cache Policies**: TTL, header/query string forwarding.
- **Origin Request Policies**: Headers/cookies/query strings forward đến origin.
- **Response Headers Policies**: Thêm security headers (CORS, HSTS, CSP).

#### Origin Access Control (OAC) vs Origin Access Identity (OAI)

| | OAI (cũ) | OAC (mới, khuyến nghị) |
|---|---|---|
| **Hỗ trợ S3 SSE-KMS** | ❌ | ✅ |
| **Hỗ trợ S3 in all regions** | Hạn chế | ✅ |
| **Signing methods** | Fixed | Flexible (sigv4) |
| **Khuyến nghị** | ❌ Deprecated | ✅ |

> **OAC/OAI** = Đảm bảo S3 bucket **chỉ** accessible qua CloudFront (không trực tiếp).

#### CloudFront Signed URLs vs Signed Cookies

| | Signed URL | Signed Cookie |
|---|---|---|
| **Dùng khi** | Cấp quyền cho **1 file cụ thể** | Cấp quyền cho **nhiều files** |
| **Thông tin** | Chứa thông tin trong URL | Trong cookie header |
| **RTMP** | ✅ | ❌ |
| **Use case** | Video streaming individual file | Toàn bộ premium content area |

#### CloudFront Functions vs Lambda@Edge

| | CloudFront Functions | Lambda@Edge |
|---|---|---|
| **Execution location** | CloudFront edge (150+ PoPs) | 13 regional edge caches |
| **Max execution time** | < 1ms | 5s (viewer) / 30s (origin) |
| **Languages** | JavaScript only | Node.js, Python |
| **Trigger points** | Viewer request/response only | Viewer + Origin request/response |
| **Memory** | 2 MB | 128 MB – 10 GB |
| **Cost** | Rẻ hơn | Đắt hơn |
| **Dùng cho** | URL rewrites/redirects, header manipulation, simple auth | Complex logic, A/B testing, auth |

#### CloudFront Geo Restriction

- **Allowlist**: Chỉ cho phép specific countries.
- **Blocklist**: Chặn specific countries.
- Dựa trên IP geolocation.

#### CloudFront Cache Invalidation

- **Invalidation**: Xóa cached objects tại edge locations (tính phí sau 1,000 paths/month).
- **Versioning** (recommended): Đặt version trong filename/URL → Cache tự expire không cần invalidate.

#### CloudFront HTTPS

- **Redirect HTTP to HTTPS**.
- **HTTPS Only**.
- **Custom SSL Certificate**: Upload lên ACM ở **us-east-1** (chỉ region này cho CloudFront).

#### CloudFront Device Detection

- Forward **User-Agent header** → CloudFront set:
  - `CloudFront-Is-Desktop-Viewer`
  - `CloudFront-Is-Mobile-Viewer`
  - `CloudFront-Is-SmartTV-Viewer`
  - `CloudFront-Is-Tablet-Viewer`
- Cấu hình bằng **cache policy/origin request policy** để forward CloudFront viewer headers; nếu không forward thì origin không nhận các headers này.

---

### 5.9 Amazon Route 53 — Chi Tiết

#### Route 53 Resolver Endpoints

| Endpoint | Hướng flow | Mô tả |
|---|---|---|
| **Inbound** | On-prem → AWS | On-prem DNS forward queries vào AWS → Resolve VPC DNS, private hosted zones |
| **Outbound** | AWS → On-prem | VPC DNS forward queries ra on-prem resolver (dùng Forwarding Rules) |

> **Kịch bản thực tế**: On-prem không resolve được hostname EC2 trong AWS:
> → Tạo **Inbound Endpoint** → Cập nhật on-prem DNS để forward `*.aws.internal` đến Inbound Endpoint IP.

#### Route 53 Private Hosted Zone

- **Không public** ra internet.
- Chỉ accessible từ VPC được associate.
- Có thể associate multiple VPCs (cùng/khác account).
- Dùng cho: Internal service discovery, database hostname abstraction.
- **A/AAAA record** cho database → Ẩn IP thực, dễ rotate.

#### Route 53 Health Checks Types

| Type | Mô tả |
|---|---|
| **HTTP / HTTPS / TCP** | Monitor endpoint trực tiếp |
| **Calculated** | Kết hợp nhiều health checks (AND/OR) |
| **CloudWatch Alarm** | Monitor private resources (không reachable từ internet) |
| **String matching** | Response body chứa specific string |

---

### 5.10 VPC Flow Logs — Phân tích

#### Format

```
<version> <account-id> <interface-id> <srcaddr> <dstaddr> <srcport> <dstport> 
<protocol> <packets> <bytes> <start> <end> <action> <log-status>
```

#### Protocol Numbers

| Number | Protocol |
|---|---|
| 1 | ICMP (ping) |
| 6 | TCP |
| 17 | UDP |

#### Troubleshooting với Flow Logs

| Scenario | Flow Log Pattern | Root Cause |
|---|---|---|
| Ping fail, no response | ACCEPT inbound; REJECT outbound | **NACL blocks outbound ICMP** (stateless) |
| HTTP request fail | REJECT inbound | SG hoặc NACL blocks inbound port 80 |
| Response not reaching client | ACCEPT inbound; REJECT outbound | **NACL blocks outbound ephemeral ports** |
| No flow logs at all | — | Flow logs not enabled hoặc IAM permissions |

---

### 5.11 VPC Reachability Analyzer

- Kiểm tra **connectivity** giữa 2 endpoints trong VPC mà không cần gửi actual traffic.
- Phân tích: Route tables, NACLs, Security Groups, Peering, Transit Gateway, VPN.
- Kết quả: **Reachable** hoặc **Not reachable** + Explanation.
- Dùng để **troubleshoot** routing/security issues nhanh.

---

### 5.12 AWS Global Accelerator vs CloudFront

| | CloudFront | Global Accelerator |
|---|---|---|
| **Content caching** | ✅ (CDN) | ❌ |
| **Protocol** | HTTP/HTTPS | **TCP, UDP** |
| **Static IP** | ❌ | ✅ (2 Anycast IPs) |
| **Latency optimization** | Edge cache | AWS backbone network routing |
| **Dùng cho** | Static/dynamic web content | Non-HTTP (gaming, IoT, VoIP), global failover |
| **Health checks** | ❌ built-in routing | ✅ Tự động failover |

---


### 5.13 Bổ Sung Theo Task 5.1–5.3

#### VPC Connectivity Checklist

| Lớp kiểm tra | Câu hỏi cần trả lời |
|---|---|
| **Subnet/route table** | Subnet có route đúng tới IGW/NAT/TGW/VGW/endpoint không? |
| **Security group** | Stateful allow đúng inbound/outbound theo port/protocol không? |
| **Network ACL** | Stateless nên có cả inbound và outbound, bao gồm ephemeral ports chưa? |
| **DNS** | `enableDnsSupport`/`enableDnsHostnames`, private hosted zone, Resolver rule/endpoint đúng chưa? |
| **Endpoint/private path** | Gateway endpoint cho S3/DynamoDB, interface endpoint cho service khác, endpoint policy có deny không? |
| **Logs** | VPC Flow Logs, ELB access logs, WAF logs, CloudFront logs có đủ để xác định accept/reject/latency không? |

#### Private Connectivity Trong Phạm Vi Ôn

- **VPC Peering**: 1-1, không transitive, không overlap CIDR.
- **Transit Gateway**: hub-and-spoke nhiều VPC/VPN, route table kiểm soát segmentation.
- **Site-to-Site VPN**: nhanh triển khai, encrypted qua Internet, dùng BGP nếu dynamic routing.
- **Client VPN**: user remote access vào VPC.
- **PrivateLink/interface endpoint**: expose service qua private IP, tránh public Internet.
- **Gateway endpoint**: S3/DynamoDB, miễn phí, route table based.

#### Route 53, Resolver, Query Logging

- **Route 53 Resolver query logging** ghi DNS queries từ VPC ra CloudWatch Logs/S3/Data Firehose để điều tra DNS và security.
- **Resolver inbound endpoint** cho on-prem resolve private hosted zone/VPC names; **outbound endpoint** cho VPC forward query về on-prem DNS.
- **Resolver DNS Firewall** block/allow domain list ở cấp VPC, hữu ích để chặn malware domain hoặc DNS exfiltration.
- Routing policy chọn theo mục tiêu: failover cho active/passive, latency cho low-latency Region, weighted cho canary/A-B, geolocation/geoproximity cho điều khiển theo vị trí.

#### CloudFront Caching Issues

| Triệu chứng | Nguyên nhân hay gặp | Cách xử lý |
|---|---|---|
| User vẫn thấy nội dung cũ | TTL cao hoặc chưa invalidation | Dùng versioned file name hoặc invalidation path |
| Cache hit ratio thấp | Forward quá nhiều headers/cookies/query strings | Tối giản cache policy, tách behavior theo path |
| Origin quá tải | TTL thấp, object không cacheable, lỗi 4xx/5xx không được xử lý | Tối ưu cache/error TTL, thêm Origin Shield nếu phù hợp |
| Private S3 origin bị access denied | OAC/bucket policy/KMS key policy chưa đúng | Cho CloudFront service principal dùng OAC và quyền KMS nếu SSE-KMS |

#### CloudWatch Network Monitoring

- Dùng CloudWatch metrics của **NAT Gateway**, **Transit Gateway**, **VPC endpoints**, **ELB**, **CloudFront**, **VPN tunnels** để phát hiện packet drop, bytes/packets bất thường, tunnel down, target unhealthy.
- Kết hợp **VPC Flow Logs + CloudWatch Logs Insights/Athena** để truy vết traffic bị reject hoặc không tới đích.
- Với hybrid/private connectivity, luôn kiểm tra cả hai phía: AWS route table/TGW route table và route/firewall/on-prem DNS phía khách hàng.

#### Network Cost Optimization

- Đặt NAT Gateway theo AZ và route private subnet cùng AZ để giảm cross-AZ data transfer.
- Dùng Gateway Endpoint cho S3/DynamoDB để tránh NAT data processing charge.
- Dùng CloudFront cache để giảm data transfer từ origin và giảm request về ALB/EC2/S3.
- Tránh full-mesh VPC peering khi số VPC tăng; dùng TGW khi cần quản trị routing tập trung, nhưng vẫn tính phí attachment/data processing.

## 📊 PHẦN SO SÁNH TỔNG HỢP

### CloudWatch vs CloudTrail vs Config vs Trusted Advisor

| | CloudWatch | CloudTrail | AWS Config | Trusted Advisor |
|---|---|---|---|---|
| **Thu thập** | Metrics, Logs, Events | API calls | Resource config changes | Checks & recommendations |
| **Hỏi** | "Hệ thống đang hoạt động thế nào?" | "Ai làm gì, khi nào?" | "Config thay đổi thế nào?" | "Có đang follow best practices?" |
| **Thời gian** | Real-time | Near real-time | Continuous/periodic | Periodic |
| **Dùng để** | Monitor, alert, performance | Audit, compliance, forensics | Compliance, drift detection | Optimization, security gaps |

### ELB Types — Decision Tree

```
WebSockets + host/path routing + containers? → ALB (Layer 7)
Static IP + UDP/TCP extreme performance?    → NLB (Layer 4)
3rd-party security appliances?              → GLB (Layer 3/4)
```

### Storage Gateway — Decision Tree

```
Cần toàn bộ data local + backup S3?    → Stored Volume
S3 là primary + cache local hot data?  → Cached Volume
File share (NFS/SMB) → S3 objects?     → File Gateway
Thay thế tape backup?                  → Tape Gateway (VTL)
```

### RDS Backup Recovery — Decision Tree

```
Cần rollback nhanh, cùng cluster?      → Aurora Backtracking
Cần restore đến điểm cụ thể (DB mới)? → Point-in-Time Restore
Cần restore từ snapshot cũ (DB mới)?  → Restore from Snapshot
Cần automated backup?                  → AWS Backup
```

### Security Services — When to Use

| Scenario | Service |
|---|---|
| SQL injection, XSS, web attacks | **WAF** |
| DDoS protection | **Shield** (Standard/Advanced) |
| Threat detection (malware, crypto-mining) | **GuardDuty** |
| OS vulnerability scan, container scan | **Inspector v2** |
| S3 sensitive data discovery (PII) | **Macie** |
| Centralized security findings | **Security Hub** |
| Security best practices check | **Trusted Advisor** |
| Firewall traffic filtering VPC | **Network Firewall** |
| Block malicious DNS queries | **Route 53 Resolver DNS Firewall** |

---

## 🎯 KEY FACTS — BẢNG TRA CỨU NHANH

### CloudWatch

| Chủ đề | Giá trị / Điểm quan trọng |
|---|---|
| Basic Monitoring | 5 phút, **miễn phí** |
| Detailed Monitoring | 1 phút, **có phí** |
| ASG metrics | 1 phút, **miễn phí** (bật riêng) |
| Custom metrics (memory, disk) | Cần **CloudWatch Agent** |
| Composite Alarms | Kết hợp nhiều alarm (AND/OR/NOT) |
| Alarm states | OK, ALARM, **INSUFFICIENT_DATA** |
| CloudWatch Logs retention default | **Never expire** |
| StatusCheckFailed_System → Action | **Stop + Start** (migrate host) |
| StatusCheckFailed_Instance → Action | User must investigate OS/app |
| EC2 Recovery (CloudWatch) | Giữ: instance ID, private IP, EIP, public IPv4; Mất: RAM data |

### Auto Scaling

| Chủ đề | Giá trị |
|---|---|
| Cooldown default | **300 giây** |
| Cooldown áp dụng cho | **Simple Scaling** (không phải Target Tracking) |
| Lifecycle hook default timeout | **3600 giây** (1 giờ) |
| Spread Placement Group | Tối đa **7 instances/AZ/group** |
| ASG scaling policies recommended | **Target Tracking** |
| ASG không thể span | **Nhiều Regions** (chỉ nhiều AZs) |

### RDS & Database

| Chủ đề | Giá trị |
|---|---|
| RDS backup retention | **0–35 ngày** (default: 7) |
| Không set retention = 0 khi | Có **Read Replicas** |
| Aurora Backtracking | **Không tạo DB mới**; rewind trong phút |
| Aurora PITR | **Tạo DB mới**; trong retention period |
| Aurora Global Database replication lag | **< 1 giây** |
| DynamoDB PITR | **35 ngày** |
| ElastiCache Memcached evictions | **Thêm nodes** |
| ElastiCache Redis Multi-AZ | ✅; Memcached ❌ |
| RDS Proxy | Giải quyết **"too many connections"** |
| Oracle RAC on RDS | ❌ Không hỗ trợ → dùng **EC2** |

### EBS & Storage

| Chủ đề | Giá trị |
|---|---|
| gp3 max IOPS | **16,000** (độc lập với size) |
| io1/io2 max IOPS | **64,000** (Nitro) |
| io2 Block Express max IOPS | **256,000** |
| RAID 0 | Tăng **IOPS/throughput**; no fault tolerance |
| RAID 1 | Fault tolerance; không cải thiện write |
| EBS Multi-Attach | Chỉ **io1/io2** |
| S3 Multipart Upload bắt buộc | **> 5 GB** |
| S3 Transfer Acceleration | Upload qua **CloudFront edge** |

### Networking

| Chủ đề | Giá trị |
|---|---|
| VPC CIDR range | **/16** (max) đến **/28** (min) |
| AWS reserved IPs/subnet | **5 IPs** đầu tiên |
| VPC default limit/region | **5 VPCs** |
| NAT Gateway max bandwidth | **45 Gbps** |
| NAT Gateway IPv6 | ❌ Không hỗ trợ |
| Egress-Only IGW | **IPv6 only**, outbound only |
| Custom NACL ephemeral ports | **1024–65535** |
| Gateway Endpoint services | **S3** và **DynamoDB** (miễn phí) |
| VPC Peering | Không **transitive** |
| ACM cert cho CloudFront | Phải ở **us-east-1** |
| Route 53 Inbound Endpoint | On-prem → AWS DNS resolution |
| Route 53 Evaluate Target Health | Route 53 detect ALB/ELB failure |
| Alias Record zone apex | ✅ Được; CNAME ❌ không được |

### Security

| Chủ đề | Giá trị |
|---|---|
| S3 MFA access | Enable MFA cho user **+** Bucket Policy condition |
| KMS CMK auto rotation | Optional, mỗi **1 năm** |
| KMS AWS managed key rotation | Tự động, **1 năm** |
| SCP | Restrict **maximum permissions**; không grant |
| SCP không ảnh hưởng | **Management account**, service-linked roles |
| Firewall Manager admin change | Current admin revoke → Management account designate new |
| Cognito + ADFS | **User Pool** + ADFS làm SAML IdP |
| Inspector v2 scan | EC2 + ECR + **Lambda** |
| GuardDuty data sources | VPC Flow Logs, CloudTrail, DNS logs |
| SSM Session Manager | Không cần SSH key, port 22, bastion |
| SSM Parameter Store free tier | **Standard** tier miễn phí |
| Secrets Manager auto-rotation | ✅ (Lambda-backed) |

### CloudFormation

| Chủ đề | Giá trị |
|---|---|
| WaitCondition timeout → Fix | Thêm **cfn-signal** vào user data |
| DependsOn | Kiểm soát thứ tự tạo resources |
| Change Sets | Preview changes trước khi apply |
| Drift Detection | Phát hiện manual changes ngoài CFN |
| StackSets | Deploy sang **nhiều accounts/regions** |
| Nested Stacks | Tái sử dụng template components |
| cfn-hup | Detect metadata changes → re-run cfn-init |

---

## 📚 AWS SERVICES IN-SCOPE — ĐẶC ĐIỂM KEY

### Amazon Athena
- Serverless SQL query engine cho **S3**.
- Phân tích ELB access logs, CloudTrail logs, VPC Flow Logs lưu trong S3.
- Pay per query (per TB scanned).

### Amazon Data Firehose
- **Near-real-time** stream delivery đến S3, Redshift, OpenSearch, Splunk.
- Không cần manage consumers.

### AWS Step Functions
- **Serverless orchestration** của Lambda functions và services.
- Visual workflows (state machines).

### AWS Compute Optimizer
- Phân tích utilization data → Đề xuất right-sizing cho EC2, Lambda, EBS, ECS, Auto Scaling.
- **Chỉ đề xuất** — Không tự thay đổi.

### Amazon Application Recovery Controller (ARC)
- **Readiness checks**: Verify resources deployed đủ capacity cho recovery.
- **Routing controls**: Manually shift traffic giữa Regions/AZs.
- Dùng cho DR drill và actual failover.

### VPC IPAM (IP Address Manager)
- Quản lý và monitor IP address space tập trung.
- Tích hợp với AWS Organizations.
- Cảnh báo khi IP ranges overlap hoặc exhausted.

---

## ❌ NGOÀI PHẠM VI THI

**Job Tasks Out of Scope:**
- Design distributed architectures
- Design CI/CD pipelines
- Design hybrid/multi-VPC networking
- Develop software
- Define security/compliance/governance requirements
- Develop ransomware defense strategies
- Assess and plan resource capacity
- Analyze costs and TCO
- Manage billing and invoicing

**AWS Services Out of Scope (chọn lọc):**
- AWS CloudHSM, Amazon Neptune, Amazon Timestream
- AWS AppConfig, Amazon EMR, Amazon MSK
- AWS CloudWAN, AWS App Mesh
- Amazon Lightsail, AWS Nitro Enclaves
- AWS CodeGuru, Amazon Kendra, Amazon Lex
- AWS Application Migration Service, Migration Hub
- Amazon FSx for OpenZFS
- AWS Payment Cryptography, Amazon Security Lake

---

## 🎯 KINH NGHIỆM ÔN TẬP RÚT RA TỪ PDF TUTORIALS DOJO

### 1. Học theo “mẫu vận hành” thay vì học rời từng service

Với SOA-C03, nhiều câu hỏi không kiểm tra định nghĩa service đơn lẻ mà kiểm tra tư duy vận hành theo chuỗi:

**Metric/Log → Alarm/Rule → Event → Automated Remediation → Audit/Root Cause**

Mẫu suy nghĩ này cần phản xạ nhanh:
- **CloudWatch**: metrics, logs, alarms, dashboards.
- **EventBridge**: định tuyến sự kiện gần real-time sang target.
- **Systems Manager**: automation, remediation, patching, ops.
- **CloudTrail**: audit API activity, ai làm gì, khi nào.
- **AWS Config**: kiểm tra trạng thái cấu hình và compliance.

Nếu đề hỏi “phát hiện, cảnh báo, tự động xử lý”, đừng chỉ nhìn một service. Hãy map cả luồng vận hành.

### 2. PDF này có xu hướng ra bẫy theo kiểu so sánh dịch vụ

Từ phần giữa đến cuối tài liệu, nhiều nội dung quan trọng nằm ở các cặp so sánh. Đây là nhóm cần học thuộc ở mức phản xạ:

- **CloudWatch vs CloudTrail**
  - **CloudWatch**: monitoring metrics/logs, alarm, operational visibility.
  - **CloudTrail**: audit API calls, governance, compliance, forensic trail.

- **CloudWatch vs EventBridge**
  - **CloudWatch** giỏi quan sát và cảnh báo.
  - **EventBridge** giỏi route event gần real-time sang service khác.

- **CloudWatch Agent vs SSM Agent**
  - **CloudWatch Agent**: thu thập system metrics/logs như memory, disk, custom OS metrics.
  - **SSM Agent**: remote command, patching, session, automation.

- **ELB Health Check vs Route 53 Health Check**
  - **ELB Health Check**: kiểm tra target phía sau load balancer.
  - **Route 53 Health Check**: phục vụ DNS failover/routing decision ở mức endpoint.

- **SCP vs IAM Policy**
  - **SCP**: giới hạn trần quyền ở cấp Organization/OU/account, không tự cấp quyền.
  - **IAM Policy**: cấp/giới hạn quyền cho principal hoặc resource cụ thể.

- **S3 Pre-signed URL vs CloudFront Signed URL/Cookie vs OAC**
  - **Pre-signed URL**: cấp truy cập tạm thời trực tiếp đến object S3.
  - **CloudFront Signed URL/Cookie**: bảo vệ nội dung private qua CDN.
  - **OAC**: buộc truy cập S3 thông qua CloudFront, chặn truy cập trực tiếp từ public endpoint.

- **Latency vs Geolocation vs Geoproximity routing**
  - **Latency**: chọn nơi có độ trễ thấp nhất.
  - **Geolocation**: route theo vị trí người dùng.
  - **Geoproximity**: route theo vị trí tài nguyên/người dùng có thể bias traffic.

- **Redis cluster mode disabled vs enabled vs Memcached**
  - **Memcached**: đơn giản, scale cache nhanh, không persistence.
  - **Redis non-clustered**: tính năng phong phú, replica, persistence.
  - **Redis clustered**: sharding + scale lớn + HA.

Nếu chưa làm được kiểu “nhìn keyword là loại ngay 2 đáp án”, thì phần so sánh này vẫn chưa đủ chắc.

### 3. Một số con số và facts phải nhớ rất cứng

- **CloudWatch basic monitoring cho EC2**: **5 phút**
- **CloudWatch detailed monitoring cho EC2**: **1 phút**
- **Custom metrics** có thể xuống **1 giây**
- **CloudTrail Event History** mặc định xem được **90 ngày**
- **CloudTrail** thiên về audit, không phải công cụ primary để realtime remediation
- **S3 Multipart Upload** bắt buộc khi object **> 5 GB**
- **ACM certificate cho CloudFront** phải ở **us-east-1**

Đây là nhóm facts dễ bị cài vào distractor answer.

### 4. Cách đọc keyword để chọn đáp án nhanh

Một số từ khóa gần như map trực tiếp sang service:

- **“Who made this API call?”** → **CloudTrail**
- **“Near real-time event routing”** → **EventBridge**
- **“Memory utilization của EC2”** → **CloudWatch Agent / custom metric**
- **“DNS failover between endpoints/regions”** → **Route 53 health check/routing**
- **“Private content via CDN”** → **CloudFront signed URL/cookie hoặc OAC**
- **“Org-wide deny regardless of local IAM allow”** → **SCP**
- **“Patch fleet without SSH/RDP exposure”** → **Systems Manager**

Khi làm practice test, nên highlight keyword rồi tự nói ra service trước khi nhìn đáp án.

### 5. Domain ưu tiên để ôn có hiệu suất cao

Theo nội dung PDF, tần suất xuất hiện dày đặc nhất rơi vào các cụm sau:

- **Monitoring/Logging/Remediation**
  - CloudWatch, Logs, alarms, metric filters, EventBridge, CloudTrail
- **Compute operations**
  - EC2, Auto Scaling, ELB, status checks, launch templates, placement
- **Networking troubleshooting**
  - VPC, route tables, NACL, SG, VPC Flow Logs, Route 53
- **Security operations**
  - IAM, SCP, KMS, Secrets Manager, SSM Session Manager, GuardDuty, Config
- **Storage/DR**
  - EBS, EFS, S3, Backup, DataSync, replication/failover scenarios

Nếu thời gian gấp, hãy ưu tiên học sâu các nhóm trên trước rồi mới quay lại các service ít gặp hơn.

### 6. Chiến lược ôn tập nên áp dụng

1. Ôn theo **domain weight** trước, nhưng chốt kiến thức bằng **scenario**.
2. Với mỗi service, bắt buộc trả lời được 3 câu:
   - Nó dùng để **quan sát**, **kiểm soát**, hay **audit**?
   - Nó hoạt động ở **instance/app**, **network/DNS**, hay **organization/account**?
   - Nó là **detective**, **preventive**, hay **remedial** control?
3. Tạo bảng so sánh ngắn cho các service dễ nhầm, không học bằng đoạn văn dài.
4. Làm practice questions theo cụm chủ đề, sau đó làm mixed set để luyện chuyển ngữ cảnh nhanh.
5. Bổ sung hands-on tối thiểu cho:
   - CloudWatch alarm + SNS/EventBridge
   - CloudTrail tra cứu API event
   - SSM Session Manager / Run Command
   - Route 53 routing policies
   - Auto Scaling + ELB health behavior

### 7. Kết luận thực dụng

PDF này mạnh ở phần **bao phủ chủ đề** và **so sánh dịch vụ**, nhưng chỉ dùng nó thôi là chưa đủ. Cách ôn hiệu quả nhất vẫn là:

- Dùng tài liệu này để đóng các lỗ hổng khái niệm.
- Dùng practice tests để luyện loại nhiễu và nhận keyword.
- Dùng lab ngắn để biến kiến thức từ “nhớ mặt” thành “biết vận hành”.

Nếu mục tiêu là đỗ chắc, đừng ôn theo kiểu học thuộc service list. Hãy ôn theo **tình huống vận hành thực tế** và **quyết định chọn đúng service trong bối cảnh áp lực thời gian**.

---

## 🧩 BỔ SUNG SAU KHI OCR PDF TUTORIALS DOJO 261 TRANG

> Phần này là các ý bổ sung sau khi quét toàn bộ PDF Tutorials Dojo Study Guide v3.0. Ưu tiên những điểm còn mỏng trong ghi chú hiện tại: scenario map, runbook vận hành, và bẫy so sánh dịch vụ.

### 1. Scenario Map Cần Phản Xạ Nhanh

| Tình huống trong đề | Dịch vụ / hướng xử lý |
|---|---|
| Cảnh báo khi Trusted Advisor check/service limit thay đổi | **EventBridge** bắt event từ Trusted Advisor |
| Audit hành động delete/rotate KMS key | **CloudTrail** log KMS API calls |
| Kiểm tra traffic có tới EC2 hay không | **VPC Flow Logs** |
| Bảo đảm SSH luôn bị tắt trên private server | **AWS Config Rule** + có thể remediate bằng **SSM Automation** |
| Lấy EC2 instance metadata | `http://169.254.169.254/latest/` |
| Monitor CPU của một process đơn lẻ trên EC2 | **CloudWatch Agent** với plugin `procstat` |
| Báo cáo trạng thái replication/encryption của object S3 | **S3 Inventory** |
| Alarm khi toàn bộ target sau ALB unhealthy | Metric `AWS/ApplicationELB HealthyHostCount` |
| Email khi có IAM `CreateUser` API call | **EventBridge** dùng CloudTrail event pattern + target SNS |
| Tự động patch security updates cho managed instances | **Systems Manager Patch Manager** |
| Query dữ liệu đang nằm trong S3 bằng SQL | **Amazon Athena** |
| Static S3 website chậm với user toàn cầu | **CloudFront distribution** đặt S3 làm origin |
| Enforce tag khi provision resource qua catalog | **AWS Service Catalog TagOption** |
| ASG xử lý SQS message bị backlog | Scale ASG theo **queue depth / messages in queue** |
| Cần log client IP, latency, request path, response từ ALB | **ALB access logs** lưu vào S3 |
| Queue pressure trên Classic Load Balancer | Metric `SurgeQueueLength` |
| Redshift snapshot phải có ở Region khác | Bật **automated snapshot copy** sang Region khác |
| SMB file server HA, dùng Windows ACL | **FSx for Windows File Server Multi-AZ** |
| Upload object lớn lên S3 chậm do xa Region | **S3 Transfer Acceleration** |
| EFS `PercentIOLimit = 100%` | Tạo EFS **Max I/O** mới và migrate bằng **DataSync** |
| Backup EBS/EC2 cần file-system consistency | `CreateImage` có reboot, schedule bằng Lambda + EventBridge |
| Chạy shell script từ xa trên EC2 an toàn | **SSM Run Command** |
| Phát hiện config drift của CloudFormation | **Drift Detection** |
| Reuse CloudFormation template cho nhiều môi trường | **Nested Stacks** |
| CloudFormation luôn lấy latest AMI ID | **SSM Parameter Store** dynamic parameter |
| ElastiCache Memcached eviction tăng cao | Scale bằng cách **thêm nodes** |
| Tạo account mới kèm guardrails/baseline | **AWS Control Tower** |
| Object S3 > 60 ngày chuyển sang IA | **S3 Lifecycle policy** |
| Redshift COPY/UNLOAD traffic cần đi trong VPC | **Enhanced VPC Routing** |
| Public TLS cert tự renew | **AWS Certificate Manager (ACM)** |
| KMS key dùng imported key material cần rotate định kỳ | Tạo key mới/import material mới, cập nhật key ID/alias |
| User cần pass role cho AWS service | IAM permission `iam:PassRole` |
| Private EC2 gọi KMS không đi Internet | **VPC endpoint** cho KMS |

### 2. EC2 Operations Còn Dễ Bị Bỏ Sót

#### EC2 Purchasing & Capacity

| Option | Điểm nhớ nhanh |
|---|---|
| **Compute Savings Plans** | Linh hoạt nhất: áp dụng qua instance family, size, AZ, Region, OS, tenancy; cũng áp dụng cho Fargate và Lambda. |
| **EC2 Instance Savings Plans** | Giá thấp hơn nhưng bị ràng buộc theo instance family trong một Region. |
| **Reserved Instances** | Ít linh hoạt hơn Savings Plans; Standard RI có thể bán lại trên Marketplace, Convertible RI đổi thuộc tính nếu giá trị mới >= cũ. |
| **Spot Instances** | Rẻ cho workload interruptible; có **2 phút cảnh báo** trước khi bị stop/terminate khi mất capacity/giá vượt ngưỡng. |
| **Dedicated Hosts** | Trả tiền theo host, thấy socket/core/host ID, phù hợp BYOL theo socket/core/VM. |
| **Dedicated Instances** | Chạy trên single-tenant hardware nhưng không thấy socket/core; EBS volume không nằm trên single-tenant hardware. |
| **Capacity Reservation** | Reserve capacity trong một AZ, không nhất thiết có commitment dài hạn. |

#### Placement Groups

| Loại | Dùng khi | Bẫy cần nhớ |
|---|---|---|
| **Cluster** | HPC, ML, workload cần low latency/high throughput giữa instances | Trong một AZ; nên launch cùng lúc và cùng instance type để giảm lỗi insufficient capacity. |
| **Partition** | HDFS, HBase, Cassandra, app topology-aware | Tách logical partitions theo rack/power/network; tối đa **7 partitions/AZ**. |
| **Spread** | Workload nhỏ nhưng cần giảm correlated hardware failure | Mỗi instance tách rack; tối đa **7 running instances/AZ/group**. |

#### Storage IOPS Cho EC2

- Nếu cần persistence + IOPS cao: ưu tiên **EBS Provisioned IOPS** như `io2`/`io2 Block Express`.
- Nếu cần latency cực thấp và dữ liệu có thể mất khi stop/terminate: **instance store** có thể phù hợp hơn vì gắn vật lý vào host.
- Nitro-based instances cho EBS Provisioned IOPS cao hơn các instance cũ; nhớ kiểm tra giới hạn IOPS/throughput theo instance type.

#### EC2 Image Builder

- Dùng khi ASG launch chậm vì UserData cài quá nhiều dependency hoặc cần golden image chuẩn hóa.
- Pipeline gồm: **source image** → **image recipe** → **build/test components** → storage → infrastructure config → distribution settings.
- Image recipe có version control; build/test components có thứ tự chạy.
- Image Builder dùng **SSM Agent** trong quá trình build; role cần quyền cho toàn bộ build/test components.
- Output có thể là AMI hoặc Docker image; AMI có thể share/copy theo Region, Docker image đẩy vào ECR.

#### EC2Rescue Runbook

- **Windows offline rescue**: detach root EBS volume từ instance lỗi, attach vào rescue host **cùng AZ**, chạy EC2Rescue để diagnose/restore/capture logs.
- EC2Rescue có thể kiểm tra hoặc sửa các lỗi như RDP disabled, Windows Firewall, DHCP/network interface, EC2Launch, system time, password regeneration.
- Có mode **current instance** để đọc cấu hình/log và mode **offline instance** để xử lý root volume gắn ngoài.
- **Linux**: dùng EC2Rescue for Linux hoặc SSM Automation document như `AWSSupport-TroubleshootSSH` khi cần troubleshoot SSH/boot/network.
- Trước khi rescue hoặc sửa offline volume, luôn nghĩ tới snapshot/backup để rollback.

### 3. Storage, CDN & Data Movement

#### S3 Pre-signed URL

- Bucket/object S3 private mặc định; pre-signed URL cấp quyền tạm thời theo **credential của người tạo URL**.
- URL có action cụ thể: `GET` để download, `PUT` để upload.
- Người upload/download qua URL không cần AWS credential riêng, nhưng URL hết hạn theo expiry và credential dùng để ký.
- Nếu cần private content qua CDN, so sánh nhanh:
  - **S3 pre-signed URL**: truy cập trực tiếp S3 tạm thời.
  - **CloudFront signed URL/cookie**: kiểm soát private content qua CDN.
  - **OAC**: ép user đi qua CloudFront, chặn direct S3 URL.

#### CloudFront Cache Policy vs Origin Request Policy

- **Cache Policy** quyết định cache key: headers, cookies, query strings nào tham gia cache.
- **Origin Request Policy** quyết định dữ liệu nào được forward về origin.
- Cache key càng nhiều biến như header/cookie/query string thì cache hit ratio càng giảm.
- Muốn tăng cache hit ratio: dùng `Cache-Control: max-age` hợp lý, tăng TTL khi phù hợp.
- Nếu mobile bị nhận desktop version, cân nhắc forward `User-Agent` hoặc dùng chính sách cache/origin request phù hợp.

#### S3 Transfer Acceleration vs Snowball vs Direct Connect vs VPN

| Nhu cầu | Chọn |
|---|---|
| Client phân tán toàn cầu upload S3 qua public Internet | **S3 Transfer Acceleration** |
| Di chuyển batch dữ liệu rất lớn, Internet mất quá lâu | **Snowball** |
| Cần private dedicated connectivity ổn định tới AWS | **Direct Connect** |
| Cần private encrypted tunnel qua Internet | **Site-to-Site VPN / IPsec VPN** |

#### EFS, FSx, DataSync, Transfer Family

- **EFS Access Point**: tạo entry point cho app, enforce root directory/POSIX user/permission, hữu ích khi nhiều app dùng chung file system.
- Mount EFS nên dùng mount helper + TLS; mount qua DNS là chính, IP dùng khi cần xử lý trường hợp đặc biệt.
- **FSx for Windows File Server**: SMB, Windows ACL, AD integration, có Multi-AZ, audit log có thể gửi CloudWatch Logs hoặc Kinesis Data Firehose.
- **FSx for Lustre**: HPC/ML, sub-ms latency, throughput rất cao; scratch cho short-term/non-critical, persistent cho long-term; tích hợp S3 import/export.
- **DataSync**: online transfer/migration/sync giữa on-prem và AWS storage hoặc giữa AWS storage; agent chạy trên VMware/Hyper-V/KVM/EC2 khi nguồn on-prem.
- DataSync task có các knobs hay ra đề: data verification, bandwidth limit, transfer mode, delete behavior ở destination, filter, schedule, CloudWatch logging.
- **AWS Transfer Family**: managed SFTP/FTPS/FTP/AS2 endpoint vào S3 hoặc EFS; dùng khi cần giữ workflow/client file transfer truyền thống.

#### AWS Backup

- Khái niệm chính: **backup plan**, backup rule/schedule/lifecycle, resource assignment theo tag/resource ID, **backup vault**, recovery point, backup/restore jobs.
- Vault dùng KMS để mã hóa backup; có thể có default vault hoặc nhiều vault.
- Tích hợp AWS Organizations để cross-account backup, monitoring, và backup policies.
- Hỗ trợ centralized backup cho EC2, EBS, RDS/Aurora, DynamoDB, EFS, FSx, S3, Storage Gateway, v.v.

### 4. Database & Analytics Operations

#### RDS

- DB instance class: Standard, Memory Optimized, Burstable; chọn theo CPU/memory pattern.
- **Multi-AZ** = HA/failover; **Read Replica** = scale read/performance, không thay thế Multi-AZ.
- Automated backup tạo PITR; retention có thể cấu hình, tối đa thường là **35 ngày**.
- Khi delete DB instance: kiểm tra **deletion protection** và cân nhắc **final snapshot**.
- **RDS Proxy**: connection pooling, giảm burst connections từ Lambda/app; có thể enforce TLS, target là DB instance hoặc Aurora cluster.
- RDS encryption bằng KMS áp dụng cho storage, automated backups, snapshots, và read replicas liên quan.

#### Aurora / DynamoDB / ElastiCache

- **Aurora**: storage tự tăng, tối đa cao hơn RDS engine truyền thống; có custom endpoints, replica auto scaling, Global Database cho multi-Region.
- **DynamoDB**: serverless NoSQL, global tables, PITR, encryption at rest mặc định; DAX giảm read latency từ milliseconds xuống microseconds cho read-heavy workload.
- **Redis vs Memcached**:
  - Redis: data structures phong phú, persistence, backup, replication, Multi-AZ/auto failover.
  - Redis cluster mode enabled: sharding để scale lớn.
  - Memcached: đơn giản, multi-threaded, scale ngang cache object đơn giản, không HA/persistence như Redis.
- Memcached eviction vượt ngưỡng thường xử lý bằng tăng số node hoặc tăng capacity.

#### OpenSearch

- Dùng cho full-text search, log analytics, real-time app monitoring, security analytics.
- Nếu câu hỏi nói gần real-time search/analytics trên log/event, nhớ phân biệt với Athena (SQL over S3, không phải search engine realtime).

### 5. Monitoring, Logging, Remediation

- **Metric Filter**: biến log pattern trong CloudWatch Logs thành custom metric để alarm.
- CloudWatch Alarm action có thể là SNS notification, EC2 action, Auto Scaling action, hoặc integration qua EventBridge/Lambda tùy bài.
- Threshold type có thể static hoặc anomaly detection; anomaly detection học baseline từ dữ liệu lịch sử.
- **CloudTrail Event History** xem management events gần đây trong **90 ngày**; muốn lưu lâu/query bằng Athena thì tạo trail vào S3.
- Trail có thể bật SSE-KMS, log file validation, SNS notification, và optional delivery sang CloudWatch Logs.
- **AWS Health Dashboard**: personalized/account-specific service events, open issues, scheduled changes; khác Trusted Advisor vì Health tập trung vào sự kiện ảnh hưởng tài khoản/tài nguyên.
- **AWS Config**: lưu configuration history vào S3, rule evaluate khi config change hoặc theo schedule; remediation thường chạy bằng SSM Automation.
- **Change Manager**: workflow kiểm soát thay đổi across accounts/Regions; phù hợp môi trường cần approval/change control.

### 6. Security & Governance Bổ Sung

- KMS automatic rotation không áp dụng cho key có imported key material, custom key store/CloudHSM, hoặc HMAC KMS keys.
- Nếu cần rotate imported key material định kỳ: tạo key/material mới, cập nhật alias/key reference trong app/workload.
- S3 encryption:
  - **SSE-S3**: AWS managed S3 keys.
  - **SSE-KMS**: KMS key, audit/control tốt hơn.
  - **SSE-C**: customer-provided key.
  - **Client-side encryption**: mã hóa trước khi gửi lên S3.
- EFS in transit: dùng TLS khi mount bằng EFS mount helper.
- RDS TLS dùng server certificate; TDE trên Oracle/SQL Server có thể có overhead nếu dùng cùng encryption at rest.
- **IAM Access Analyzer**: định nghĩa zone of trust theo account hoặc organization, scan resource policies và báo external access.
- **Detective**: điều tra security findings/root cause sau khi GuardDuty/Security Hub phát hiện.
- **Directory Service**: chọn khi cần managed Microsoft AD/AD Connector/Simple AD cho workload Windows/enterprise identity.
- Billing/governance chỉ nên học để nhận diện service:
  - **Cost Explorer**: usage/cost pattern, RI/SP reports.
  - **Cost Allocation Tags**: phân bổ chi phí theo tag.
  - **CUR**: detailed billing/usage report lưu S3, query bằng Athena, visualize bằng QuickSight.
  - **License Manager**: BYOL/license inventory, có thể mở rộng across Organizations.

### 7. Networking & DNS Edge Cases

- Route table target hay gặp: IGW, NAT Gateway, Egress-only IGW, TGW, VGW, VPC peering, GWLB endpoint, ENI, local route.
- **Egress-only Internet Gateway**: outbound-only cho IPv6, chặn inbound từ Internet.
- VPC Flow Logs có thể capture accept/reject/all traffic, aggregation interval 1 hoặc 10 phút.
- **Traffic Mirroring**: mirror packet từ ENI nguồn sang target để IDS/forensics; không thay đổi traffic gốc.
- Route 53 health check có 3 kiểu: endpoint, calculated health check, CloudWatch alarm state.
- Route 53 Resolver:
  - **Inbound endpoint**: on-prem/peered VPC forward DNS query vào Route 53 Resolver.
  - **Outbound endpoint**: VPC forward query ra DNS resolver ngoài theo Resolver rules.
  - Nên cấu hình ít nhất 2 IP ở 2 AZ để tăng reliability.
- Routing policy bẫy:
  - **Latency**: chọn Region latency thấp nhất, không đảm bảo cùng geography luôn cùng Region.
  - **Geolocation**: route theo vị trí user.
  - **Geoproximity**: route theo vị trí user + resource, có thể dùng bias; cần Traffic Flow.

### 8. CloudFront SSL & Agent Comparison

#### SNI Custom SSL vs Dedicated IP Custom SSL

| | SNI Custom SSL | Dedicated IP Custom SSL |
|---|---|---|
| Dùng khi | Client/browser hiện đại hỗ trợ SNI | Client cũ không hỗ trợ SNI |
| Cách hoạt động | Nhiều domain dùng chung IP nhờ SNI trong TLS handshake | CloudFront cấp dedicated IP tại edge locations |
| Chi phí | Thường là lựa chọn mặc định, không cần dedicated IP charge | Đắt hơn do dedicated IP |
| Mức bảo mật | Tương đương nếu client hỗ trợ | Tương đương, phục vụ compatibility |

#### CloudWatch Agent vs SSM Agent vs Custom Script

| Tool | Dùng để |
|---|---|
| **CloudWatch Agent** | Thu thập memory/disk/process metrics, logs, StatsD/collectd custom metrics. |
| **SSM Agent** | Nhận lệnh từ Systems Manager: Run Command, Patch, Session Manager, Automation. |
| **Custom daemon/script** | Khi cần logic đặc thù hoặc policy không cho dùng agent có quyền cao như SSM Agent. |

---

## ✅ FINAL GAP CLOSURE — PHẦN BỔ SUNG SAU ĐÁNH GIÁ KHẮT KHE

> Mục này chốt những phần còn mỏng so với danh sách in-scope SOA-C03. Ưu tiên học theo tình huống vận hành, không học theo kiểu thuộc lòng service catalog.

### 1. Application Integration Operations: SNS, SQS, EventBridge, Step Functions

| Service | Dùng khi | Bẫy đề thi |
|---|---|---|
| **SNS** | Fan-out notification đến email/SMS/HTTPS/SQS/Lambda; CloudWatch Alarm gửi notification. | SNS không giữ message để consumer pull lại như queue; cần subscription policy/KMS policy đúng. |
| **SQS Standard** | Decouple producer/consumer, retry async workload, buffer spike traffic. | At-least-once delivery và best-effort ordering; consumer phải idempotent. |
| **SQS FIFO** | Cần ordering theo message group và exactly-once processing logic ở mức queue. | Throughput thấp hơn Standard; cần message group ID và deduplication. |
| **EventBridge** | Route AWS/service/custom/SaaS events theo pattern; event-driven automation. | Rule match đúng chưa đủ; target cần permission, retry policy và DLQ. |
| **Step Functions** | Orchestrate nhiều bước Lambda/AWS SDK/service integrations, approval/retry/branching. | Không dùng Step Functions cho một tác vụ đơn giản có thể xử lý bằng một Lambda hoặc SSM Automation runbook. |

**Scenario cần nhớ:**  
S3 upload object → EventBridge/S3 Event Notification → Lambda xử lý → lỗi thì gửi SQS DLQ → CloudWatch Alarm trên DLQ depth → SNS/User Notifications báo vận hành.

### 2. Containers & Image Operations: ECR, ECS, EKS

| Chủ đề | Điểm SOA-C03 cần nắm |
|---|---|
| **Amazon ECR** | Private container registry; scan image vulnerabilities; lifecycle policy xóa image cũ; IAM permission cho push/pull. |
| **ECS task logs** | Dùng `awslogs` log driver hoặc FireLens; task execution role cần quyền ghi CloudWatch Logs và pull ECR image. |
| **ECS service scaling** | Scale task count theo CPU/memory/custom metric/SQS queue depth; ALB target group health ảnh hưởng deployment. |
| **EKS observability** | CloudWatch Observability add-on/agent, Container Insights, Prometheus metrics; IRSA/service account permission là bẫy thường gặp. |
| **Private subnet containers** | Nếu không có NAT, cần VPC endpoints cho ECR API/DKR, S3 gateway endpoint cho image layers, CloudWatch Logs, STS/SSM tùy workload. |

### 3. Developer Tools In-Scope: AWS X-Ray

- **X-Ray** dùng để trace request qua microservices, Lambda, API Gateway, ECS/EKS/EC2 app, giúp thấy latency từng segment/subsegment.
- CloudWatch metrics/logs trả lời “cái gì đang cao/lỗi”; **X-Ray** trả lời “request chậm ở service/segment nào”.
- Bẫy: X-Ray không thay CloudTrail. X-Ray trace app request; CloudTrail audit API calls.
- Khi app distributed có latency tăng nhưng CPU/RDS/ALB metrics không đủ kết luận, bật tracing bằng X-Ray SDK/daemon/agent hoặc service integration.

### 4. Database Operations Còn Mỏng: Aurora Serverless v2, DAX, RDS Proxy

| Service/feature | Dùng khi | Không nên chọn khi |
|---|---|---|
| **Aurora Serverless v2** | Workload database biến động, cần scale capacity mịn hơn theo ACU và vẫn dùng Aurora capabilities. | Cần control instance cố định, engine/feature không hỗ trợ, hoặc workload steady có Reserved capacity rẻ hơn. |
| **DAX** | DynamoDB read-heavy, cần latency microseconds, eventual consistency chấp nhận được. | Workload write-heavy, cần strongly consistent reads, hoặc hot partition do partition key xấu. |
| **RDS Proxy** | Lambda/app mở nhiều connection ngắn gây `Too many connections`; cần pooling và failover tốt hơn. | Bottleneck là query/index/storage I/O chứ không phải connection storm. |

### 5. Cloud Financial Management In-Scope Nhưng Chỉ Học Ở Góc Vận Hành

| Công cụ | Cần biết để làm gì |
|---|---|
| **Cost Explorer** | Xem cost/usage trend, lọc theo service/tag/account, xem RI/Savings Plans utilization/coverage. |
| **Cost and Usage Reports (CUR)** | Báo cáo chi tiết nhất, lưu S3, query bằng Athena; dùng khi cần phân tích sâu theo account/tag/resource. |
| **Savings Plans** | Cam kết spend theo giờ để giảm giá EC2/Fargate/Lambda; Compute Savings Plans linh hoạt hơn EC2 Instance Savings Plans. |
| **Cost allocation tags** | Bắt buộc nếu đề nói chargeback/showback hoặc cost theo team/project. |

**Bẫy scope:** SOA-C03 không yêu cầu phân tích TCO/billing sâu. Chỉ cần biết công cụ nào giúp CloudOps nhìn usage/cost bất thường và khuyến nghị tối ưu.

### 6. Governance/Provisioning In-Scope Còn Mỏng: Control Tower, Service Catalog, IPAM

- **AWS Control Tower**: tạo landing zone multi-account với guardrails; dùng khi đề nói tạo account mới có baseline, SCP, logging, audit.
- **AWS Service Catalog**: cho phép user provision sản phẩm đã chuẩn hóa; dùng TagOptions để enforce tagging và giới hạn template được dùng.
- **VPC IPAM**: quản lý CIDR tập trung, phát hiện overlap/exhaustion, hỗ trợ multi-account/Organizations; dùng khi đề nói subnet/VPC CIDR lộn xộn hoặc cần cấp phát IP có kiểm soát.
- **AWS RAM**: share subnet/TGW/Resolver rules/resource giữa account; không copy resource.

### 7. Priority Correction: Nội Dung Có Ích Nhưng Không Nên Ôn Sâu Cho SOA-C03

| Nội dung trong note | Cách học đúng |
|---|---|
| **OpenSearch** | Chỉ nhận diện nếu gặp log/search analytics; không phải trọng tâm in-scope đã liệt kê. Athena/Data Firehose/CloudWatch Logs quan trọng hơn cho SOA-C03. |
| **Detective** | Hữu ích thực tế cho điều tra security, nhưng đề SOA-C03 ưu tiên Security Hub, GuardDuty, Config, Inspector, Macie. |
| **Directory Service** | Chỉ đọc nếu câu hỏi có AD/identity integration; trọng tâm vẫn là IAM, IAM Identity Center, federation. |
| **License Manager** | Chỉ nhận diện BYOL/license inventory; không học sâu billing/licensing. |
| **CodeCommit/CodeBuild/CodePipeline chi tiết** | SOA-C03 có deployment strategy và Git/Terraform ở mức vận hành; không cần thiết kế CI/CD pipeline sâu. |

### 8. Final Exam-Readiness Checklist

Trước khi làm mock exam, tự kiểm được các câu sau:

1. Metric nào chứng minh EC2 host lỗi, OS lỗi, EBS nghẽn, ALB target unhealthy, DynamoDB throttle?
2. Alarm nào gửi SNS, alarm nào kích Auto Scaling, alarm nào nên chuyển qua EventBridge/SSM Automation?
3. Khi EventBridge không invoke target, permission nằm ở rule role hay resource-based policy của target?
4. Khi AccessDenied, đã kiểm SCP, permission boundary, session policy, resource policy, endpoint policy, KMS key policy chưa?
5. Khi private subnet không gọi AWS service, có NAT hay VPC endpoint phù hợp chưa?
6. Khi CloudFront trả nội dung cũ hoặc 403 từ S3, đã kiểm TTL/cache key/OAC/bucket policy/KMS key policy chưa?
7. Khi cần restore database, đề hỏi RTO/RPO hay chỉ snapshot retention?
8. Khi deployment fail, có đọc CloudFormation events, cfn logs, CloudTrail, IAM `iam:PassRole`, subnet IP availability chưa?

---

*Tài liệu tổng hợp: AWS SOA-C03 Exam Guide v1.1 + Tutorials Dojo Study Guide v3.0 (OCR 261 trang) + AWS Official Documentation*  
*Hiệu lực: SOA-C03 từ 30/09/2025 | Điểm đạt: 720/1000*

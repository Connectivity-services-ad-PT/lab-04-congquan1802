# RUN_LOCAL.md – Hướng dẫn chạy Lab 04

Tài liệu này giúp người khác clone repo sạch và chạy lại service bằng Docker.

1. Clone repo và vào thư mục dự án

```bash
git clone <repo-url>
cd lab-04-congquan1802
```

2. Cài dependencies cho Newman và các công cụ kiểm thử

```bash
npm install
```

3. Build Docker image

```bash
docker build -t fit4110/iot-ingestion:lab04 .
```

4. Chạy container với `.env.example`

```bash
docker run -d --rm --name fit4110-iot-lab04 -p 8000:8000 --env-file .env.example fit4110/iot-ingestion:lab04
```

Kiểm tra health endpoint:

```bash
curl http://localhost:8000/health
```

5. Chạy Newman test và tạo báo cáo

```bash
npm run test:local
```

Báo cáo sẽ xuất ra:

```text
reports/newman-lab04-local.xml
reports/newman-lab04-local.html
```

Nếu cần dừng container:

```bash
docker stop fit4110-iot-lab04
```

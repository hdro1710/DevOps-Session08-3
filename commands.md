# Push payment-service lên GHCR

Thay `hdro1710` bằng username GitHub của bạn (viết thường toàn bộ).

## 1. Tạo PAT (làm trên web GitHub)
Settings -> Developer settings -> Personal access tokens -> Tokens (classic) -> Generate new token (classic)
- Scope: `write:packages` (tự kèm `read:packages`); không chọn `repo`/`delete:packages` nếu không cần
- Lưu token vào biến môi trường (không dán token vào file nộp)

## 2. Đăng nhập
```bash
export GHCR_PAT=<token>
echo $GHCR_PAT | docker login ghcr.io -u hdro1710 --password-stdin
```

## 3. Build và gắn tag
```bash
cd payment-service
docker build -t payment-service:1.0.0 .
docker tag payment-service:1.0.0 ghcr.io/hdro1710/payment-service:1.0.0
docker images | grep payment-service
```

## 4. Push
```bash
docker push ghcr.io/hdro1710/payment-service:1.0.0
```

## 5. Kiểm tra
https://github.com/hdro1710?tab=packages

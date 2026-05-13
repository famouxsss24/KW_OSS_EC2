# KW_OSS_EC2 — Streamlit EC2 배포 실습

> 광운대학교 정보융합학부 2학년 유명현 (2023204088)
> 오픈소스소프트웨어실습 / 박규동 교수님 / 실습 3

## 개요

AWS Learner Lab의 EC2 환경에 Streamlit 앱을 배포하고, 외부에서 퍼블릭 IP로 접속하여 앱이 정상 동작함을 확인하는 실습입니다.
앱 자체는 중간대체과제에서 만든 **"나는 어떤 무기체계 개발자일까?"** Streamlit 앱을 그대로 사용했습니다.

## 파일 구성

- `app.py` — Streamlit 메인 앱
- `requirements.txt` — Python 패키지 의존성
- `data/` — 배경 이미지 등 정적 리소스 (`users.json`, `stats.json`은 런타임 생성, gitignore)

## EC2 실행 방법

```bash
# 1. 패키지 설치 (Amazon Linux 2023 기준)
sudo dnf install -y python3 python3-pip git

# 2. 저장소 클론
git clone https://github.com/famouxsss24/KW_OSS_EC2.git
cd KW_OSS_EC2

# 3. 의존성 설치
pip3 install -r requirements.txt

# 4. Streamlit 실행 (외부 접속 허용)
streamlit run app.py --server.port 8501 --server.address 0.0.0.0
```

### 보안 그룹 인바운드 규칙

| 유형 | 포트 | 소스 |
|------|------|------|
| SSH | 22 | My IP |
| Custom TCP | 8501 | 0.0.0.0/0 |

브라우저 접속: `http://<EC2_PUBLIC_IP>:8501`

## 데모 영상

(영상 업로드 후 추가 예정)

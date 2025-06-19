# Kubernetes Helm Charts for Multi-Application Deployment

이 프로젝트는 **Kubernetes 환경**에서 여러 애플리케이션(FastAPI, Spring Boot 등)과 모니터링 도구(Datadog, Prometheus, Grafana)를 **Helm 차트 기반**으로 배포하기 위한 설정을 포함합니다.

---

## 📦 디렉터리 구성 설명

### `datadog/`
- `datadog-agent.yaml`:  
  Datadog Agent를 설정하는 Custom Resource Definition 파일입니다.

### `fastAPI/`, `spring/`, `monitoring/`
각 디렉터리는 개별 애플리케이션 또는 서비스의 Helm 차트를 포함하며, 공통적으로 아래 파일을 포함합니다:

- `Chart.yaml`:  
  차트 이름, 버전 등의 메타데이터가 정의되어 있습니다.

- `templates/`:  
  Deployment, Service, Ingress 등 Kubernetes 매니페스트 템플릿이 정의됩니다.

- `values.yaml`:  
  이미지 태그, 환경 변수, Ingress 인증서 ARN 등 배포 시 필요한 값이 정의됩니다.

---

## 🚀 배포 예시

```bash
# FastAPI 애플리케이션 배포
helm upgrade --install fastapi ./fastAPI -n fastapi-ns

# Spring Boot 애플리케이션 배포
helm upgrade --install spring ./spring -n spring-ns

# Prometheus & Grafana 배포
helm upgrade --install monitoring ./monitoring -n monitoring-ns

# Datadog Agent 적용
kubectl apply -f datadog/datadog-agent.yaml
````

---

## ✅ 사전 요구 사항

* Kubernetes 클러스터 접근 권한
* Helm 3.x 이상 설치
* 배포 대상 네임스페이스 생성 여부 확인
* (옵션) Datadog API Key 및 Grafana 설정 정보 등

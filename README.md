# Snap-It Kubernetes Manifests

이 저장소는 Snap-It 어플리케이션을 위한 Kubernetes 매니페스트를 포함하고 있습니다.

## 구조

```
snap-it-manifests/
└── snap-it-chart/   # Helm 차트
    ├── Chart.yaml
    ├── values.yaml
    └── templates/    # 쿠버네티스 매니페스트 템플릿
        ├── deployment.yaml
        ├── service.yaml
        ├── namespace.yaml
        └── ...
```

## 사용 방법

### 수동 배포

```bash
cd snap-it-manifests/snap-it-chart
helm install snap-it . -n snapit --create-namespace
```

### CI/CD 파이프라인

이 저장소는 CI/CD 파이프라인에 의해 자동으로 업데이트됩니다. 새로운 이미지 태그가 빌드될 때 values.yaml 파일의 이미지 태그가 업데이트됩니다.

## 네임스페이스

애플리케이션은 `snapit` 네임스페이스에 배포됩니다.

## 서비스 접근

NodePort 서비스 (포트: 32766)를 통해 외부에서 애플리케이션에 접근할 수 있습니다. 
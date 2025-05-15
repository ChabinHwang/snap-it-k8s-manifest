# Snap-It Kubernetes Manifests

이 저장소는 Snap-It 서버 어플리케이션을 위한 Kubernetes 매니페스트를 포함하고 있습니다.

## 구조

```
snap-it-k8s-manifest/
├── Chart.yaml         # Helm 차트 메타데이터
├── values.yaml        # 애플리케이션 설정값
├── argocd-application.yaml # ArgoCD 애플리케이션 정의
└── templates/         # 쿠버네티스 매니페스트 템플릿
    ├── NOTES.txt      # Helm 설치 후 출력되는 노트
    ├── deployment.yaml # 배포 템플릿
    └── service.yaml   # 서비스 템플릿
```

## 구성 요소

- **Chart.yaml**: Helm 차트 버전과 애플리케이션 버전 정보
- **values.yaml**: 컨테이너 이미지, 서비스 설정, 리소스 제한 등 구성 값
- **templates/**: Kubernetes 리소스를 정의하는 템플릿 파일들
- **argocd-application.yaml**: ArgoCD를 통한 GitOps 배포를 위한 Application 정의

## 사용 방법

### 수동 배포

```bash
helm install snap-it . -n snapit --create-namespace
```

### ArgoCD를 통한 배포

이 저장소는 ArgoCD를 통해 지속적으로 배포됩니다. `argocd-application.yaml` 파일에 정의된 설정에 따라 자동으로 동기화됩니다.

## 네임스페이스

애플리케이션은 `snapit` 네임스페이스에 배포됩니다.

## 서비스 접근

NodePort 서비스 (포트: 32766)를 통해 외부에서 애플리케이션에 접근할 수 있습니다.

## 이미지 업데이트

새로운 이미지가 빌드되면 `values.yaml` 파일의 `image.tag` 값이 업데이트됩니다. 
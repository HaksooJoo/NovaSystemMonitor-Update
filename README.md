# NovaSystemMonitor 업데이트 배포 저장소

이 저장소는 **NovaSystemMonitor** Windows x64 프로그램의 공개 업데이트 파일만 제공합니다. 프로그램 소스는 비공개 저장소 [`HaksooJoo/NovaSystemMonitor`](https://github.com/HaksooJoo/NovaSystemMonitor)에서 관리합니다.

## 자동 업데이트 규칙

- 앱 시작 시와 6시간마다 GitHub `releases/latest` API를 확인합니다.
- 앱은 새 버전이 있을 때 사용자의 승인을 받은 후에만 다운로드/설치합니다.
- Release 태그: `vX.Y.Z` (예: `v0.11.2`).
- 업데이트 자산의 이름: `NovaSystemMonitor_vX.Y.Z_Portable.zip` (예: `NovaSystemMonitor_v0.11.2_Portable.zip`).
- 선택 자산은 공개 Release의 `digest`에 포함된 `sha256:<64자리 16진수>` 값으로 무결성을 검증합니다. 누락된 digest, 불일치 파일, 잘못된 URL, 이전 버전은 설치되지 않습니다.
- 설치형 EXE는 선택적 사용자 다운로드용입니다: `NovaSystemMonitor_vX.Y.Z_Setup.exe`.
- 업데이트 ZIP은 파일이 **압축 파일 루트**에 놓인 실행 가능한 self-contained Windows x64 포터블 앱 패키지여야 합니다.
- 최신 버전은 정식 공개 Release에만 배포하며 `draft`, `prerelease`는 자동 업데이트 대상이 아닙니다.

## 배포 방법

비공개 소스 저장소의 GitHub Actions `Publish verified NovaSystemMonitor update` 워크플로를 수동 실행하면, 테스트와 패키지 검증 후 이 저장소에 Release를 게시합니다. 실행 전 소스 저장소의 Actions Secret `NOVA_UPDATE_RELEASE_TOKEN`에는 **이 업데이트 저장소 1개만** 대상으로 `Contents: Read and write` 권한을 부여해야 합니다.

**중요:** 이 저장소에 아직 Release가 없으면 업데이트 확인 결과는 '배포된 새 버전 없음'입니다. 파일을 Git 커밋으로만 올려도 자동 업데이트는 시작되지 않습니다.

## 보안

공개 Release는 인증 없는 다운로드를 지원합니다. 프로그램 사용자에게 GitHub 개인 액세스 토큰을 배포하거나 요구하지 않습니다. SHA-256은 배포 자산의 손상/변조를 감지하지만, 배포자의 서명 및 신뢰를 대신하지는 않습니다. 공식 계정 및 Release 게시 권한을 안전하게 관리하세요.

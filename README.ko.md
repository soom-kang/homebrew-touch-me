![touch me for ZEUSLAP](docs/assets/touch-me-title.png)

[English](README.md) · [한국어](README.ko.md) · [Source](https://github.com/soom-kang/touch-me)

# Touch Me Homebrew Tap

Touch Me는 Mac에서 ZEUSLAP 터치 모니터의 입력을 제대로 활용하도록 돕는 메뉴 막대 앱입니다. 이 저장소는 Touch Me beta를 Homebrew로 설치하고 업데이트할 수 있도록 제공하는 개인 Tap으로, 배포 버전·다운로드 주소·파일 검증 정보를 관리합니다.

현재 beta는 Apple Silicon Mac과 macOS 26(Tahoe) 이상을 대상으로 하며, P16KT에서 확인한 USB/HID profile이 필요합니다. 다른 ZEUSLAP 모델의 호환성은 확인되지 않았습니다. 기본 언어는 영어이며 설정에서 한국어로 바꿀 수 있습니다.

Beta.6은 beta.5에서 도입한 복구 정책을 유지하며 장치 모드를 바꾸기 전에 원래 값을 별도로 기록합니다. 비정상 종료 후 복구는 같은 부팅 세션에서 계속 연결된 동일 장치와 안전하게 확인한 이전 owner가 필요합니다. 연결 identity가 바뀌거나 기록이 잘못되면 값을 추측해 쓰지 않고 매핑을 차단합니다.

Beta.6은 QA 완료 기록을 포함한 재배포이며 동작 변경은 없습니다. 실기기 PASS는 beta.5/build 23의 결과입니다. Beta.6 설치·Gatekeeper·GUI·실기기 사용·업그레이드 검사는 `NOT_RUN`이며 검증 Mac에 설치된 앱은 그대로 유지합니다.

드래그 시작 전에 두 번째 손가락이 감지되면 대기 중인 클릭을 취소합니다. 한 손가락 탭은 손을 뗄 때 클릭하며, 화면 좌표 8단위를 초과해 이동하면 드래그를 시작합니다. 진행 중인 드래그는 처음 손가락을 따라갑니다. 제스처를 바꾸거나 스크롤 뒤 다시 시작하려면 손가락을 모두 떼세요. 변경 사항과 검증 한계는 [release notes](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.6)를 확인하세요.

## 설치

`/Applications/Touch Me.app`을 수동으로 설치했다면 **로그인 시작**을 끄고 **매핑 중지**를 선택하세요. 장치 모드 복구를 확인한 뒤 정상 **종료**합니다. 기존 앱을 Applications 밖에 보존한 다음 설치를 진행하세요. 저장한 환경설정은 유지하고 강제로 덮어쓰지 않습니다.

```bash
brew install --cask soom-kang/touch-me/touch-me
```

`0.8.0-beta.6`은 Developer ID 서명과 Apple 공증 없이 ad hoc 서명을 사용합니다. 첫 실행 전에 [release source와 checksum](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.6)을 확인하세요. macOS가 실행을 차단할 수 있습니다. 승인 경로가 제공되면 **시스템 설정 → 개인정보 보호 및 보안 → 확인 없이 열기**에서 [Apple의 수동 승인 절차](https://support.apple.com/en-us/102445)를 따릅니다. 손상·악성 소프트웨어 경고나 관리 정책이 있다면 원인을 확인해야 합니다. 승인과 실행을 보장하지 않습니다.

시스템 설정에서 **입력 모니터링**과 **손쉬운 사용**을 허용한 뒤 앱을 새로 고침하세요. 업데이트 후에는 재승인이 필요할 수 있으므로 매핑 전에 두 권한을 확인합니다. Cask는 권한을 부여하거나 quarantine을 해제하지 않습니다.

## 업데이트·제거

두 작업 모두 **매핑 중지**, 장치 모드 복구 확인, 정상 **종료** 순서로 준비합니다. 복구가 실패하면 작업을 중단하고 현재 연결을 유지한 채 **복구 재시도**를 누르세요. 같은 USB 포트에 다시 연결해도 바뀐 연결 identity의 복구를 허용하지 않습니다. 현재 프로세스의 복구 완료를 확인하기 전에는 진행하지 않습니다.

```bash
brew update
brew upgrade --cask soom-kang/touch-me/touch-me
```

제거할 때는 **로그인 시작**을 먼저 끄고 같은 중지·종료 절차를 완료한 뒤 실행합니다.

```bash
brew uninstall --cask soom-kang/touch-me/touch-me
```

제거 후에도 저장한 환경설정은 유지됩니다. 자동 실행, process 종료, 권한 변경 hooks와 `zap`은 제공하지 않습니다.

## Tap 관리

Beta 버전은 수동으로 갱신합니다. Cask의 버전, 버전별 release URL과 SHA-256을 함께 관리하세요. `audit_exceptions/github_prerelease_allowlist.json`에는 배포하려는 정확한 beta 버전을 기록합니다. 해당 prerelease만 허용하고 다른 일반 audit 검사는 유지합니다.

게시와 audit은 [release runbook](https://github.com/soom-kang/touch-me/blob/main/docs/Homebrew.ko.md)을 따릅니다. Audit 결과는 설치, Gatekeeper 승인, GUI 동작, 실기기 매핑이나 로그인 실행의 근거가 되지 않습니다. 사용법과 지원 범위는 [앱 안내](https://github.com/soom-kang/touch-me/blob/main/README.ko.md)를 확인하세요.

[MIT License](LICENSE), copyright 2026 Soom Kang.

![touch me for ZEUSLAP](docs/assets/touch-me-title.png)

[English](README.md) · [한국어](README.ko.md) · [Source](https://github.com/soom-kang/touch-me)

# Touch Me Homebrew Tap

Touch Me는 Mac에서 ZEUSLAP 터치 모니터의 입력을 제대로 활용하도록 돕는 메뉴 막대 앱입니다. 이 저장소는 Touch Me beta를 Homebrew로 설치하고 업데이트할 수 있도록 제공하는 개인 Tap으로, 배포 버전·다운로드 주소·파일 검증 정보를 관리합니다.

현재 beta는 Apple Silicon Mac과 macOS 26(Tahoe) 이상을 대상으로 하며, P16KT에서 확인한 USB/HID profile이 필요합니다. 다른 ZEUSLAP 모델의 호환성은 확인되지 않았습니다. 기본 언어는 영어이며 설정에서 한국어로 바꿀 수 있습니다.

Beta.7은 앱을 계속 실행한 상태에서 USB-C 재연결을 처리합니다. 새 연결의 현재 값이 `(0,0)`이고 저장한 USB location과 화면이 일치하면 권한·장치·화면 안전 검사를 거쳐 매핑을 자동으로 재개합니다. 현재 값이 `(2,0)`이면 안내를 확인한 뒤 직접 **매핑 시작**을 눌러야 하며 **매핑 중지** 후에도 그 값을 유지합니다.

이전 기록은 같은 boot에서 기록된 HID/USB service가 모두 종료됐고 소유권이 확인된 경우에만 archive로 보존합니다. Archive는 원래 모드 복구를 확인한 결과가 아니며 그 값을 새 연결에 쓰도록 허용하지 않습니다. 불확실한 기록은 매핑을 차단하므로 보존한 채 **복구 재시도**를 사용하세요.

이 Tap은 검증한 beta.7/build 25 release를 배포합니다. 공개 DMG와 checksum sidecar가 확정한 산출물과 일치하며 Cask Ruby syntax와 Homebrew style도 통과했습니다. 선택 Cask trust가 없고 사용자가 현재 trust를 유지하기로 결정해 일반 online audit은 `BLOCKED`입니다. Audit 검사는 우회하지 않았습니다.

로컬 재연결 후보는 사용자 확인으로 한 차례 재연결을 통과했습니다. 최종 beta.7 설치·Gatekeeper·GUI·실기기 사용·Homebrew upgrade 검사는 `NOT_RUN`입니다. 이전 beta.5/build 23 실기기 acceptance와 beta.6 release 기록은 과거 근거로 보존합니다.

드래그 시작 전에 두 번째 손가락이 감지되면 대기 중인 클릭을 취소합니다. 한 손가락 탭은 손을 뗄 때 클릭하며, 화면 좌표 8단위를 초과해 이동하면 드래그를 시작합니다. 진행 중인 드래그는 처음 손가락을 따라갑니다. 제스처를 바꾸거나 스크롤 뒤 다시 시작하려면 손가락을 모두 떼세요. 변경 사항과 검증 한계는 [release notes](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.7)를 확인하세요.

## 설치

`/Applications/Touch Me.app`을 수동으로 설치했다면 **로그인 시작**을 끄고 **매핑 중지**를 선택하세요. 대기 중인 복구나 기록 처리를 완료한 뒤 정상 **종료**합니다. 기존 앱을 Applications 밖에 보존한 다음 설치를 진행하세요. 저장한 환경설정과 recovery record는 유지하고 강제로 덮어쓰지 않습니다.

```bash
brew install --cask soom-kang/touch-me/touch-me
```

`0.8.0-beta.7`은 Developer ID 서명과 Apple 공증 없이 ad hoc 서명을 사용합니다. 첫 실행 전에 [release source와 checksum](https://github.com/soom-kang/touch-me/releases/tag/v0.8.0-beta.7)을 확인하세요. macOS가 실행을 차단할 수 있습니다. 승인 경로가 제공되면 **시스템 설정 → 개인정보 보호 및 보안 → 확인 없이 열기**에서 [Apple의 수동 승인 절차](https://support.apple.com/en-us/102445)를 따릅니다. 손상·악성 소프트웨어 경고나 관리 정책이 있다면 원인을 확인해야 합니다. 승인과 실행을 보장하지 않습니다.

시스템 설정에서 **입력 모니터링**과 **손쉬운 사용**을 허용한 뒤 앱을 새로 고침하세요. 업데이트 후에는 재승인이 필요할 수 있으므로 매핑 전에 두 권한을 확인합니다. Cask는 권한을 부여하거나 quarantine을 해제하지 않습니다.

## 업데이트·제거

두 작업 모두 **매핑 중지**, 대기 중인 복구나 기록 처리 완료, 정상 **종료** 순서로 준비합니다. 복구나 기록 처리가 실패하면 작업을 중단하고 **복구 재시도**를 누르세요. Recovery record는 보존하며 업그레이드나 제거를 진행하기 위해 삭제하지 않습니다. 같은 USB 포트에 다시 연결해도 이전 모드를 새 연결에 쓰도록 허용하지 않습니다.

```bash
brew update
brew upgrade --cask soom-kang/touch-me/touch-me
```

제거할 때는 **로그인 시작**을 먼저 끄고 같은 중지·종료 절차를 완료한 뒤 실행합니다.

```bash
brew uninstall --cask soom-kang/touch-me/touch-me
```

제거 후에도 저장한 환경설정과 recovery record는 유지됩니다. 자동 실행, process 종료, 권한 변경 hooks와 `zap`은 제공하지 않습니다.

## Tap 관리

Beta 버전은 수동으로 갱신합니다. Cask의 버전, 버전별 release URL과 SHA-256을 함께 관리하세요. `audit_exceptions/github_prerelease_allowlist.json`에는 배포하려는 정확한 beta 버전을 기록합니다. 해당 prerelease만 허용하고 다른 일반 audit 검사는 유지합니다.

게시와 audit은 [release runbook](https://github.com/soom-kang/touch-me/blob/main/docs/Homebrew.ko.md)을 따릅니다. Audit 결과는 설치, Gatekeeper 승인, GUI 동작, 실기기 매핑이나 로그인 실행의 근거가 되지 않습니다. 사용법과 지원 범위는 [앱 안내](https://github.com/soom-kang/touch-me/blob/main/README.ko.md)를 확인하세요.

[MIT License](LICENSE), copyright 2026 Soom Kang.

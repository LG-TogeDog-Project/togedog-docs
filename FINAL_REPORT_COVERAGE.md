# 최종 산출문서 공개 반영표

본 문서는 2026년 6월 25일 작성된 77페이지 최종 산출문서와 TogeDog 공개 저장소의 대응 관계를 정리합니다. 오거나이제이션 프로필은 전체 프로젝트를 설명하고, 이 저장소는 상세 설계와 실제 구현 문서로 연결합니다.

## 문서 영역별 공개 위치

| 최종 산출문서 | 핵심 내용 | 공개 위치 |
|---|---|---|
| 1–4쪽 | 표지, 프로젝트 소개, 목차, WBS | 오거나이제이션 프로필 `1. 프로젝트 개요` |
| 5–7쪽 | 시장 배경, LG 현황, 장애인·반려견 연결성, SWOT, 고객 정의 | 오거나이제이션 프로필 `2–4` |
| 8–11쪽 | 데이터 수집·전처리, Sentence-BERT, BERTopic | 오거나이제이션 프로필 `5` |
| 12–16쪽 | 대표 페르소나, Actor, 기회영역 | 오거나이제이션 프로필 `6` |
| 17–22쪽 | Actor별 CAM과 대표 Action | 오거나이제이션 프로필 `6.3–6.4` |
| 23–26쪽 | 관찰–고찰–통찰, 4D-CX, 서비스 정의, 비즈니스 캔버스 | 오거나이제이션 프로필 `7` |
| 27–35쪽 | 요구사항 개요, 유스케이스 다이어그램, CARE_001–008 | 오거나이제이션 프로필 `8–9` |
| 36–42쪽 | 기능 요구사항 ID·우선순위 | 오거나이제이션 프로필 `10`, 각 앱 README와 실제 코드 |
| 43–44쪽 | 외부 API·라이브러리 연동 | 각 코드 저장소 `pubspec.yaml`, `requirements.txt`, README |
| 45–47쪽 | 기획 단계 내부 API 계약 | 오거나이제이션 프로필 `11` |
| 48–55쪽 | 메뉴 구조, 서비스 흐름, 화면설계서 | 오거나이제이션 프로필 `12`, `togedog-mobile` 소스·assets |
| 56–57쪽 | 시스템 아키텍처 | [`ARCHITECTURE.md`](./ARCHITECTURE.md) |
| 58쪽 | Object Definition, ERD | [`reference/DB_설계서.md`](./reference/DB_%EC%84%A4%EA%B3%84%EC%84%9C.md) |
| 59–72쪽 | 데이터셋, 전처리, YOLO 학습·평가 | `togedog-ai` 노트북·결과 파일과 오거나이제이션 프로필 `15` |
| 73–75쪽 | Inventor 하드웨어 프로토타입 | 오거나이제이션 프로필 `16` |
| 76쪽 | DX·CX·BX·ESG Performance Tracker | 오거나이제이션 프로필 `18` |
| 77쪽 | 참고문헌 | 오거나이제이션 프로필 `23` |

## 기획 계약과 실제 구현의 구분

최종 산출문서의 API 표는 ThinQ/Firebase 인증과 JWT Bearer Token을 전제로 한 목표 계약입니다. 현재 공개 백엔드는 프로토타입 검증을 위해 개발용 `X-Member-Id` 헤더를 사용합니다.

| 구분 | 기획·목표 구조 | 공개 프로토타입 |
|---|---|---|
| 인증 | ThinQ/Firebase Auth, JWT Bearer Token | 개발용 `X-Member-Id` 헤더 |
| 사용자 초기화 | `/api/auth/thinq/init` | `POST /members` |
| 반려견 | `/api/profile/pet` | `/dogs` |
| 기기 | `/api/device/*` | `/devices` |
| 위험 이벤트 | `/api/events/ai-vision-alert` | `/danger-detections` |
| 리포트 | `/api/reports/*` | `/reports/*` |

실제 요청·응답 스키마는 [`reference/API_명세서.md`](./reference/API_%EB%AA%85%EC%84%B8%EC%84%9C.md)를 기준으로 합니다.

## 구현 경계

| 기능 | 공개 상태 |
|---|---|
| 보호자용 Flutter 화면과 접근성 UX | 구현 |
| 카메라 P2P 영상 송수신 | 프로토타입 구현 |
| YOLO 12종 객체 탐지 학습·평가 | 구현 |
| TFLite 앱 연결 | 코드 구현, 모델 파일 별도 필요 |
| YAMNet 환경음 분석 | 연결 실험·향후 확장 |
| FastAPI REST·WebSocket | 구현 |
| Firebase 데이터 저장 | 선택적 구현 |
| Firebase Auth·ThinQ 공식 연동 | 향후 확장 |
| 심박수·활동량 실물 센서 | 데이터 구조·콘셉트 |
| 상용 웨어러블 | 3D·하드웨어 프로토타입 |

## 공개본에서 제외하는 자료

### 보안상 제외

- 실제 `.env`, API 키, 비밀번호, 토큰
- Firebase 서비스 계정과 플랫폼 설정 파일
- Android/iOS 인증서와 서명 키

### 개인정보·저작권·라이선스상 제외

- 사용자 식별정보가 포함된 VOC 원문과 크롤링 원본
- 플랫폼 약관 또는 데이터셋 라이선스상 재배포가 불명확한 학습 원본
- 배포 권한 확인 전 모델 가중치
- 내부 작업공간 WBS 링크

### 저장소 위생상 제외

- 빌드 결과, 캐시, IDE 임시 파일

## 모델 재현 안내

학습 과정은 `togedog-ai/notebooks/train_yolo_v3.ipynb`에 공개되어 있습니다. 모델 가중치는 배포 라이선스 확인 후 GitHub Release 또는 모델 레지스트리에 체크섬·라이선스와 함께 제공하는 것을 원칙으로 합니다. 현재 앱이 참조하는 주요 경로는 다음과 같습니다.

```text
togedog-mobile/assets/deep_learning/best_v3_float16.tflite
togedog-mobile/assets/deep_learning/yamnet.tflite
```

첫 번째 파일은 객체 탐지용이며, 두 번째 파일은 환경음 분석 확장 실험용입니다.

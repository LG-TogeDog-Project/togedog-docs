# Repository Map

| 저장소 | 주요 기술 | 대표 진입점 |
|---|---|---|
| `togedog-mobile` | Flutter, TFLite, TTS, Vibration, WebRTC | `lib/main.dart` |
| `togedog-camera` | Flutter, Camera, WebRTC, YOLO stream | `lib/main.dart` |
| `togedog-backend` | FastAPI, Pydantic, Firebase, WebSocket | `app/main.py` |
| `togedog-ai` | Colab, Ultralytics YOLO, Roboflow | `notebooks/train_yolo_v3.ipynb` |
| `togedog-docs` | Markdown, Mermaid | `README.md` |

## 공개 저장소 제외 항목

- 환경변수 실값과 API 키
- Firebase 서비스 계정 및 플랫폼 설정 파일
- Android/iOS 서명 키
- 개인정보·원문 재배포 문제가 있는 VOC 원본
- 재배포 라이선스 확인이 필요한 학습 원본 데이터셋
- 라이선스·배포 경로 확인이 필요한 모델 가중치 (`*.pt`, `*.tflite`, `*.onnx` 등)
- 빌드 결과와 캐시

모델 파일은 보안 비밀정보가 아니지만 현재 공개 저장소만으로는 라이선스와 용량을 안전하게 관리하기 어려워 제외했습니다. 배포 승인을 마치면 GitHub Release 또는 별도 모델 레지스트리에서 체크섬과 라이선스를 함께 제공합니다.

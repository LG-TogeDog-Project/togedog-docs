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
- 학습 원본 데이터셋
- 대용량 모델 가중치 (`*.pt`, `*.tflite`, `*.onnx` 등)
- 빌드 결과와 캐시

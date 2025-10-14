Vị trí **Product Engineer (Mid-Level)** tại **Starley** yêu cầu kỹ năng khá rộng: backend mạnh, hiểu hệ thống real-time (WebRTC/WebSocket), có exposure với AI/ML và tư duy sản phẩm.
- https://japan-dev.com/jobs/starley/starley-software-engineer---backend-ekvm6j
---

## 🎯 Mục tiêu cuối cùng (sau 3 tháng)

Bạn có thể:

1. **Giải thích & code được backend system** (Python/FastAPI hoặc Rust/Node) có real-time communication (WebSocket).
2. **Hiểu cách tích hợp AI model vào hệ thống backend** (gọi inference API, streaming voice).
3. **Tự tin phỏng vấn bằng tiếng Nhật và tiếng Anh**, có thể mô tả design, xử lý scaling và CI/CD.
4. **Demo được 1 mini product** tương tự Cotomo (voice chat bot nhỏ).

---

## 🗓 Kế hoạch chi tiết 3 tháng

### **Tháng 1: Backend System + Realtime Foundation**

**Mục tiêu:** Nắm vững thiết kế hệ thống backend, hiểu real-time communication, database và cloud.

#### 🔹 Kiến thức kỹ thuật

* **Python (hoặc Node.js):**

  * Làm quen framework: `FastAPI` hoặc `NestJS`
  * Hiểu lifecycle request → response, middleware, async I/O.
* **WebSocket & WebRTC:**

  * Làm demo real-time chat: FastAPI + WebSocket.
  * Học cơ chế signaling, STUN/TURN trong WebRTC.
  * Đọc doc: [MDN WebRTC Guide](https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API)
* **Database:**

  * PostgreSQL: schema design, index, transaction, performance tuning cơ bản.
  * Redis cache (basic).
* **Cloud:**

  * Deploy 1 project nhỏ lên **GCP** hoặc **AWS EC2 + RDS**.
* **CI/CD:**

  * Dùng **GitHub Actions** build → test → deploy.

#### 🔹 Output

* Mini project: “Real-time chat app” với user login + message streaming.
* Code clean + deploy thật (AWS/GCP).

---

### **Tháng 2: AI Integration + Scalable Design**

**Mục tiêu:** Hiểu cách tích hợp AI model (speech recognition, synthesis, NLP), xử lý streaming data.

#### 🔹 Kiến thức kỹ thuật

* **Speech Recognition / TTS:**

  * Dùng API như **Whisper (OpenAI)** hoặc **Vosk**, **gTTS**, **Coqui TTS**.
  * Hiểu pipeline: Mic → Stream → ASR → LLM → TTS → Audio.
* **LLM/NLP integration:**

  * Gọi API từ **OpenAI**, **HuggingFace**.
  * Hiểu cơ bản về RAG (retrieval-augmented generation).
* **Streaming:**

  * Làm API stream response theo thời gian thực.
  * Dùng WebSocket hoặc Server-Sent Events (SSE).
* **Architecture:**

  * Học design pattern backend: microservice, pub/sub, queue (Pub/Sub, Kafka).
  * Tìm hiểu về **ElasticSearch** & use-case.

#### 🔹 Output

* Mini project: “Voice assistant” (nghe → hiểu → nói).

  * Backend FastAPI stream audio.
  * Gọi Whisper + GPT + TTS.
  * Kết nối WebSocket để truyền audio real-time.

---

### **Tháng 3: Product Thinking + Interview Prep**

**Mục tiêu:** Chuẩn bị cho phỏng vấn thật — coding, system design, product sense, communication (JP/EN).

#### 🔹 Kỹ thuật

* Ôn **system design**:

  * High traffic design (cache, load balancer, stateless).
  * Scaling real-time systems.
  * Logging, monitoring (Sentry).
* Học về **DevOps cơ bản**: Docker, k8s (concept thôi), logging/monitoring.
* Hiểu **Unity integration** (nếu có thời gian, xem cách gọi voice API từ game engine).

#### 🔹 Phỏng vấn (Tech + Product + Communication)

* **Technical Interview:**

  * Data modeling, API design, concurrency, scaling.
  * Câu hỏi thực tế: “How would you build a scalable voice chat app?”
* **Product Interview:**

  * “How would you improve Cotomo’s UX?”
  * “Which metrics would you track?”
* **Behavioral + Communication:**

  * Trả lời bằng tiếng Nhật tự nhiên (準備OK? / 工夫したことは？ / 失敗した経験は？)
  * Practice bằng tiếng Anh: explain architecture clearly.

#### 🔹 Output

* Build portfolio:

  * GitHub repo + README + demo link.
  * Slide tóm tắt “Voice AI Assistant System”.
* Mock interview mỗi tuần:

  * 1 technical (English)
  * 1 behavioral (Japanese)

---

## 📘 Tài nguyên gợi ý

| Chủ đề                           | Nguồn                                                                                             |
| -------------------------------- | ------------------------------------------------------------------------------------------------- |
| **FastAPI**                      | [fastapi.tiangolo.com](https://fastapi.tiangolo.com/)                                             |
| **WebRTC Basics**                | [MDN WebRTC Guide](https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API)                   |
| **Speech AI**                    | [OpenAI Whisper](https://github.com/openai/whisper), [Coqui TTS](https://github.com/coqui-ai/TTS) |
| **System Design**                | “System Design Primer” on GitHub                                                                  |
| **Japanese Tech Interview Prep** | Qiita記事検索: “バックエンド エンジニア 面接 質問”                                                                   |
| **Product Sense**                | [PM Exercises](https://www.productmanagementexercises.com/)                                       |

---

## 📅 Lịch học mẫu hằng tuần

| Tuần  | Mục tiêu                         | Output           |
| ----- | -------------------------------- | ---------------- |
| 1–2   | FastAPI + PostgreSQL + WebSocket | Chat app         |
| 3–4   | WebRTC + Cloud deploy            | Streaming chat   |
| 5–6   | Whisper + TTS integration        | Voice bot MVP    |
| 7–8   | Optimize, add logging + CI/CD    | Stable version   |
| 9–10  | System design + Product UX       | Architecture doc |
| 11–12 | Mock interviews (JP/EN)          | Portfolio ready  |

---

Nếu bạn muốn, mình có thể giúp bạn tạo **bảng kế hoạch học tập chi tiết theo ngày (90 ngày)**, bao gồm:

* tài liệu học mỗi ngày,
* milestone kiểm tra,
* câu hỏi phỏng vấn mẫu (JP/EN).

👉 Bạn có muốn mình tạo bản kế hoạch chi tiết theo ngày không (định dạng Notion hoặc bảng markdown)?

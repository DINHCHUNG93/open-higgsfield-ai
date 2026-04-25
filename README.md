🎉 Open Generative AI – Studio AI tạo ảnh/video mã nguồn mở thay thế Higgsfield không giới hạn nội dung và luôn update các models mới nhất như HappyHorse, GPT-image 2

Đây là dự án open-source giúp tạo ảnh, video, lip sync và cinematic shots từ hơn 200+ models AI như Flux, Midjourney, Kling, Sora, Veo, Seedance… trong một giao diện duy nhất. Repo hiện hơn 5k stars trên GitHub.  ￼

Tính năng nổi bật

* Image Studio: text-to-image + image-to-image
* Video Studio: text-to-video + image-to-video
* Lip Sync Studio: đồng bộ môi, talking avatar
* Cinema Studio: chỉnh lens, focal length, camera style
* Multi-image input: hỗ trợ tới 14 ảnh tham chiếu
* Self-host + desktop app + MIT license  ￼

Điểm đáng chú ý

Khác với Higgsfield hay Freepik bị khóa hệ sinh thái, dự án này cho phép:

→ self-host
→ BYOK (bring your own key)
→ chỉnh sửa UI
→ không bị vendor lock-in

Tuy nhiên phần backend mạnh vẫn chủ yếu chạy qua MuAPI nên thực tế không hoàn toàn “free”, mà giống một frontend mạnh cho nhiều model AI hơn.  ￼

#AI #OpenSource #GenerativeAI


# Open Higgsfield AI — Open-Source Alternative to Higgsfield AI

> **The free, open-source alternative to Higgsfield AI.** Generate AI images and videos using 200+ state-of-the-art models — without the closed ecosystem or subscription fees.

Open Higgsfield AI is an open-source AI image, video, and cinema studio that brings Higgsfield-style creative workflows to everyone. Powered by [Muapi.ai](https://muapi.ai), it supports text-to-image, image-to-image, text-to-video, and image-to-video generation across models like Flux, Nano Banana, Midjourney, Kling, Sora, Veo, and more — all from a sleek, modern interface you can self-host and customize.

**Why Open Higgsfield AI instead of Higgsfield AI?**
- **Free & open-source** — no subscription, no vendor lock-in
- **Self-hosted** — your data stays on your machine
- **200+ models** — text-to-image, image-to-image, text-to-video, image-to-video
- **Extensible** — add your own models, modify the UI, build on top of it

For a deep dive into the technical architecture and the philosophy behind the "Infinite Budget" cinema workflow, see our [comprehensive guide and roadmap](https://medium.com/@anilmatcha/building-open-higgsfield-ai-an-open-source-ai-cinema-studio-83c1e0a2a5f1).

![Studio Demo](docs/assets/studio_demo.webp)

## ✨ Features

- **Image Studio** — Generate images from text prompts (50+ text-to-image models) or transform existing images (55+ image-to-image models). Switches model set automatically based on whether a reference image is provided.
- **Video Studio** — Generate videos from text prompts (40+ text-to-video models) or animate a start-frame image (60+ image-to-video models). Same intelligent mode switching as Image Studio.
- **Cinema Studio** — Higgsfield AI-style interface for photorealistic cinematic shots with pro camera controls (Lens, Focal Length, Aperture)
- **Upload History** — Reference images are uploaded once and stored locally. A picker panel lets you reuse any previously uploaded image across sessions — no re-uploading.
- **Smart Controls** — Dynamic aspect ratio, resolution, and duration pickers that adapt to each model's capabilities
- **Generation History** — Browse, revisit, and download all past generations (persisted in browser storage)
- **Image & Video Download** — One-click download of generated outputs in full resolution
- **API Key Management** — Secure API key storage in browser localStorage (never sent to any server except Muapi)
- **Responsive Design** — Works seamlessly on desktop and mobile with dark glassmorphism UI

### 🖼️ Image Studio — Dual Mode

The Image Studio automatically switches between two model sets:

| Mode | Trigger | Models | Prompt |
| :--- | :--- | :--- | :--- |
| **Text-to-Image** | Default (no image) | 50+ t2i models (Flux, Nano Banana, Ideogram, GPT-4o, Midjourney…) | Required |
| **Image-to-Image** | Reference image uploaded | 55+ i2i models (Kontext, Seededit, Nano Banana Edit, Upscaler, Background Remover…) | Optional |

### 🎬 Video Studio — Dual Mode

The Video Studio follows the same pattern:

| Mode | Trigger | Models | Prompt |
| :--- | :--- | :--- | :--- |
| **Text-to-Video** | Default (no image) | 40+ t2v models (Kling, Sora, Veo, Wan, Seedance, Hailuo, Runway…) | Required |
| **Image-to-Video** | Start frame uploaded | 60+ i2v models (Kling I2V, Veo3 I2V, Runway I2V, Wan I2V, Midjourney I2V…) | Optional |

### 🎥 Cinema Studio Controls

The **Cinema Studio** offers precise control over the virtual camera, translating your choices into optimized prompt modifiers:

| Category | Available Options |
| :--- | :--- |
| **Cameras** | Modular 8K Digital, Full-Frame Cine Digital, Grand Format 70mm Film, Studio Digital S35, Classic 16mm Film, Premium Large Format Digital |
| **Lenses** | Creative Tilt, Compact Anamorphic, Extreme Macro, 70s Cinema Prime, Classic Anamorphic, Premium Modern Prime, Warm Cinema Prime, Swirl Bokeh Portrait, Vintage Prime, Halation Diffusion, Clinical Sharp Prime |
| **Focal Lengths** | 8mm (Ultra-Wide), 14mm, 24mm, 35mm (Human Eye), 50mm (Portrait), 85mm (Tight Portrait) |
| **Apertures** | f/1.4 (Shallow DoF), f/4 (Balanced), f/11 (Deep Focus) |

### 📁 Upload History & Picker

Every image you upload is saved locally (URL + thumbnail) so you never upload the same file twice:

- Click the upload button to open the **reference image picker**
- Previously uploaded images appear in a 3-column grid with thumbnails
- Click any thumbnail to instantly reuse it — no API call needed
- Upload a new image with the "Upload new" button in the panel
- Remove individual images from history with the ✕ button
- History persists across browser sessions (stored in `localStorage`)

## 🚀 Quick Start

### Prerequisites

- [Node.js](https://nodejs.org/) (v18+)
- A [Muapi.ai](https://muapi.ai) API key

### Setup

```bash
# Clone the repository
git clone https://github.com/Anil-matcha/Open-Higgsfield-AI.git
cd Open-Higgsfield-AI

# Install dependencies
npm install

# Start the development server
npm run dev
```

Open `http://localhost:5173` in your browser. You'll be prompted to enter your Muapi API key on first use.

### Production Build

```bash
npm run build
npm run preview
```

## 🏗️ Architecture

```
src/
├── components/
│   ├── ImageStudio.js    # Dual-mode t2i/i2i studio with dynamic model switching
│   ├── VideoStudio.js    # Dual-mode t2v/i2v studio with dynamic model switching
│   ├── CinemaStudio.js   # Pro studio with camera controls & infinite canvas flow
│   ├── UploadPicker.js   # Reusable upload button + history panel component
│   ├── CameraControls.js # Scrollable picker for camera/lens/focal/aperture
│   ├── Header.js         # App header with settings and controls
│   ├── AuthModal.js      # API key input modal
│   ├── SettingsModal.js  # Settings panel for API key management
│   └── Sidebar.js        # Navigation sidebar
├── lib/
│   ├── muapi.js          # API client: generateImage, generateVideo, generateI2I, generateI2V, uploadFile
│   ├── models.js         # 200+ model definitions (t2i, t2v, i2i, i2v) with endpoint & input mappings
│   └── uploadHistory.js  # localStorage CRUD + canvas thumbnail generation for upload history
├── styles/
│   ├── global.css        # Global styles and animations
│   ├── studio.css        # Studio-specific styles
│   └── variables.css     # CSS custom properties
├── main.js               # App entry point
└── style.css             # Tailwind imports
```

## 🔌 API Integration

The app communicates with [Muapi.ai](https://muapi.ai) using a two-step pattern:

1. **Submit** — `POST /api/v1/{model-endpoint}` with prompt and parameters
2. **Poll** — `GET /api/v1/predictions/{request_id}/result` until status is `completed`

Authentication uses the `x-api-key` header. During development, a Vite proxy handles CORS by routing `/api` requests to `https://api.muapi.ai`.

File uploads use `POST /api/v1/upload_file` (multipart/form-data) and return a hosted URL that is passed to image-conditioned models.

## 🎨 Supported Model Categories

| Category | Count | Examples |
|---|---|---|
| **Text-to-Image** | 50+ | Flux Dev, Nano Banana Pro, Ideogram v3, Midjourney v7, GPT-4o, SDXL |
| **Image-to-Image** | 55+ | Nano Banana Edit, Flux Kontext Pro, GPT-4o Edit, Seededit v3, Upscaler, Background Remover |
| **Text-to-Video** | 40+ | Kling v3, Sora 2, Veo 3, Wan 2.6, Seedance Pro, Hailuo 2.3, Runway Gen-3 |
| **Image-to-Video** | 60+ | Kling v2.1 I2V, Veo3 I2V, Runway I2V, Midjourney v7 I2V, Hunyuan I2V, Wan2.2 I2V |

## 🛠️ Tech Stack

- **Vite** — Build tool & dev server
- **Tailwind CSS v4** — Utility-first styling
- **Vanilla JS** — No framework, pure DOM manipulation
- **Muapi.ai** — AI model API gateway

## 🤔 How is this different from Higgsfield AI?

Higgsfield AI is a proprietary AI video and image generation platform. **Open Higgsfield AI** is a community-driven, open-source alternative that provides similar creative capabilities without the closed ecosystem:

| | Higgsfield AI | Open Higgsfield AI |
| :--- | :--- | :--- |
| **Cost** | Subscription-based | Free (open-source) |
| **Models** | Proprietary | 200+ open & commercial models |
| **Self-hosting** | No | Yes |
| **Customizable** | No | Fully hackable |
| **Data privacy** | Cloud-based | Your data stays local |
| **Source code** | Closed | MIT licensed |

## 📄 License

MIT

## 🙏 Credits

Built with [Muapi.ai](https://muapi.ai) — the unified API for AI image and video generation models.

---
**Deep Dive**: For more details on the "AI Influencer" engine, upcoming "Popcorn" storyboarding features, and the future of this project, read the [full technical overview](https://medium.com/@anilmatcha/building-open-higgsfield-ai-an-open-source-ai-cinema-studio-83c1e0a2a5f1).

---
*Looking for a free Higgsfield AI alternative? Open Higgsfield AI is an open-source AI image and video generation studio and Higgsfield AI replacement that you can self-host, customize, and extend.*

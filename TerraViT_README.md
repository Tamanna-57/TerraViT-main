# 🌍 TerraViT — AI-Powered Climate Intelligence System

> An end-to-end climate-monitoring platform that uses **Vision Transformers (ViT)** on geospatial satellite imagery to **detect, visualize, and explain** environmental changes over time.

<p align="center">
  <img alt="Python" src="https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white">
  <img alt="FastAPI" src="https://img.shields.io/badge/FastAPI-Backend-009688?logo=fastapi&logoColor=white">
  <img alt="PyTorch" src="https://img.shields.io/badge/PyTorch-ViT-EE4C2C?logo=pytorch&logoColor=white">
  <img alt="Next.js" src="https://img.shields.io/badge/Next.js-Frontend-black?logo=next.js&logoColor=white">
  <img alt="License" src="https://img.shields.io/badge/License-MIT-green">
</p>

---

## 🏆 Recognition

🥉 **Third Position — Project Showcase 2.0, Global AI Summit 2025** for presenting TerraViT as an AI-powered climate intelligence system.

---

## 📖 Overview

Climate change is hard to *see* in raw satellite data. TerraViT turns that data into
clear, explainable insight. A user provides satellite imagery of a region, and the
system uses a **Vision Transformer** to analyze it, detect environmental changes
(such as deforestation, land-use change, and vegetation loss), and — crucially —
**explain *where* the model is looking** using attention maps.

Unlike a black-box classifier, TerraViT pairs every prediction with **attention-based
visual explanations**, making the results interpretable for researchers,
policymakers, and the general public.

---

## ✨ Key Features

- 🛰️ **Satellite Image Analysis** — runs Vision Transformer inference on geospatial imagery.
- 🔍 **Explainable AI** — attention maps highlight the regions driving each prediction.
- 📈 **Temporal Change Detection** — visualizes environmental changes across time.
- ⚡ **Fast Inference API** — FastAPI backend with the model loaded once at startup.
- 🎨 **Interactive Dashboard** — Next.js + Tailwind frontend for predictions and heatmaps.
- 🔗 **Clean REST API** — decoupled backend/frontend for easy extension.

---

## 🏗️ Architecture

```
┌──────────────────────────┐        ┌───────────────────────────┐
│   Next.js Frontend        │  REST  │   FastAPI Backend          │
│  (React + Tailwind CSS)   │ ─────► │  - Input validation        │
│  - Upload imagery         │  JSON  │  - Image preprocessing     │
│  - Visualize predictions  │ ◄───── │  - ViT inference (PyTorch) │
│  - Attention heatmaps     │        │  - Attention extraction    │
└──────────────────────────┘        └─────────────┬─────────────┘
                                                   │
                                          ┌────────▼─────────┐
                                          │  Vision Transformer
                                          │   (PyTorch model) │
                                          └──────────────────┘
```

**Request flow:**
1. User uploads satellite imagery on the Next.js frontend.
2. Frontend sends a `POST` request with the image to the FastAPI backend.
3. Backend validates and preprocesses the image (resize, normalize, tensor conversion).
4. The Vision Transformer (loaded once at startup) runs inference.
5. Attention maps are extracted for explainability.
6. Backend returns predictions + attention data as JSON.
7. Frontend renders the predictions, temporal changes, and attention heatmaps.

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **AI/ML** | PyTorch, Vision Transformer (ViT) |
| **Backend** | FastAPI, Uvicorn, Pillow / OpenCV, NumPy |
| **Frontend** | Next.js, React, Tailwind CSS |
| **Tooling** | Git, GitHub |

---

## 📂 Project Structure

```
TerraViT/
├── backend/
│   ├── main.py              # FastAPI app & API routes
│   ├── model.py             # ViT model loading & inference
│   ├── preprocessing.py     # Image preprocessing utilities
│   ├── attention.py         # Attention-map extraction
│   └── requirements.txt
├── frontend/
│   ├── pages/               # Next.js pages
│   ├── components/          # React components (upload, viewer, heatmap)
│   ├── styles/              # Tailwind CSS
│   └── package.json
├── models/                  # Saved model weights
├── assets/                  # Sample imagery / screenshots
└── README.md
```

> *Note: adjust the structure above to match your actual repo layout.*

---

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- Node.js 18+
- pip & npm

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/TerraViT.git
cd TerraViT
```

### 2. Backend setup
```bash
cd backend
python -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate
pip install -r requirements.txt
uvicorn main:app --reload         # runs on http://localhost:8000
```

### 3. Frontend setup
```bash
cd frontend
npm install
npm run dev                        # runs on http://localhost:3000
```

### 4. Open the app
Visit **http://localhost:3000** and upload a satellite image to see predictions
and attention heatmaps.

---

## 🔌 API Reference

### `POST /predict`
Run environmental-change analysis on a satellite image.

**Request** (`multipart/form-data`)
| Field | Type | Description |
|---|---|---|
| `image` | file | Satellite image to analyze |

**Response** (`application/json`)
```json
{
  "status": "success",
  "predictions": {
    "label": "deforestation",
    "confidence": 0.92
  },
  "attention_map": "<base64 / url to heatmap>",
  "temporal_insights": { "...": "..." }
}
```

> *Update field names to match your actual implementation.*

---

## 🧠 How the Vision Transformer Works (in brief)

A Vision Transformer splits an image into fixed-size **patches**, embeds them, and
uses **self-attention** to learn which patches matter most. TerraViT taps into these
attention weights to produce **heatmaps** — turning the model from a black box into
an explainable tool.

---

## 🗺️ Roadmap / Future Work

- [ ] Dockerize backend + frontend for one-command deployment
- [ ] Add caching for repeated image requests
- [ ] Support batch image analysis
- [ ] Integrate live satellite data feeds
- [ ] Add user authentication & saved reports

---

## 🤝 Contributing

Contributions are welcome! Please open an issue to discuss major changes before
submitting a pull request.

---

## 📜 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 👩‍💻 Author

**Tamanna Arora**
B.Tech CSE (AI/ML), Bennett University
[LinkedIn](https://linkedin.com/in/<your-handle>) · [GitHub](https://github.com/<your-username>)

---

<p align="center"><i>Built to turn satellite data into climate clarity. 🌱</i></p>

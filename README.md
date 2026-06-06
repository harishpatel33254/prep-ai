link to acces the working site --- https://harishpatel33254.github.io/prep-ai/
# 🎯 prep.ai

### AI-powered job-readiness platform for students

**Built for the AI for Employability Hackathon**


[![Live Demo](https://img.shields.io/badge/Live%20Demo-Vercel-black?style=for-the-badge&logo=vercel)](https://prep-ai.vercel.app)
[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react)](https://reactjs.org)
[![Claude API](https://img.shields.io/badge/Powered%20by-Claude%20AI-orange?style=for-the-badge)](https://anthropic.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](LICENSE)

</div>

---

## 🚀 What is prep.ai?

**prep.ai** is a full-stack AI career coach that helps students become job-ready through four intelligent tools — all powered by the Claude API (Anthropic). Instead of spending money on coaching or waiting for feedback from mentors, students get instant, personalized, high-quality career guidance in one place.

> **Hackathon Problem Statement:** Build an AI tool that helps students become job-ready through resume analysis, interview evaluation, skill-gap planning, portfolio review, or job-posting trust checks.

---

## ✨ Features

### 🎤 AI Interview Practice
- Choose from 6 job roles: Software Engineer, Data Scientist, Product Manager, Marketing Analyst, Finance Analyst, UI/UX Designer
- 5 role-specific questions per session — Behavioral, Technical, Situational, and HR types
- Live answer timer and word count tracker
- **AI scoring across 4 dimensions:** Relevance, Structure (STAR method), Depth, Communication
- Instant feedback with strengths, improvement points, and a model answer
- Session summary with score per question
- Full history tracking across sessions (localStorage)

### 📄 Resume Analyzer
- Paste your resume text (and optionally a job description)
- **ATS compatibility score** (0–100) and **JD match score** (when JD is provided)
- Section-by-section breakdown: Summary, Experience, Skills, Education, Formatting
- Missing ATS keywords highlighted
- Quick wins list and AI-rewritten summary for maximum impact
- Identifies both strengths and critical issues

### 🧭 Skill Gap Planner
- Enter your target role and current skills
- Select your experience level (Fresher / Junior / Mid / Senior)
- **Readiness score** showing how close you are to job-ready
- Critical skill gaps vs. nice-to-have gaps clearly separated
- **3-phase personalized learning roadmap** with duration and resources per phase
- Portfolio project ideas to build real-world credibility
- Estimated time to become job-ready

### 🔎 Job Trust Checker
- Paste any job posting to detect scam patterns
- **Trust score (0–100)** with a verdict: `SAFE`, `SUSPICIOUS`, or `LIKELY SCAM`
- Red flags and green flags clearly listed
- 5-dimension analysis: Company Clarity, Compensation Realism, Requirements Sensibility, Language Quality, Contact Legitimacy
- Clear actionable recommendation for the job seeker

---



## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + Vite |
| AI Engine | Anthropic Claude API (`claude-sonnet-4-20250514`) |
| Styling | Custom CSS-in-JS (no external UI library) |
| Fonts | DM Sans, Syne, DM Mono (Google Fonts) |
| Storage | localStorage (session history) |
| Deployment | Vercel |

---

## ⚡ Getting Started

### Prerequisites

- Node.js v18 or higher
- An Anthropic API key — get one at [console.anthropic.com](https://console.anthropic.com)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/harishpatel33254/prep-ai.git
cd prep-ai

# 2. Install dependencies
npm install

# 3. Create environment file
cp .env.example .env
```

### Environment Variables

Create a `.env` file in the root directory:

```env
VITE_ANTHROPIC_KEY=sk-ant-your-api-key-here
```

> ⚠️ **Never commit your `.env` file.** It is already in `.gitignore`.

### Running Locally

```bash
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

### Building for Production

```bash
npm run build
npm run preview
```

---

## 🌐 Deployment

### Deploy to Vercel (Recommended)

1. Push your code to GitHub
2. Go to [vercel.com](https://vercel.com) and import your repo
3. Set Framework Preset to **Vite**
4. Go to **Settings → Environment Variables** and add `VITE_ANTHROPIC_KEY`
5. Click **Deploy** — your app is live!

### Deploy to GitHub Pages

```bash
npm install --save-dev gh-pages
```

Add to `package.json`:

```json
"homepage": "https://YOUR_USERNAME.github.io/prep-ai",
"scripts": {
  "predeploy": "npm run build",
  "deploy": "gh-pages -d dist"
}
```

Then run:

```bash
npm run deploy
```

> ⚠️ GitHub Pages cannot securely store API keys. Use Vercel for production or set up a backend proxy.

---

## 📁 Project Structure

```
prep-ai/
├── public/
│   └── vite.svg
├── src/
│   ├── App.jsx          ← Main application (all 4 tools)
│   └── main.jsx         ← React entry point
├── .env                 ← API key (not committed)
├── .env.example         ← Template for env setup
├── .gitignore
├── index.html
├── package.json
├── README.md
└── vite.config.js
```

---

## 🤖 How the AI Works

Every tool sends a carefully engineered prompt to Claude and expects a structured **JSON response** that drives the UI dynamically.

```
User input (resume / answer / skills / job post)
        ↓
Structured prompt with role context + evaluation criteria
        ↓
Claude API (claude-sonnet-4-20250514)
        ↓
JSON response parsed → scores, feedback, roadmap, flags
        ↓
Dynamic UI rendered with results
```

Each tool uses a different evaluation framework:
- **Interview** → STAR method scoring across 4 dimensions
- **Resume** → ATS compatibility + keyword gap analysis
- **Skill Gap** → Role requirements vs. current profile → phased roadmap
- **Job Check** → Pattern recognition for fraud signals

---

## 🗺️ Roadmap

- [ ] Voice input for interview practice (Web Speech API)
- [ ] Resume PDF upload and parsing
- [ ] Portfolio project review tool
- [ ] LinkedIn profile analyzer
- [ ] Mock coding round for engineering roles
- [ ] Export results as PDF report
- [ ] User accounts and cloud-synced history
- [ ] Multi-language support

---

## 🙋 FAQ

**Q: Is my data stored anywhere?**
> No. All data is processed in your browser. Interview history is saved locally on your device only. Nothing is sent to any server except the Claude API for AI evaluation.

**Q: How much does the API cost?**
> Claude API pricing is usage-based. For a hackathon demo with moderate use, costs are minimal (typically under $1). See [Anthropic pricing](https://anthropic.com/pricing) for details.

**Q: Can I use this without an API key?**
> The app includes fallback mock responses for demo purposes if the API call fails, so the UI is always functional.

**Q: What job roles are supported?**
> Currently: Software Engineer, Data Scientist, Product Manager, Marketing Analyst, Finance Analyst, UI/UX Designer. More roles can be added easily in the `ROLES` and `QUESTIONS` config in `App.jsx`.

---

## 👨‍💻 Built By

Made with ❤️ for the **AI for Employability Hackathon**

> *"Practice. Get scored. Land the job."*

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**If this helped you, please give it a ⭐ on GitHub!**

</div>

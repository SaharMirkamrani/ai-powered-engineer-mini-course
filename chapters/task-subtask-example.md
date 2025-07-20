## ✅ Tasks & Subtasks for AI Podcast Summarizer (MVP)

### 1. 🛠️ Project Setup
- [ ] Set up monorepo or separate frontend/backend (optional)  
- [ ] Initialize Next.js project with TailwindCSS  
- [ ] Set up backend (Node.js/Express or Python FastAPI)  
- [ ] Configure environment variables for API keys and services  
- [ ] Add GitHub repo + CI config  

---

### 2. 🎧 Audio Input

#### 2.1 Accept podcast link or upload
- [ ] Design UI: input field for podcast URL  
- [ ] Validate supported platforms (e.g. Apple Podcasts, Spotify)  
- [ ] Optionally support file upload (MP3, M4A)  
- [ ] Send to backend for processing  

---

### 3. 🧠 Transcription Pipeline

#### 3.1 Integrate Whisper (on VPS or local)
- [ ] Install and test Whisper  
- [ ] Handle long audio chunking + batching  
- [ ] Return full transcript to backend  

#### 3.2 (Optional) use 3rd-party STT (if Whisper is skipped)
- [ ] Use API like Deepgram, AssemblyAI, or OpenAI Whisper API  
- [ ] Handle response format and costs  

---

### 4. 🪄 Summarization Pipeline

#### 4.1 Prompt Design & Context Engineering
- [ ] Design few-shot prompt for summarization  
- [ ] Optimize prompt for clarity, structure, and tone  

#### 4.2 LLM Integration
- [ ] Connect to GPT-4o / Claude 3.5 API  
- [ ] Send transcript and receive summary  
- [ ] Parse and format summary (headings, timestamps, etc.)  

---

### 5. 🧪 UI – Results Display
- [ ] Show summary text with headers/bullets  
- [ ] Display timestamped sections (optional: clickable)  
- [ ] Add loading states and error handling  

---

### 6. 📤 Export & Sharing
- [ ] Add "Copy to clipboard" button  
- [ ] Export summary to Markdown or PDF  
- [ ] Optional: "Share summary via link"  

---

### 7. 🗃️ Save to Dashboard (optional MVP+)
- [ ] Add simple login (magic link or GitHub login)  
- [ ] Store summaries per user  
- [ ] Show saved summaries in a dashboard  

---

### 8. 🧪 Testing & QA
- [ ] Test with different podcast lengths  
- [ ] Test low-quality audio edge cases  
- [ ] Manual prompt result validation  
- [ ] Basic unit + integration tests  

---

### 9. 📑 Docs & Final Touches
- [ ] Add README with setup instructions  
- [ ] Add `.env.example`  
- [ ] Create a simple changelog  
- [ ] Add credits for any open-source tools or APIs used  

---

### 10. 🚀 Deployment
- [ ] Deploy frontend on Vercel (or Netlify)  
- [ ] Deploy backend on VPS or Render  
- [ ] Connect domain if needed  
- [ ] Monitor logs and errors  

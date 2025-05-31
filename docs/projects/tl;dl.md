# TL;DL — Your Commute-Sized Daily Dose of YouTube

**TL;DL (Too Long; Didn’t Listen)** is my weekend side project that came out of pure necessity.

## 🚌 The Problem: YouTube ≠ Commute-Friendly

I spend about 30-45 minutes commuting between home and office — a perfect window to catch up on the latest in business, geopolitics, sports, and tech. Naturally, I built a habit of queuing up YouTube videos, speeding them up to 1.5x, and diving in.

But there was a problem:

- Total length of videos go well over an hour.
- I couldn’t always finish them during the commute.
- Some days, I had to watch them late at night or just skip them entirely.
- Over time, my watch queue became an unread inbox 😩

## 🎧 The Lightbulb Moment: Podcasts + AI

Then I came across **NotebookLM** by Google and its audio summary feature — that’s when it hit me:

> **Why not convert YouTube videos into concise podcast-style summaries?**

- Audio is perfect for my commute.
- AI can compress the fluff.
- Bonus: I don’t have to *watch* anything.

Thus, **TL;DL** was born.

## 🛠️ The Stack: Simple, Smart, and Efficient

I didn’t want to reinvent the wheel or burn API tokens unnecessarily. So I stitched together a neat little pipeline with open-source tools and free APIs.

### 🔄 1. Channel Tracking with RSS

- Discovered YouTube offers an RSS feed for every channel.
- No scraping. No quota limits. Just clean metadata (title, video ID, publish date).
- Filtered videos from the last 24 hours for freshness.
- Example for [RSS Feed](https://www.youtube.com/feeds/videos.xml?channel_id=UCREjSTFcjv3TMm6DcQcu1yg)

### 📜 2. Transcript Extraction

- Used a Python library (`youtube_transcript_api`) to pull subtitles programmatically.
- No need to download the video or fiddle with any third-party tools.

### 🤖 3. Summarization with ChatGPT

- Sent the transcript to OpenAI’s API via LangChain.
- Translated (if needed) and summarized into crisp, conversational scripts.

### 🗣️ 4. Text to Speech

- Found a free TTS engine using Microsoft Edge voices (`edge-tts`).
- Not Google-quality, but good enough for now.
- Planning to switch to Google Gemini 2 voices next.

### ⬆️ 5. Podcast Publishing

- Used the YouTube Data API v3 to upload the audio as a video.
- Dockerized the whole thing and scheduled it to run every morning 🚀

## 🎯 What’s Next

This is just v0.1 — very much a personal project right now. But here’s where it’s heading:

### 👥 Two-Speaker Format

- Make the audio feel more dynamic and natural, with alternating voices.
- Adds personality to the summaries.

### ⚙️ Configurable for Others

- Let users plug in their own channels, categories, or languages.
- Might open source it or wrap it into a simple web interface.

### 🧼 Code Cleanup & Polish

- Refactor the Python + shell scripts for better readability and structure.
- Add:
  - Fail checks & retries
  - Logging
  - `pydantic` for validation
  - Docstrings and typed functions
- Move away from calling Python files directly from Docker shell — not proud of that bit 🙈

## 💡 Why This Matters

We’re drowning in content. TL;DL tries to fight back with:

- **Curation** (latest videos only)  
- **Compression** (summarized)  
- **Conversion** (text → audio → podcast)

If you're like me — short on time but high on curiosity — I think you’ll love what this turns into.

Stay tuned. And maybe... stay subscribed? 😄

PS: Link to youtube channel -> [Youtube Podcast - TL;DL](https://www.youtube.com/@tldl_by_datapaglu_avi)

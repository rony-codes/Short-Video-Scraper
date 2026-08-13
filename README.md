# Short Video Scraper

A small Node.js/Express app that searches for short-form videos (via SerpApi's Google Short Videos engine) and downloads them locally using `yt-dlp`.

## Features

- 🔍 Search for short videos by keyword
- 📥 Download selected videos to the server
- 🌐 Simple frontend served from `/public`

## Tech Stack

- **Backend:** Node.js, Express
- **Search:** [SerpApi](https://serpapi.com/) (Google Short Videos engine)
- **Downloader:** [yt-dlp](https://github.com/yt-dlp/yt-dlp)

## Prerequisites

Before running this project, make sure you have:

- [Node.js](https://nodejs.org/) v18+
- [yt-dlp](https://github.com/yt-dlp/yt-dlp#installation) installed and available on your system `PATH`
  - Verify with: `yt-dlp --version`
- A [SerpApi](https://serpapi.com/) account and API key

## Installation

1. **Clone the repo**
   ```bash
   git clone https://github.com/rony-codes/Short-Video-Scraper.git
   cd Short-Video-Scraper
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**

   Create a `.env` file in the root directory:
   ```env
   SERPAPI=your_serpapi_key_here
   ```

 

4. **Run the server**
   ```bash
   node index.js
   ```

   The app will be available at `http://localhost:3000`.

## API Endpoints

### `GET /api/search`

Search for short videos.

**Query params:**
| Param | Required | Description |
|-------|----------|-------------|
| `q` | ✅ | Search query |
| `count` | ❌ | Number of results to return (default: 5) |

**Example:**
```bash
curl "http://localhost:3000/api/search?q=cooking+tips&count=3"
```

### `POST /api/download`

Download a video by URL.

**Body:**
```json
{
  "url": "https://example.com/video-url",
  "title": "optional-filename"
}
```

Downloaded files are saved to `/downloads` and served statically at `/downloads/<filename>`.

## Project Structure

```
.
├── public/          # Static frontend files
├── downloads/        # Downloaded videos (auto-created, gitignored)
├── index.js          # Main Express server
├── package.json
└── .env               # Your API key (not committed)
```

## Notes

- This project is intended for personal/educational use. Downloading video content may be subject to the terms of service of the platform the video originates from.
- SerpApi usage counts against your monthly search quota — see [SerpApi pricing](https://serpapi.com/pricing).

## License

ISC

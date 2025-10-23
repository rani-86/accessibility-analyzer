👇

🌐 Accessibility Analyzer

Accessibility Analyzer is a full-stack web application that scans any website URL for accessibility issues, performance, SEO, and best practices using tools like axe-core, Puppeteer, and Lighthouse.

🚀 Features

🧩 Scans websites for accessibility violations using axe-core

⚡ Analyzes performance, SEO, and best practices using Lighthouse

📊 Returns structured JSON reports for easy frontend visualization

🌙 Supports dark mode and clean UI in frontend

☁️ Deployed using Render (Backend) and Vercel (Frontend)

🏗️ Tech Stack
Component	Technology Used
Frontend	React.js
Backend	Node.js + Express
Web Scraping	Puppeteer
Accessibility Audit	axe-core
Performance & SEO Audit	Lighthouse
Deployment	Render (Backend), Vercel (Frontend)
⚙️ Installation (Local Setup)
1️⃣ Clone the Repository
git clone https://github.com/<your-username>/accessibility-analyzer.git
cd accessibility-analyzer

2️⃣ Install Dependencies
npm install

3️⃣ Run the Backend
node index.js

4️⃣ Backend will start at:
http://localhost:5000

🔗 API Endpoints
1️⃣ Root Endpoint

GET /
Description: Check if API is running.
Response:

"Accessibility Analyzer API is running 🚀"

2️⃣ Accessibility Scan (axe-core)

GET /scan?url=<target_url>
Runs an accessibility scan using axe-core and Puppeteer.

Example:

GET http://localhost:5000/scan?url=https://example.com


Response:

{
  "url": "https://example.com",
  "issues": 5,
  "violations": [
    {
      "id": "color-contrast",
      "impact": "serious",
      "description": "Ensures sufficient color contrast between foreground and background colors"
    }
  ]
}


🧠 Libraries Used: puppeteer, axe-core

3️⃣ Lighthouse Audit (Performance + SEO + Accessibility)

GET /lighthouse?url=<target_url>
Performs a Lighthouse audit for performance, accessibility, SEO, and best practices.

Example:

GET http://localhost:5000/lighthouse?url=https://example.com


Response:

{
  "url": "https://example.com",
  "performance": 92,
  "accessibility": 88,
  "seo": 95,
  "bestPractices": 90
}


🧠 Libraries Used: lighthouse, chrome-launcher

4️⃣ Full Combined Scan

GET /full-scan?url=<target_url>
Combines both axe-core and Lighthouse scans into a single response.

Example:

GET http://localhost:5000/full-scan?url=https://example.com


Response:

{
  "url": "https://example.com",
  "accessibility_issues": 5,
  "accessibility_violations": [...],
  "lighthouse_report": {
    "performance": 91,
    "accessibility": 88,
    "seo": 97,
    "bestPractices": 93
  }
}

🧠 How It Works Internally

This project works in two powerful layers — combining real browser automation and web audits:

🔹 1. Puppeteer + axe-core (Accessibility Analysis)

The backend launches a headless Chrome browser using Puppeteer.

It navigates to the target URL (provided by the user).

It then injects axe-core, an open-source accessibility testing library.

The script runs axe.run() inside the webpage’s DOM.

The results are returned in JSON format — including rule IDs, severity (minor/serious/critical), and descriptions.

✅ Example Rule Detected: Missing alt attribute on images
✅ Example Rule Detected: Low color contrast between text and background

🔹 2. Lighthouse (Performance, SEO & Best Practices)

The backend runs Lighthouse in headless mode using Chrome Launcher.

Lighthouse loads the same page and runs audits across categories:

Performance — load speed, render time, caching, etc.

Accessibility — semantic HTML, ARIA roles, etc.

SEO — meta tags, mobile-friendliness, indexing hints.

Best Practices — HTTPS usage, safe requests, responsive design.

It extracts the final scores and returns them as JSON.

✅ Example:

Performance: 92

Accessibility: 88

SEO: 95

Best Practices: 90

🔹 3. Combined Response

Finally, the /full-scan endpoint merges both results — giving users a holistic report of how accessible and optimized a website is.

🌍 Deployment Guide
🛠 Backend on Render

Push your backend to GitHub

Create a new Web Service on Render

Set environment:

BUILD COMMAND: npm install
START COMMAND: node index.js


Add Environment Variable (if using Lighthouse):

NODE_ENV = production


Deploy — e.g.

https://aa-backend-2.onrender.com

💻 Frontend on Vercel

Push your React app to GitHub

Import it into Vercel

Update API URLs:

const res = await axios.get(`https://aa-backend-2.onrender.com/scan?url=${url}`);


Deploy 🎉

📊 Example Use Case

Enter any website URL (like https://www.wikipedia.org) and the app will:

Run axe-core for accessibility issues

Run Lighthouse for performance and SEO

Return a complete accessibility report to the frontend

👩‍💻 Author

Rani Sharma
🌐 LinkedIn

💻 GitHub

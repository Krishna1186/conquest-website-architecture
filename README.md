# Conquest: The Digital Front Door

> **Note to Recruiters:** This repository demonstrates the *system architecture* designed for the Conquest website. The actual source code is private, but this documentation explains the engineering decisions that make the site instant, reliable, and easy to update.

## 🚀 The Goal: "Impossible to Crash"
When 50+ startups launch simultaneously, thousands of investors and users flood our site. We couldn't afford a "loading..." spinner or a server crash.

We built Conquest to be **static-first**. This means:
1.  **No Waiting**: The website doesn't get built when you click "Enter"—it's already built and waiting for you.
2.  **Global Speed**: We use a global delivery network (CDN) so a user in Bangalore gets the site from a server in Mumbai, not New York.
3.  **Zero Downtime**: Because there is no central database to "go down" during traffic spikes, the site essentially cannot crash.

## ⚡ Key Engineering wins

### 1. Instant Navigation
Clicking a link on Conquest feels like switching tabs in your browser. We use a technique called **prefetching**:
- When your mouse hovers over a link, the site secretly downloads that page in the background.
- By the time you click, the content is already there.
- **Result**: Page transitions happen in **< 100 milliseconds**.

### 2. "Lazy" Loading
We don't make your phone download data it doesn't need.
- Images only load when you scroll them into view.
- Heavy fonts or scripts wait until the main text is readable.
- **Impact**: The site loads in 1.4 seconds on a 4G mobile connection.

### 3. Editor-Friendly Updates
Our marketing team changes content daily. They shouldn't need a developer to fix a typo.
- We connected the site to a generic Content Management System (headless CMS).
- When they hit "Publish," a robot automatically rebuilds the entire site and updates usage worldwide in about 2 minutes.

## 🛠️ Technology Choices (The "Why")

| Problem | Our Solution | Why? |
| :--- | :--- | :--- |
| **Speed** | **Gatsby (React)** | It turns complex code into simple HTML files that load instantly. |
| **Reliability** | **Netlify / Vercel** | They distribute our files to hundreds of servers worldwide. |
| **Scaling** | **Static Generation** | Serving a generic file to 1 person costs the same computing power as serving it to 1 million. |

---

*This architecture ensures that Conquest focuses on its mission—accelerating startups—rather than fixing server outages.*

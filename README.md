# Portfolio & Resume Website

A cross-platform portfolio website built with React Native + Expo, running on web via GitHub Pages. Displays GitHub projects as interactive flip cards, an experience timeline, and a live API backend deployed on Vercel.

## 🌐 Live Site
**[preetirawathw-25.github.io](https://preetirawathw-25.github.io)**

## Tech Stack

| Technology | Purpose |
|---|---|
| React Native + Expo SDK 54 | Cross-platform framework (web-first) |
| Expo Router | File-based navigation |
| NativeWind v4 (Tailwind) | Utility-first styling |
| Lottie React Native | Animated pulsing dot (current role) |
| Express.js | REST API backend |
| Vercel | API hosting (serverless) |
| GitHub Pages | Frontend hosting |
| GitHub API | Live repo + README data |

## How to Run

### Prerequisites
- Node.js 18+
- npm or yarn

### Frontend

```bash
git clone https://github.com/preetirawathw-25/my-website-resume
cd my-website-resume
npm install
npm run web
```

### API (Backend)

```bash
cd api
npm install
```

Create a `.env` file:
```
GITHUB_TOKEN=your_github_personal_access_token
```

### Deploying the Frontend

```bash
npx expo export -p web
# Copy dist/ contents to your GitHub Pages repo
```

### Deploying the API

```bash
cd api
vercel --prod
```

## 📁 Project Structure

```
my-website-resume/
├── app/
│   ├── (tabs)/
│   │   ├── index.tsx              # Home — projects + experience
│   │   ├── about.tsx              # Coming Soon page
│   │   ├── _layout.tsx            # Tab navigation bar
│   │   └── index.styles.ts        # Home screen stylesheet
│   └── _layout.tsx                # Root layout + font loading
├── components/
│   ├── card-component.tsx         # Flip card with "What I Learnt" back
│   ├── hero-component.tsx         # Hero section with profile info
│   ├── experience-item.tsx        # Experience entry (title, tags, dates)
│   ├── timeline-connector.tsx     # Animated dot + vertical line
│   ├── icon-button.tsx            # Tag chip with ripple wave animation
│   ├── footer-component.tsx       # Footer with social links
│   └── terminal-component.tsx     # Terminal-style UI element
├── hooks/
│   └── use-github.ts              # useRepos, useProfile, useLearnt hooks
├── assets/
│   └── images/
│       └── pulsingGreenDote.json  # Lottie animation for current role
├── api/
│   ├── index.js                   # Express API (repos, profile, readme)
│   ├── package.json
│   └── vercel.json                # Vercel serverless config
├── global.css                     # NativeWind component classes
└── app.json                       # Expo config + web output settings
```

## 🎯 Key Features

### UI & Interactions
- **Flip Cards** — Project cards flip on press to reveal a "What I Learnt" section pulled live from each repo's README
- **Experience Timeline** — Animated Lottie green dot for current role, pink dot + line for past roles
- **Responsive Grid** — 1 column (mobile) / 2 columns (tablet) / 4 columns (desktop ≥1400px)
- **Wave Ripple** — Tag chips have a press-to-fill wave animation (disabled for non-clickable tags)
- **Coming Soon** — About Me page styled to match the site

### Technical
- **Live GitHub Data** — Repos and README sections fetched from a Vercel API at runtime
- **NativeWind** — Tailwind utility classes on React Native components via `className`
- **Serverless API** — Express app deployed via `@vercel/node` with CORS and GitHub token auth
- **Cross-platform** — Single codebase runs on iOS, Android, and Web

## API Endpoints

Base URL: `https://api-seven-mu-55.vercel.app`

| Endpoint | Description |
|---|---|
| `GET /repos` | All public GitHub repositories |
| `GET /profile` | GitHub profile data |
| `GET /readme/learnt/:repo` | "What I Learnt" section from a repo's README |

## What I Learnt

### React Native & Cross-Platform
- Building a portfolio as a React Native app that compiles to web via Expo
- How NativeWind (Tailwind CSS for React Native) works and its limitations with dynamic classes
- Using `useWindowDimensions` for reliable responsive breakpoints instead of CSS media queries
- Percentage-based flex widths to avoid floating-point pixel wrapping in grid layouts

### Animation
- Integrating Lottie animations in React Native with `lottie-react-native`
- Building a custom ripple/wave fill animation using `Animated.Value` and interpolation
- 3D card flip effect using `rotateY` transform and `backfaceVisibility`

### Deployment
- Hosting a React Native web export on GitHub Pages with `.nojekyll` for `_expo/` asset serving
- Deploying an Express.js API as a Vercel serverless function using `@vercel/node`
- How Jekyll's `_` directory filtering silently breaks Expo's `_expo/static/` asset paths

### API & Data
- Fetching and parsing GitHub README markdown to extract specific sections at runtime
- Building a lightweight Express proxy to avoid GitHub API rate limits on the frontend

---

Built with Expo + React Native as a living portfolio — ships to web, iOS, and Android from one codebase.

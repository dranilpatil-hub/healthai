# HealthAI — Symptom Assessment App

AI-powered symptom assessment platform built with React + Claude API.

## Project Structure

```
healthai/
├── public/
│   └── index.html          ← HTML shell
├── src/
│   ├── index.js            ← React entry point
│   └── App.js              ← Entire application
├── package.json            ← Dependencies
├── vercel.json             ← Vercel config
└── .gitignore
```

## Deploy to Vercel (Step by Step)

### Option A — GitHub + Vercel (Recommended)

1. Create a GitHub account at github.com if you don't have one
2. Create a new repository called `healthai`
3. Upload all these files maintaining the folder structure
4. Go to vercel.com → New Project → Import from GitHub
5. Select the `healthai` repo → Deploy
6. Done — live in ~2 minutes

### Option B — Vercel CLI

```bash
npm install -g vercel
cd healthai
vercel login
vercel --prod
```

## Enable Email Reports

1. Go to emailjs.com → Create free account
2. Add Email Service (Gmail recommended)
3. Create Template with these variables:
   - {{to_name}}, {{to_email}}, {{chief_complaint}}
   - {{triage_label}}, {{triage_reasoning}}
   - {{conditions}}, {{next_steps}}, {{disclaimer}}
4. In src/App.js find this section and fill in your keys:

```js
const [emailjsConfig] = useState({
  serviceId: "service_XXXXXX",      ← from EmailJS dashboard
  templateId: "template_XXXXXX",    ← from EmailJS dashboard
  publicKey: "YOUR_PUBLIC_KEY"      ← from EmailJS dashboard
});
```

## Notes
- The Claude API is called directly from the browser (works in this artifact environment)
- For production deployment, consider adding a backend proxy to protect API keys
- All user data stays in browser memory only — nothing is stored server-side

# VA Claims Shield

> **A veteran-built, open-source toolkit for submitting, tracking, and defending VA benefits claims.**
> Because the VA shouldn't be the only one with infrastructure.

---

## We Are Actively Seeking Contributors

If you are a veteran, a developer, a legal advocate, or anyone who has watched the VA lose documents, close cases without cause, or stonewallclaims — **this project is for you.**

The U.S. Department of Veterans Affairs operates a document intake system that is opaque, unaccountable, and designed in a way that makes it nearly impossible for a veteran to prove what they submitted, when they submitted it, or whether it was ever received. Veterans are told their documents were never received. Appeals are closed without explanation. Cases are assigned to political appointees with no accountability.

This project builds the infrastructure to fight back.

We are building a suite of open-source tools that give veterans — and the advocates who support them — the same kind of institutional power the VA already has. Programmatic document submission. Irrefutable audit trails. Status tracking. Evidence package builders. All built on the VA's own publicly available APIs, turned back around in service of the people those APIs were supposed to serve.

**This is not a charity project. This is a weapons-grade accountability toolkit.**

---

## What We Are Building

### Phase 1 — Submission Tracker
A web application that submits documents directly to the VA's Veterans Benefits Management System (VBMS) via the Benefits Intake API and logs every submission with a permanent, tamper-evident audit record. Every GUID. Every timestamp. Every status change. Stored in a database you control.

**The problem it solves:** The VA says they never received your document. You have proof they did.

### Phase 2 — Status Poller
A background service that monitors the status of submitted documents using stored GUIDs, polls the VA API on a schedule, and alerts the veteran when something changes — received, processing, error, or suspiciously stuck.

**The problem it solves:** You stop waiting by the phone. The system tells you the moment something moves.

### Phase 3 — Evidence Package Builder
A guided tool that walks a veteran through building a complete evidence package — claim narrative, supporting documents, medical records, service records — and submits the entire bundle through the Intake API in one operation.

**The problem it solves:** Veterans don't know what to submit or how to organize it. This tool makes a complete, properly structured submission accessible to anyone.

---

## The API

This project is built on the **VA Benefits Intake API**, a publicly available API provided by the U.S. Department of Veterans Affairs through their Lighthouse developer platform.

- **API Portal:** https://developer.va.gov/explore/api/benefits-intake
- **Sandbox signup:** https://developer.va.gov/explore/api/benefits-intake/sandbox-access
- **Documentation:** https://developer.va.gov/explore/api/benefits-intake/docs
- **API Terms of Service:** https://developer.va.gov/terms-of-service

Anyone can sign up for a free sandbox key. Production access requires a demo and VA approval.

---

## Setting Up Your Development Environment

This guide will take you from zero to a working local environment. Follow each step in order.

### What You Need
- A Windows, Mac, or Linux machine
- Node.js v18 or higher
- Git
- A VA sandbox API key (free — see above)
- Postman (for testing API calls without writing code first)

---

### Step 1 — Get Your VA Sandbox API Key

1. Go to https://developer.va.gov/explore/api/benefits-intake/sandbox-access
2. Fill out the form with your name, email, and organization
3. You will receive a sandbox API key by email within minutes
4. Save this key — you will need it in every API call

---

### Step 2 — Install Postman

Postman is the tool we use to test API calls before building them into code. It lets you see exactly what the VA API returns without writing a single line of code first.

**On Windows (via Chocolatey — run CMD as Administrator):**
```bash
choco install postman -y
```

**On Mac:**
```bash
brew install --cask postman
```

**On Linux:**
```bash
snap install postman
```

Or download directly from https://www.postman.com/downloads/

---

### Step 3 — Test Your API Key in Postman

This confirms your sandbox key works before you write any code.

**Step 3a — Generate an upload slot**

1. Open Postman and create a new request
2. Set method to **POST**
3. Set URL to: `https://sandbox-api.va.gov/services/vba_documents/v1/uploads`
4. Click the **Headers** tab
5. Add key: `apikey` / value: `YOUR_SANDBOX_KEY`
6. Hit **Send**

You should receive a JSON response containing a `guid` and a `location` URL. This means your key works and you are connected to the VA sandbox.

**Step 3b — Upload a test PDF**

1. Open a new request tab in Postman
2. Set method to **PUT**
3. Paste the entire `location` URL from the previous response as the URL
4. Click the **Body** tab → select **binary** → select any PDF file from your machine
5. Hit **Send** immediately — the location URL expires in 15 minutes

A **200 OK** response means you have successfully submitted a document to the VA sandbox. You are ready to build.

---

### Step 4 — Clone This Repository

```bash
git clone https://github.com/IainAmosMelchizedek/va-claims-shield.git
cd va-claims-shield
```

---

### Step 5 — Install Dependencies

```bash
npm install
```

---

### Step 6 — Set Up Your Environment Variables

Copy the example environment file:

```bash
cp .env.example .env
```

Open `.env` and add your VA sandbox API key:

```
VA_API_KEY=your_sandbox_key_here
VA_API_BASE_URL=https://sandbox-api.va.gov
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React + Vite |
| Backend | Node.js + Express |
| Database | PostgreSQL |
| Deployment | Vercel (frontend) + your own server (backend) |
| API | VA Benefits Intake API (Lighthouse) |
| Testing | Postman |
| Version Control | GitHub |

---

## How to Contribute

We need developers, designers, veterans, legal advocates, and people who are just angry enough to do something about it.

### If you are a developer:
- Check the **Issues** tab for open tasks
- Comment on an issue before starting work so we don't duplicate effort
- Fork the repo, make your changes, and open a pull request
- All pull requests require a description of what you changed and why

### If you are a veteran:
- Open an issue describing a problem you have experienced with the VA claims process
- Your experience is the product roadmap

### If you are a legal advocate or VSO:
- Open an issue or start a Discussion describing what tools would be most useful to your clients
- We want to build what actually helps people, not what sounds good on paper

### Code Standards
- Industry standard practices only
- No shortcuts
- Every implementation step must be tested before moving to the next
- Document what you build

---

## The Person Behind This Project

This project was initiated by **Iain Melchizedek**, a U.S. veteran, former federal compliance examiner at the CFPB, and founder of Safe Passage Strategies LLC — a data sovereignty consultancy.

Iain has 17 years of federal government experience and has personally experienced the VA's pattern of administrative obstruction, case closure without cause, and institutional indifference. He built this project because he got a sandbox API key, tested it in an afternoon, and realized the VA's own infrastructure could be used to hold them accountable.

He is not waiting for the VA to fix itself. He is building the tools to make fixing unnecessary.

---

## License

MIT — use it, fork it, build on it. Just don't use it to harm veterans.

---

## Contact

- **Project:** https://github.com/IainAmosMelchizedek/va-claims-shield
- **Organization:** Safe Passage Strategies LLC
- **Web:** https://safepassagestrategies.com

---

*Built by a veteran. For veterans. Against the institution that was supposed to serve them.*

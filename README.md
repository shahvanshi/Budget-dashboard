# 💰 Budget Dashboard

A personal finance web app built for real life — simple to use, beautiful to look at, and synced to your own Google Sheet.

**Live app → [shahvanshi.github.io/Budget-dashboard](https://shahvanshi.github.io/Budget-dashboard)**

---

## What it does

A daily financial companion that helps you track spending, build towards goals, and understand where your money is going — without spending hours on spreadsheets.

- Log transactions in under 30 seconds
- See your monthly spending broken down by category
- Track progress towards personal savings goals
- Compare budget vs. actual spending with over/under indicators
- Handle Splitwise shared expenses cleanly
- Build your own custom categories that match your actual life
- Everything syncs to your personal Google Sheet in real time

---

## Features

### Quick log
Add a transaction in seconds — pick a date, enter an amount, choose a category from your custom list, add an optional note. Supports regular transactions, credit card purchases (logged by category, not as a payment), and Splitwise monthly settlements.

### Overview
Monthly snapshot with navigation arrows to move between months. Shows income, expenses, savings, net balance, and savings rate at a glance. Includes a spending breakdown pie chart, savings breakdown pie chart, and a budget check panel showing exactly which categories are over or under budget.

### Goals
Set savings goals with a target amount and optional monthly contribution. Track progress with a visual bar. Contribute manually whenever you put money in. Edit any goal at any time — name, target, amount saved, icon.

### Budget
Set monthly targets for each category once. Progress bars fill automatically as you log transactions — green when on track, amber when close, red when over.

### Splitwise
A dedicated flow for month-end Splitwise settlements. Since you settle at the end of each month, the app lets you log your share per category in one session. Tagged separately so you can see your Splitwise spending on its own or combined with regular expenses.

### Categories
Fully custom — build your own income, expense, and savings categories. Add ones that match your life (e.g. TFSA, FHSA, Pet care, Freelance). All categories sync to your Google Sheet and appear instantly in the Quick log dropdowns.

---

## Tech stack

| Layer | Technology |
|---|---|
| Frontend | HTML, CSS, Vanilla JavaScript |
| Hosting | GitHub Pages |
| Auth | Google Identity Services (OAuth 2.0) |
| Database | Google Sheets API v4 |
| Charts | Chart.js |
| Currency | Canadian Dollar (CAD) |

No frameworks. No build tools. No backend server. Just one HTML file.

---

## How the sync works

Your data lives entirely in your own Google Sheet — not on any third-party server. When you sign in with Google, the app gets permission to read and write to your sheet. Every transaction, goal, budget setting, and custom category is saved there within 1-2 seconds of you adding it.

The app also keeps a local copy in your browser so it loads instantly even before the sheet syncs.

Your Google Sheet has 4 tabs:

| Tab | What's stored |
|---|---|
| Transactions | Every transaction you log |
| Goals | Your savings goals and progress |
| Budget | Your monthly budget targets per category |
| Categories | Your custom income, expense and savings categories |

---

## Setup (for your own fork)

If you want to run your own version:

**1. Fork this repository**

**2. Create a Google Cloud project**
- Go to [console.cloud.google.com](https://console.cloud.google.com)
- Create a new project
- Enable the **Google Sheets API**
- Set up an **OAuth consent screen** (External, add your email as a test user)
- Create an **OAuth 2.0 Client ID** (Web application type)
- Add your GitHub Pages URL as an authorised JavaScript origin

**3. Create a Google Sheet**
- Go to [sheets.new](https://sheets.new)
- Copy the Sheet ID from the URL (the long string between `/d/` and `/edit`)
- Share the sheet as "Anyone with the link can edit"

**4. Update the config in `index.html`**
```js
const CLIENT_ID = 'your-oauth-client-id.apps.googleusercontent.com';
const SHEET_ID  = 'your-google-sheet-id';
```

**5. Enable GitHub Pages**
- Go to repo Settings → Pages
- Deploy from branch: `main`, folder: `/ (root)`
- Your app will be live at `https://yourusername.github.io/Budget-dashboard`

---

## Usage tips

**Credit cards** — log purchases by category (e.g. Groceries), not as a card payment. Don't log the card payment itself at month end — that would double-count.

**Splitwise** — during the month, let Splitwise track normally. At month end, check what you owe, and log your share per category using the Splitwise tab in Quick log.

**Categories** — go to the Categories tab and customise before you start logging. Add your savings vehicles (TFSA, FHSA, Emergency Fund jar) and any expense categories specific to your life. Delete the defaults you don't use.

**Budget** — set it once at the start of the month. The Overview will then show you a live over/under breakdown as you log transactions.

---

## Roadmap (Version 3 ideas)

- Recurring transactions (rent, subscriptions auto-logged monthly)
- Net worth tracker
- Year-over-year comparison
- Mobile-optimised layout
- Export to CSV

---

## Built with

Designed and developed with [Claude](https://claude.ai) as a personal finance tool tailored to real usage patterns — Splitwise month-end settlements, dual credit cards, CAD currency, and custom savings categories.

---

*Your data stays in your Google Sheet. Always.*

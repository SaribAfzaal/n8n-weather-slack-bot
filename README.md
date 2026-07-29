# n8n Weather-to-Slack Automation

An automated workflow built with **n8n** that fetches live weather data from the **Open-Meteo API**, formats it into a clean, readable message, and delivers it to a **Slack channel** on a daily schedule — no manual work required.

---

## Overview

This project demonstrates a low-code automation pipeline that:

- Runs automatically on a **daily schedule**
- Pulls real-time weather data from the free **Open-Meteo API** (no API key required)
- Formats the raw API response into a clean, human-readable summary
- Sends the formatted update directly to a **Slack channel** via webhook

It's a small project, but it covers a full automation lifecycle: scheduled trigger → external API call → data transformation → third-party integration — the same pattern used in production workflow automation.

---

## Preview

**n8n Workflow Canvas**

![n8n workflow](./screenshots/workflow-canvas.png)

**Slack Output**

![Slack output](./screenshots/slack-output.png)

---

## Tech Stack

| Tool | Purpose |
|---|---|
| [n8n](https://n8n.io/) | Workflow automation engine (self-hosted locally) |
| [Open-Meteo API](https://open-meteo.com/) | Free weather data source, no auth required |
| [Slack API](https://api.slack.com/messaging/webhooks) | Incoming webhook for message delivery |

---

## How It Works

1. **Schedule Trigger** — kicks off the workflow automatically once a day.
2. **HTTP Request Node** — calls the Open-Meteo API to fetch current weather data (temperature, humidity, wind speed) for a set location.
3. **Function / Set Node** — reformats the raw JSON response into a clean, readable message.
4. **Slack Node** — sends the formatted message to a designated Slack channel via webhook.

---

## Getting Started

Want to run this yourself? Here's how:

### Prerequisites
- [n8n](https://docs.n8n.io/hosting/installation/) installed locally or hosted
- A Slack workspace with an [Incoming Webhook](https://api.slack.com/messaging/webhooks) set up

### Setup

1. **Clone this repository**
   ```bash
   git clone https://github.com/SaribAfzaal/n8n-weather-slack-bot.git
   cd n8n-weather-slack-bot
   ```

2. **Import the workflow into n8n**
   - Open n8n
   - Go to **Workflows → Import from File**
   - Select `workflow.json` from this repo

3. **Add your Slack credentials**
   - In n8n, set up your own Slack credential (or paste your Incoming Webhook URL into the Slack node)
   - This repo's `workflow.json` uses a placeholder URL — no real credentials are included

4. **Set your location**
   - Update the latitude/longitude parameters in the HTTP Request node to your desired location

5. **Activate the workflow**
   - Toggle the workflow to **Active** in n8n so it runs on schedule

---

## Security Note

No API keys, tokens, or webhook URLs are included in this repository. The exported workflow uses placeholder values — you'll need to connect your own Slack credentials to run it.

---

## Future Enhancements

- [ ] **AI-generated summaries** using a local LLM via [Ollama](https://ollama.com/) — instead of raw stats, generate a natural-language weather summary (e.g., *"Warm and humid today — a light jacket for the evening breeze."*)
- [ ] Multi-city support
- [ ] Severe weather alerts / conditional notifications

---

## Author

Built by Sarib Afzaal as a portfolio project exploring workflow automation with n8n.

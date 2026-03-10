# Website Availability Monitor 🌐

![Status](https://img.shields.io/badge/status-active-brightgreen)
![Made With](https://img.shields.io/badge/made%20with-n8n-orange)
![Alerts](https://img.shields.io/badge/alerts-Slack-purple)
![Hosted On](https://img.shields.io/badge/hosted%20on-AWS%20EC2-yellow)
![Schedule](https://img.shields.io/badge/runs%20every-5%20minutes-blue)

## Overview
This project monitors the availability of multiple websites every 5 minutes 
using an automated n8n workflow. When a site goes down, an instant Slack alert 
is triggered with the URL, status code, and timestamp. This eliminates manual 
checking and reduces mean time to detection (MTTD) for outages.

---

## Architecture
![Workflow](screenshots/01-full-workflow.png)

---

## Tech Stack
| Tool | Purpose |
|------|---------|
| n8n | Workflow automation engine |
| HTTP Request Node | Site availability checks |
| Slack API | Real-time alerting |
| AWS EC2 | Hosting the n8n instance |

---

## How It Works
1. **Schedule Trigger** fires every 5 minutes automatically
2. **Code Node** defines the list of URLs to monitor
3. **HTTP Request Node** sends a GET request to each URL and returns the status code
4. **IF Node** checks if the status code equals 200 (site is UP)
5. If the site is DOWN — **Slack Node** sends an alert with the URL, status code and timestamp

---

## Features
- Monitors multiple websites in a single workflow
- Triggers automatically every 5 minutes
- Sends instant Slack alerts when a site is down
- Continues checking remaining sites even if one fails
- Returns HTTP status codes for every site checked

---

## Screenshots

### Full Workflow Canvas
![Workflow](screenshots/01-full-workflow.png)

### Schedule Node
![Schedule](screenshots/02-schedule-node.png)

### Code Node
![Code](screenshots/03-code-node.png)

### HTTP Request Node
![HTTP](screenshots/04-http-request-node.png)

### IF Node
![IF](screenshots/05-if-node.png)

### Slack Node
![Slack](screenshots/06-slack-node.png)

### Successful Test Run
![Test](screenshots/07-successful-test-run.png)

---

## How to Run This Project
1. Clone this repo
2. Import `workflow.json` into your n8n instance
3. Add your Slack API credentials in the Slack node
4. Update the URLs in the Code Node to your own sites
5. Activate the workflow

---

## Lessons Learned
- Learned how to handle HTTP errors gracefully using the "Continue on Fail" setting
- Discovered that n8n returns raw HTML by default and had to enable 
  "Include Response Headers and Status" to retrieve proper HTTP status codes
- Understood the importance of type conversion when using number values 
  inside IF node conditions
- Learned how a single HTTP Request node can process multiple items 
  when fed from a Code node

---

## Author
Isaac Ambi — DevOps Engineer  
[GitHub](https://github.com/isaacambi) | 
[LinkedIn](https://www.linkedin.com/in/isaac-ambi-012b75135/?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_contact_details%3BUJR4Er2tT8e1qurZm%2FUu3Q%3D%3D)

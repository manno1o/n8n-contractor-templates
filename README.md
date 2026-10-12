# n8n workflows for HVAC and plumbing shops

Three workflows I built for contractors. Free, import them and change the names/numbers.

| File | What it does |
|---|---|
| `missed-call-text-back.json` | Someone calls and nobody picks up → they get a text in a few seconds (different message after hours, "reply URGENT" for emergencies) and the office gets a heads-up. |
| `lead-to-quote.json` | Website form → looks up the job in a simple price book → emails the customer a price range right away, or sends it to the office if it's not a standard job. Logs every lead to Google Sheets. |
| `review-request.json` | Job marked done → 2 hours later the customer gets "how did we do, 1-5?". 4-5 gets your Google review link, 1-3 goes to the owner's phone instead. |

## Setup

1. In n8n: **Workflows → Import from file** and pick the JSON.
2. Add credentials: Twilio (1 and 3), SMTP + Google Sheets (2).
3. Replace the placeholders: `Acme Heating & Plumbing`, `+13125550100` (office/owner phone), `+13125550199`, `office@example.com`, sheet URL, review link.
4. Point Twilio webhooks at the webhook URLs (call status for #1, incoming SMS for the reply part of #3).
5. Activate.

Prices in `lead-to-quote` are just examples from the Chicago area, put your own in.

Things to know:
- Texting customers in the US needs A2P 10DLC registration on your Twilio number, otherwise carriers drop the messages.
- Only text people who contacted you or are your customers.

If you want this set up for you, or want the phones answered too (not just texted back): https://manno1o.github.io

MIT license.

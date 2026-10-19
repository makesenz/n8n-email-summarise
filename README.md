# Unread Email Summariser — n8n AI Agent

## Overview
An n8n workflow that fetches up to five unread Gmail messages, generates a short AI summary for each, combines the summaries, and emails one digest to your inbox.

## Workflow
1. Manual Trigger — starts the workflow on demand.
2. Gmail — Get Many — retrieves up to five unread emails.
3. AI Agent + Chat Model — summarises each email in one line, maximum 20 words.
4. Aggregate — combines the individual AI outputs.
5. Gmail — Send — sends one summary email.

## Requirements
- n8n Cloud or self-hosted n8n
- Gmail OAuth credential
- OpenAI API key stored in an n8n credential
- Gmail API configured as required

## Setup
1. Import `Unread_Email_Summariser.json` into n8n.
2. Configure the Gmail credential in the retrieval node.
3. Configure the OpenAI credential in the chat model node.
4. Replace the recipient placeholder in the final Gmail node with your email address.
5. Verify the unread filter, limit of five, AI prompt, and Aggregate settings.
6. Save and execute the workflow.
7. Check the execution output and confirm the digest arrives in your inbox.

## Email Formatting
For a numbered plain-text digest, use this expression in the Gmail Message field:

`{{ 'YOUR UNREAD EMAIL SUMMARY\n\n' + $json.output.map((summary, i) => (i + 1) + '. ' + summary).join('\n\n') }}`

Use HTML formatting only when the Gmail node is configured to send HTML.

## Security
- Never commit API keys, OAuth secrets, or access tokens to GitHub.
- Credentials must be configured separately in n8n.
- Review AI summaries for accuracy.

## Submission Checklist
- [ ] Screenshot of the workflow canvas
- [ ] Screenshot of the summary email
- [ ] Workflow JSON uploaded to GitHub
- [ ] GitHub link shared in WhatsApp
- [ ] Screen recording posted in the community

## Files
- `README.md`
- `Unread_Email_Summariser.json`
EOF

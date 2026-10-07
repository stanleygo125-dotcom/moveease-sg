# MoveEase SG: AI Property Chatbot

A group project (5 members, Republic Polytechnic, C240) that puts home buying and moving in Singapore on one platform. Instead of juggling many sites, a user chats with an AI assistant that finds properties, compares them, and books moving-related services.

## What the chatbot does
1. Collects the buyer's preferences in plain language (e.g. family size, budget, area, must-have features)
2. Searches a 30-property knowledge base
3. Gives each property a match percentage (must-haves weighted higher than nice-to-haves, missing data excluded)
4. Compares shortlisted properties with neighbourhood insights
5. Sends service requests (viewing, mover, cleaning, utilities) to an n8n workflow that emails a confirmation

## Repo layout
- `chatbot/`: the Botpress chatbot export (Stanley's part)
- `website/`: the MoveEase SG website with its Botpress data bridge (Isaac's part)

## My part (Stanley Go)
- Built the Botpress chatbot workflow: preference collection, knowledge-base search, match scoring, property comparison and neighbourhood insights
- Connected the chatbot to a teammate's n8n service-request workflow and a Google AI Studio model
- Fixed mismatched variable names and workflow loops so requests arrived with complete details and confirmation emails
- Improved input handling: the bot now recognises varied restart phrases ("restart", "reset my search") and updates one preference (e.g. budget) without clearing the rest

## Team
- Stanley Go: Botpress chatbot workflow
- Isaac: website (group leader)
- Ezrieqy: n8n service-request workflow
- Jun Jie: property data
- Rayyan: Google AI Studio analysis model

## Tech
Botpress, n8n, Google AI Studio (Gemini), HTML/CSS/JavaScript, Node.js/Express

## Run it
**Chatbot**
1. Create a bot in Botpress and import `chatbot/moveease-chatbot-sanitized.bpz`
2. Add your own `GEMINI_API_KEY` as a config variable
3. Connect your own n8n webhook for the service-request flow

**Website**
1. `cd website && npm start` (serves on http://127.0.0.1:3000, needs Python)
2. Optional data bridge: `cd website/backend`, copy `.env.example` to `.env`, fill in your Botpress details, `npm install`, `npm start`

## Limits
Runs on a small curated dataset rather than live listings, and match scores are AI-generated, so they are guidance rather than exact figures.

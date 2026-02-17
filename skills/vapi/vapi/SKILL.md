---
name: vapi
description: Conversational voice AI calls via Vapi. Make AI-powered phone calls for reservations, appointments, and more.
homepage: https://vapi.ai
metadata:
  {
    "openclaw":
      {
        "emoji": "📞",
        "requires":
          {
            "bins": ["vapi"],
          },
        "install":
          [
            {
              "id": "brew",
              "kind": "brew",
              "formula": "vapiai/tap/vapi-cli",
              "bins": ["vapi"],
              "label": "Install Vapi CLI (brew)",
            },
          ],
      },
  }
---

# Vapi

Use Vapi for conversational AI voice calls. Perfect for restaurant reservations, appointment booking, and other interactive phone tasks.

## Setup

### Install CLI

```bash
brew install vapiai/tap/vapi-cli
```

### Authenticate

```bash
vapi auth
```

This opens the Vapi dashboard to get your API key.

## Quick Start

### 1. Create an Assistant

```bash
vapi assistant create \
  --name "Restaurant Reservations" \
  --model-provider openai \
  --model gpt-4o \
  --voice-provider elevenlabs \
  --voice-id 21m00Tcm4TlvDq8ikWAM \
  --system-prompt "You are a friendly reservation assistant..."
```

### 2. Make a Call

```bash
vapi call --assistant-id asst_xxx --to "+15551234567"
```

## Common Commands

| Command | Description |
|---------|-------------|
| `vapi auth` | Authenticate with Vapi |
| `vapi assistant create` | Create a new AI assistant |
| `vapi assistant list` | List your assistants |
| `vapi call --assistant-id X --to +1...` | Make outbound call |
| `vapi call-logs` | View call history |

## Example: Restaurant Booking

```bash
# Create the assistant
vapi assistant create \
  --name "Ema Austin Reservations" \
  --system-prompt "You are calling to make a reservation at Ema, a Mediterranean restaurant in Austin's Domain. Get the caller's name, phone number, party size, date, and preferred time. Confirm all details before ending the call. Be friendly and professional." \
  --model-provider openai \
  --model gpt-4o \
  --voice-provider elevenlabs \
  --voice-id 21m00Tcm4TlvDq8ikWAM

# Make the call
vapi call \
  --assistant-id asst_xxxxx \
  --to "+15551234567" \
  --message "Hi, I'd like to make a reservation for 2 people this Saturday evening."
```

## Voice Options

Popular ElevenLabs voices:
- `21m00Tcm4TlvDq8ikWAM` — Rachel (default)
- `EXAVITQu4vr4xnSDxMaL` — Sarah
- `CYw3kZ02Hs0563khs1Fj` — Arnold

Full list: https://docs.vapi.ai/voice-dropdown

## Pricing

- Vapi platform: ~$0.10/min + platform fee
- Voice providers (ElevenLabs, OpenAI): additional per-minute costs
- Outbound calls use your imported phone number (Twilio/etc.)

## Notes

- Get an account at [dashboard.vapi.ai](https://dashboard.vapi.ai)
- For outbound calls, import a Twilio number or buy one through Vapi
- The assistant's system prompt defines its behavior

# Security Policy

## Secrets

Never commit:

- `.env`
- `.env.local`
- API keys
- tokens
- private keys
- credentials
- production config values

## Sensitive Areas

Human approval is required before changing:

- authentication
- authorization
- session handling
- password logic
- token handling
- billing/payment logic
- data deletion
- personally identifiable information handling

## Project-Specific Security Notes

- `[SECURITY_NOTE_1]`
- `[SECURITY_NOTE_2]`
- `[SECURITY_NOTE_3]`

## Required For Security-Sensitive Tasks

Record in the task file:

- threat or risk considered
- changed behavior
- tests run
- remaining risk

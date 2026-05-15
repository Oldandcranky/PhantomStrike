# PhantomStrike Demo

PhantomStrike is a lightweight, browser-based demo tool for walking prospects through realistic SDLC attack-chain scenarios and mapping each step back to BlueFlag Security policy detections.

It is designed as a safe demo wrapper — not a real attacker tool and not a live exploitation framework.

## Why this exists

Technical buyers often understand individual findings, but it can be harder to explain how those findings connect into a real attack path.

PhantomStrike helps tell that story:

1. Show a realistic SDLC attack chain.
2. Walk through attacker behavior across GitHub, CI/CD, identities, secrets, and repositories.
3. Show the related BlueFlag policy detections.
4. Keep the demo safe, repeatable, and easy to narrate.

## What PhantomStrike is

PhantomStrike is a simulated command-line and dashboard experience.

The command-line output is fictional and demo-safe, but it is based on real-world SDLC attack patterns, including supply-chain style techniques inspired by Shai-Hulud-type attacks and additional attack flows developed from internal threat research.

The goal is not to show a real hacking tool. The goal is to make the attack path easier to understand.

## What PhantomStrike is not

PhantomStrike is not:

- A real exploit tool
- A scanner
- A red-team framework
- A BlueFlag backend service
- A live integration into customer environments
- A tool that performs real attacks or enforcement actions

All attack output, victims, tokens, repositories, and payloads are fake demo data.

## Main features

### Attack Scenarios

Prebuilt scenarios that walk through common SDLC attack paths, such as:

- Exposed developer tokens
- Over-permissioned GitHub identities
- CI/CD workflow abuse
- Secret discovery
- Bot or service-account abuse
- Repository and branch protection risk
- Supply-chain style compromise paths

### Chain Builder

The Chain Builder lets the presenter create a custom attack path by selecting actions in sequence.

Example flow:

```text
Initial Access -> Recon -> Secret Discovery -> CI/CD Abuse -> Impact
```

This makes the demo feel more like a guided “choose your own adventure” instead of a static slide deck.

### BlueFlag Console View

Each simulated attack action maps back to one or more BlueFlag policy detections.

The BlueFlag view shows:

- Severity
- Policy name
- Affected entity, identity, repo, or org
- Policy description / finding context

The wording is intentionally conservative. It does not claim BlueFlag automatically blocks, suspends, restores, or remediates anything unless that capability is confirmed.

### Policy Library Helper

Because BlueFlag opens policy details in a slider/drawer instead of a deep-linkable URL, PhantomStrike does not try to fake direct policy links.

Instead, clicking a policy name:

1. Copies the policy name to the clipboard.
2. Opens the BlueFlag Policy Library.
3. Lets the presenter paste/search the exact policy name.

This avoids broken links and avoids pretending the product supports UI deep linking where it does not.

## Demo positioning

A good way to explain the tool:

> PhantomStrike is a safe demo wrapper that narrates realistic SDLC attack-chain behavior and shows where BlueFlag policies surface the risky identity, repo, and CI/CD conditions that make those attacks possible.

## Recommended demo flow

1. Start with a prebuilt scenario or open Chain Builder.
2. Pick a short attack chain.
3. Run the chain.
4. Explain what the attacker is doing at each step.
5. Switch to the BlueFlag view.
6. Show the matching policies and affected entities.
7. Use the policy names to open the real BlueFlag Policy Library when needed.

## Technical accuracy notes

The demo should stay grounded in what BlueFlag actually does.

Avoid language like:

- “Blocked”
- “Auto-remediated”
- “Bot account suspended”
- “Protections restored”
- “Session terminated”

Unless those are real, confirmed product capabilities.

Prefer language like:

- “Detected”
- “Policy violation”
- “Finding”
- “Recommended response”
- “Review required”
- “Risk surfaced”
- “Affected entity”

## Configuration

The Settings panel contains the BlueFlag UI URL.

Example:

```text
https://your-instance.identityscience.ai
```

This is used when opening the BlueFlag Policy Library.

No API token is required for the current demo flow.

## Running locally

This is a static HTML demo.

Open the HTML file directly in a browser:

```text
phantomstrike-demo.html
```

Or serve it locally:

```bash
python3 -m http.server 8080
```

Then open:

```text
http://localhost:8080
```

## Browser support

Tested primarily in Chrome.

Clipboard behavior may require the page to be served over localhost or HTTPS, depending on browser security settings.

## Safety

PhantomStrike intentionally uses fake data.

Do not add real customer tokens, real secrets, real repository names, or live exploit commands to the demo.

The purpose is to explain risk clearly without creating operational attack capability.

## Future improvements

Possible next improvements:

- Cleaner guided demo mode
- Shorter prospect-facing attack chains
- More accurate BlueFlag policy descriptions
- Better policy-to-action mapping
- Narrator notes for sales engineering
- Exportable demo script
- Toggle between “technical buyer” and “executive buyer” views
- Clear labels for simulated versus product-sourced data

## Status

Prototype / internal demo aid.

Use for technical review and sales engineering feedback before broader distribution.

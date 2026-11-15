# Overkill AI Check

Find the lightest Claude model and effort level a task actually needs, and see how much of your Pro, Max or Ultra usage limit it takes compared with running it on Opus or Fable at high effort.

## Why

A lot of people run Claude Opus on high effort, or even Fable, for simple reading and writing: summarizing a PDF, cleaning up an email, pulling dates out of a contract. The answer comes out fine, but it's the same answer a lighter model would give, and it burns through plan limits much faster.

Claude subscriptions don't bill per message. They have a 5-hour session limit and a weekly limit, and heavier models, higher effort, long chats and connected tools all use those limits up faster. This tool makes that tradeoff visible before you hit send.

## What it does

1. You describe the task: your prompt, what you're trying to get done, how much material Claude reads, how much reasoning it takes, what a wrong answer would cost, and which connectors are on.
2. It recommends the lightest model and effort level that should still do the job well, with a one-line reason.
3. It shows how many times more Opus 5.5 high (and Fable 5.1 high) would use for the same task, plus a rough share of your plan's limit.

It also says so when a bigger model is the right call. The goal is the right model, not the cheapest one.

## How the recommendation works

The recommendation comes from fixed rules, not an AI call, so it costs nothing to run and gives the same answer every time. Each field adds points:

| Factor | Points |
|---|---|
| Type of work (read → long-running agent) | 0–10 |
| Material Claude reads | 0–3 |
| Reasoning needed | 0–6 |
| Cost of a wrong answer | 0–2 |
| Connectors and tools (browser use adds 1) | 0–3 |

| Total | Recommendation |
|---|---|
| 0–2 | Haiku, low effort |
| 3–5 | Sonnet, low |
| 6–8 | Sonnet, medium |
| 9–11 | Opus, medium |
| 12–15 | Opus, high |
| 16+ | Fable, high |

Two overrides: very large material never gets Haiku, and long-running agents never go below Opus. When a score sits near a cutoff, the page says so and suggests a test run. The page's "How this was scored" section shows the breakdown for every result.

## How usage is estimated

Anthropic doesn't publish exactly how large a session or week is, or how each model counts against it. The numbers here are estimates:

- Models are weighted by their relative API prices, since heavier models use limits faster.
- A Pro 5-hour session is assumed to be about 45 short messages on a mid-size model, based on Anthropic's published guidance. A Pro week is assumed to be about 15 sessions.
- Max is 5× Pro. Ultra is 10× Pro per week, with no 5-hour limit once verified.
- Thinking grows with effort, and coding or agent work counts several turns.

The comparisons between models ("Opus uses about 3× more here") are more reliable than the exact percentages. Prices, plan sizes and the session assumption live near the top of the script in `index.html` (`P`, `PLANS`, `PRO_SESSION`, `PRO_WEEK`) and are easy to update.

## Run it

It's a single static page with no build step and no dependencies to install. Open `index.html` in a browser.

### Deploy to Cloudflare Pages

1. In Cloudflare, create a Pages project and connect this repository.
2. Framework preset: **None**. Build command: leave empty. Build output directory: `/`.
3. Deploy.

Any static host works the same way.

## Privacy

- No accounts, analytics or tracking.
- Your prompt never leaves your browser.
- Your plan choice is remembered in your browser's local storage.
- Fonts load from Google Fonts.

## Roadmap

- ChatGPT models
- A Claude Code plugin that routes each request to the right model automatically
- Measured usage numbers from real readings, replacing the estimates

## License

[AGPL-3.0](LICENSE)

Overkill AI Check is an independent project and isn't affiliated with or endorsed by Anthropic. Claude is a trademark of Anthropic.

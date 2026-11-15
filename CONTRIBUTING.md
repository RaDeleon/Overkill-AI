# Contributing

Thanks for helping. The most useful changes are:

- **Prices and plan sizes.** These live near the top of the script in `index.html` (`P`, `PLANS`, `PRO_SESSION`, `PRO_WEEK`). If Anthropic changes them, update the values and mention the source in your pull request.
- **Scoring rules.** If a task gets a model that is clearly too small or too large, open an issue with the task, the recommendation you got, and what you expected.
- **Real usage readings.** A before and after session or weekly percentage for a specific model and task helps replace estimates with measurements.

## Ground rules

- Keep it one static HTML file with no build step.
- No analytics, trackers, API keys, or calls to AI services. The only outside request is Google Fonts.
- Keep help text in plain language for people who do not know what a token or an effort level is.

## Before you open a pull request

1. Open `index.html` in a browser and try each example button.
2. Check the result is unchanged for tasks you did not mean to affect.
3. The checks workflow verifies the page has no keys and no outside requests besides fonts.

Contributions are licensed under AGPL-3.0, the same as the project.

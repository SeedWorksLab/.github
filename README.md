# SeedWorks

**Website: [seedworkslab.github.io](https://seedworkslab.github.io)**

**Small, private, local-first apps for the things you do every day.**

SeedWorks is an independent app studio that builds focused tools for everyday life. We
believe good software should do one job well, keep your data on your own device, and
work whether or not you have a connection.

Every SeedWorks app is a React application built on a shared foundation: React Native
and Expo, TypeScript, Material Design 3, and a local SQLite database as the single
source of truth. Each app targets Android first, with Linux and web builds from the
same codebase.

The GitHub organization is [`SeedWorksLab`](https://github.com/SeedWorksLab).

---

## The apps

Each app is named after a fruit, and each one turns a vague intention into a
deliberate, repeatable habit. The family is still growing.

| App | What it does | Focus |
| --- | --- | --- |
| [Coconut](https://github.com/SeedWorksLab/Coconut) | Personal budget tracking built around a monthly allowance and a savings reserve. | Money |
| [Cherry](https://github.com/SeedWorksLab/Cherry) | A voice-first coffee brewing journal that learns how your recipe becomes a cup. | Coffee |
| [Banana](https://github.com/SeedWorksLab/Banana) | A weekly meal planner that turns your time, tastes and store deals into one shopping list. | Food |

All three are in active development. Each repository contains its own product
specification, release plan and setup instructions.

---

## Coconut — personal finance

Coconut models one person's financial life rather than a bank or an accounting
system. Every month you receive a monthly allowance, plan fixed expenses and flexible
budgets against it, and any amount left over flows automatically into a savings
reserve.

- **Monthly allowance and savings reserve** — plan the month, then let the surplus
  move into savings when the month closes.
- **Fixed and flexible budgets** — recurring bills with four estimation strategies,
  plus discretionary categories tracked against their plan.
- **Transactions and statistics** — unlimited entries, merchant-based budget
  suggestions, photo attachments, and spending trends over time.
- **Yearly subscriptions and one-off income** — spread an annual charge across the
  year, or add a bonus to a single month.
- **Optional shared expenses** — trusted users can share a space, split expenses
  per person, and generate a closing settlement report.
- **Optional sync** — bring your own Supabase project for multi-device sync and
  shared spaces. Off by default; the local database remains the source of truth.
- **Private by default** — local-first, no account required, no tracking, no
  advertising, and zero network calls unless you opt in.

Coconut stores money as integer cents, uses Expo SQLite for storage, and ships both a
web build and a Linux desktop build via Electron.

Read the full [Coconut README](https://github.com/SeedWorksLab/Coconut#readme).

---

## Cherry — coffee brewing

Cherry is a personal coffee journal, not a social network or a cloud service. You
plan a brew, talk through it while you make it, record how it tasted, and the app
gradually learns how dose, water, temperature, grind and pour structure affect the
result in the cup.

- **Plan, brew, tasted** — three linked stages of a single record.
- **Voice-first recording** — one appendable audio stream with phase markers, so
  logging takes less effort than not logging.
- **Cloud transcription and LLM extraction** — turn a spoken ramble into a structured
  record with full field provenance. Manual entry is always an equal alternative.
- **Bean catalogue and equipment** — roaster, origin, process, roast date, bag sizes,
  brewers, grinders and their settings.
- **Nine brewing methods** — V60, Chemex, Kalita, French press, AeroPress, Clever,
  cold brew, espresso and moka, each with a canonical recipe.
- **A deterministic recommender** — safe, curious and adventurous modes that know
  which variable to change next. The AI writes the narrative; it never decides the
  recommendation.
- **Learn tab** — grind and time sensitivity, your taste profile, and recurring
  mistakes.
- **Private by default** — local-first, no account, no analytics. AI calls go only to
  the provider you configure, with credentials stored on-device and excluded from
  backups.

Read the full [Cherry README](https://github.com/SeedWorksLab/Cherry#readme).

---

## Banana — meal planning

Banana plans your next week of meals around how much time you actually have and what
you specifically want to eat, then turns the plan into one organised shopping list
aware of current deals at Lidl, Hofer and Spar.

- **Plan, shop, cook, rate** — one weekly loop that improves the next plan.
- **Time-budget-aware planning** — per-weekday minutes, no-cook days and leftovers
  are first-class inputs to the deterministic planner.
- **Wishes honoured** — pin what you want to eat and the plan works around it.
- **Cook once, eat twice** — batch cooking and leftovers are scored objectives.
- **Deal-aware shopping list** — grouped by aisle, de-duplicated, with the cheapest
  matching offer flagged per ingredient.
- **Recipe library and pantry** — ingredients, steps, times, servings, tags and
  ratings, minus what you already have at home.
- **Preferences and allergies** — diet, allergies, dislikes, servings and a weekly
  budget, enforced in the service layer.
- **Optional AI planner** — the model proposes candidates and writes the narrative,
  while the deterministic planner still decides and never lets the AI write to the
  database.
- **Private by default** — local-first, no account, no analytics. The only outbound
  calls are your configured AI provider and public retailer offer pages.

Read the full [Banana README](https://github.com/SeedWorksLab/Banana#readme).

---

## What the family shares

The apps are separate products, but they are built from the same design philosophy
and much of the same architecture.

### Privacy comes first

- Your data lives in a local SQLite database on your device.
- There is no mandatory account, no backend, no analytics and no advertising.
- Network access is opt-in and explicit. When an app talks to a service, it is one
  you configured or a public page you enabled.
- Everything can be exported as a portable backup file and restored again.
- Secrets such as API keys are stored on-device only and stripped from backups.

### Offline is the default

Every app is fully usable without a connection. Manual entry is always as capable as
any assisted path, and AI features are enhancements, never requirements.

### Deterministic core, optional intelligence

Where an app uses an LLM, the model proposes and narrates. The decisions that affect
your data — budgets, recommendations, plans, splits — are made by deterministic,
testable service-layer logic.

### One shared technical foundation

| Layer | Choice |
| --- | --- |
| Framework | React Native via Expo SDK |
| Language | TypeScript in strict mode |
| Navigation | Expo Router |
| UI | React Native Paper, Material Design 3 |
| Storage | Expo SQLite on the device |
| Testing | Jest and jest-expo |
| Platforms | Android, Linux and web |
| Desktop | Electron and react-native-web |

Each app follows the same internal structure: `app` for screens, `database` for
schema and repositories, `models` for domain types, `services` for pure business
logic, and `theme` for Material 3 tokens.

---

## Development

Every repository uses the same core commands:

```bash
npm install        # install dependencies
npm run start      # start the Expo dev server
npm run android    # run on an Android emulator or device
npm run web        # run the web build
npm test           # run unit tests
npm run typecheck  # TypeScript check
npm run lint       # lint the code
```

Most apps expect Node.js 22+ and Android SDK API 29 or newer. Check the README of the
individual repository for exact prerequisites, release scripts and additional
commands.

---

## What comes next

SeedWorks is bigger than three apps. New fruits are already being planted, each one
aimed at a different everyday routine, and each one carrying the same promises:
private by default, offline-first, and deliberately simple.

Watch this organization, or follow the [Coconut](https://github.com/SeedWorksLab/Coconut),
[Cherry](https://github.com/SeedWorksLab/Cherry) and
[Banana](https://github.com/SeedWorksLab/Banana) repositories to see what grows next.

---

## License

The SeedWorks apps are released under the GNU Affero General Public License v3.0
unless a repository states otherwise. See the `LICENSE` file in each repository
for details.

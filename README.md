<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://static.openfoodfacts.org/images/logos/off-logo-horizontal-dark.png?refresh_github_cache=1">
  <source media="(prefers-color-scheme: light)" srcset="https://static.openfoodfacts.org/images/logos/off-logo-horizontal-light.png?refresh_github_cache=1">
  <img height="48" src="https://static.openfoodfacts.org/images/logos/off-logo-horizontal-light.svg">
</picture>
<br>

# Open Food Facts Explorer: the modern JS frontend to Open Food Facts

## Warning
- Please ask assignment before starting to code. First asking, first assigned. We have enough issues for everyone. Please open a matching issue and get consensus before raising PRs.
- DO NOT create a bug and its PR at the same time. Create the issue first and ask to be assigned.
- Do not try to race other contributors to solving an issue. Try something else, or try collaborating or helping one another on solving it.
- DO NOT jump to implement an open issue before an agreement is reached on the design.
- LINT your PRs before sending them pnpm
- Please mention GenAI tool you used if you used it (Copilot in an IDE, Copilot Workspace, Gemini…)

## Design
- [![Sketch](https://img.shields.io/badge/Sketch-%23F24E1E.svg?logo=sketch&logoColor=white) Trying to create a digital twin of openfoodfacts-explorer](https://www.figma.com/design/pgWZAEX1ZoTt0f7Azek4AV/Open-Food-Facts-Explorer-(next-gen-frontend)?node-id=1-53&t=XfEkgmUsvs6qiKr9-0)

## Features

- Uses the [official Open Food Facts NodeJS SDK](https://github.com/openfoodfacts/openfoodfacts-nodejs)
- Basic editing
- Product page display, including Knowledge Panels support
- Search
- Login support (simple login)
- Folksonomy Engine Support

## Roadmap

- Image editing
- Image upload
- Support for [Open Prices](https://prices.openfoodfacts.org/)
- Support for [Search-A-Licious](https://search.openfoodfacts.org/docs) (including facets)

## Developing

This project uses pnpm. If you have corepack enabled, you should be able to directly use `pnpm` commands. Otherwise, you can install pnpm with `npm install -g pnpm`.

First, install dependencies:

```bash
pnpm install
```

### Environment Variables Setup

Before running the project, set up the environment variables:

```bash
cp .env.example .env
```

Edit the `.env` file as needed to configure your development environment.

Then start the development server:

```bash
pnpm run dev

# or start the server and open the app in a new browser tab
pnpm run dev -- --open
```

## Building

To create a production version of your app:

```bash
pnpm run build
```

You can preview the production build with `pnpm run preview`.

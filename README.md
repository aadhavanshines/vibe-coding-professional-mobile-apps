# Vibe Coding Professional Mobile Apps: the Code

The code for the book *Vibe Coding Professional Mobile Apps* by Aadhavan Muthurengan: four professional-quality mobile apps for Android and iOS, and a bonus streaming app for Android TV, built with Claude Code, Expo SDK 58 and React Native.

| App | What it is | Folder |
| --- | --- | --- |
| **Platter** | Food delivery: discovery, dish customization, coupons, payment, live tracking on a map | `apps/platter` |
| **Cartly** | Online store: search, filters, variants, save for later, checkout, order tracking, returns | `apps/cartly` |
| **Lumo** | Social photos: stories, double-tap like, comments, explore, profiles, chat | `apps/lumo` |
| **Minutely** | 10-minute grocery: instant ADD steppers, category rail, countdown delivery | `apps/minutely` |
| **Reelhouse** | Android TV streaming: hero billboard, rows, Top 10, live sports, player, TV guide | `tv` |

The four phone apps share a design system (`packages/ui`), an API client with React Query hooks (`packages/api`) and one local backend (`server`: Hono, SQLite, JWT and Server-Sent Events for live order tracking). Screenshots of every screen are in each app's `screenshots/` folder.

All people, restaurants, products, shops and titles are fictional. The apps are original works; they don't copy any company's app, name or branding.

## Run it

You need Node.js 22.13 or later (Node 24 works too); `.nvmrc` selects 22.

```
npm install
npm run server                      # the API on http://localhost:4000
npm run web -w apps/platter         # or cartly, lumo, minutely
```

Sign in with phone **9876543210** and code **123456**.

For a phone or emulator, use `npm run start -w apps/platter` (or `android`, `ios`). On the Android emulator, set `EXPO_PUBLIC_API_URL=http://10.0.2.2:4000`. Chapter 2 of the book walks through setup.

### Reelhouse TV

`tv/` is a separate project, because it uses `react-native-tvos` as its React Native:

```
cd tv
npm install
npm run web                          # arrow keys, Enter and Escape act as the remote
EXPO_TV=1 npx expo prebuild --platform android --clean   # then: npx expo run:android
```

## Check it

```
npm run check            # TypeScript, ESLint and every test (Jest in the apps and packages, Vitest in the server)
cd tv && npm run check   # the TV app
```

The same checks run on every push in GitHub Actions.

## How it was built

Everything here was built by recorded Claude Code sessions. The exact prompts are in `sessions/`, in order, and `CLAUDE.md`, `docs/PRD.md` and `docs/DESIGN.md` are the project guide, product requirements and design spec those sessions worked from. The book explains each session, what it got right, and what review found.

## License

MIT, see `LICENSE`. The 3D illustrations are Microsoft Fluent Emoji 3D artwork, also MIT-licensed.

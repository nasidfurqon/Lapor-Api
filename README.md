# sv

Everything you need to build a Svelte project, powered by [`sv`](https://github.com/sveltejs/cli).

## Creating a project

If you're seeing this, you've probably already done this step. Congrats!

```sh
# create a new project
npx sv create my-app
```

To recreate this project with the same configuration:

```sh
# recreate this project
bun x sv@1.4.0 create --template minimal --types ts --add prettier eslint playwright="demo:yes" tailwindcss="plugins:typography,forms" --install bun mobile
```

## Adding features

Add features to your project with `sv add`:

```sh
npx sv add
```

For example, to add Tailwind CSS:

```sh
npx sv add tailwindcss
```

## Developing

Once you've created a project and installed dependencies with `npm install` (or `pnpm install` or `yarn`), start a development server:

```sh
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

To create a production version of your app:

```sh
npm run build
```

You can preview the production build with `npm run preview`.

> To deploy your app, you may need to install an [adapter](https://svelte.dev/docs/kit/adapters) for your target environment.

## Android (Capacitor)

The app builds as a static SPA in `dist`, matching `webDir` in `capacitor.config.ts`.
Build the web app before syncing it to Android:

```sh
bun run build
bunx cap sync android
bunx cap open android
```

Run `bunx cap add android` only once when the `android` directory does not exist.
After changing the web app, run the build and sync commands again, then run the
app from Android Studio on an emulator or connected device.

Capacitor 8 requires Android Studio 2025.2.1 or newer and Android SDK 36.
Use Android Studio's bundled JDK (Java 21 or newer) as the Gradle JDK; this
project's native dependencies target Java 21.

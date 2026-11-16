# Lapor Api research starter

This archive is a **documentation starter**, not an executable application. Create SvelteKit first, install Spec Kit and Capacitor, then copy `CLAUDE.md` and `docs/` to the repository root.

## Windows PowerShell — initial project
```powershell
npx sv create lapor-api
cd lapor-api
npm install
git init
npm run check
npm run build
uv tool install specify-cli
specify version
specify init --here --integration claude --script ps
```

Review changes and commit. Use `--force` for Spec Kit only after backing up/committing if the nonempty directory warning requests it.

## Android setup after configuring static adapter
```powershell
npm install -D @sveltejs/adapter-static
npm install @capacitor/core
npm install -D @capacitor/cli
npx cap init
npm install @capacitor/android
npm run build
npx cap add android
npx cap sync android
npx cap open android
```

Adjust `svelte.config.js` to adapter-static with pages/assets build and fallback 200.html; set `src/routes/+layout.ts` to `export const ssr = false;`. Ensure `capacitor.config.ts` webDir is `build`.

## First Claude session
```powershell
claude
```
In Claude chat, review `CLAUDE.md`, then invoke `/speckit-constitution` and later `/speckit-specify`. Obtain human review of ICONIX models before implementation.

Official docs: https://github.github.com/spec-kit/quickstart.html ; https://github.github.com/spec-kit/integrations/claude.html ; https://svelte.dev/docs/kit/adapter-static ; https://capacitorjs.com/docs/android

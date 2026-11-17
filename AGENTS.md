# Facebetter documentation

Mintlify docs for the Facebetter realtime beauty SDK.

## Structure

- `docs.json` — site config, navigation, i18n
- English pages at repo root (`intro/`, `android/`, …)
- Localized pages under `zh/`, `ja/`, `ko/`, `es/`, `pt-BR/` with the same tree
- Languages: en (default), zh, ja, ko, es, pt-BR
- Top tabs: **SDK Docs** / **Effect Creator** (贴纸制作) / **OBS Plugin** (OBS 插件) / **Edit Plugins** (剪辑插件：Final Cut Pro + After Effects 占位)
- Platforms live in sidebar groups under SDK Docs
- Images in `images/`

## Source of truth for content migration

Original VitePress marketing site lives in `../fb-platform/website/` (en/zh). SDK docs have been migrated here.

HarmonyOS docs were intentionally not migrated (hidden in the old site).

## Writing notes

对外客户文档规范（禁止暴露实现细节）：`.cursor/rules/customer-docs.mdc`，完整流程见 `.cursor/skills/facebetter-customer-docs/SKILL.md`。

- Prefer Mintlify components: `Tip`, `Warning`, `Note`, `Frame`, `Card`, `CardGroup`
- Link marketing/dashboard pages with absolute `https://facebetter.net/...` URLs
- Keep platform guides self-contained: quick-start → implement → errors → API
- Reshape / makeup / whitening / smoothing enums live in `intro/makeup.mdx` (and `zh/intro/makeup.mdx`). Platform API pages link there instead of duplicating tables.
- Supported SDK platforms: iOS, Android, Web, macOS, Windows, Linux (officially **Ubuntu 22.04+**; keep the platform name Linux, clarify Ubuntu in requirements). No Flutter / HarmonyOS docs. Expo is a prebuild sample at `expo/quick-start` (Android + iOS SDKs). Do not file it under Web. This site documents **SDK 2.0 only**. Do not describe 1.x APIs (`setBeautyParam`, `licenseJson`, `registerFilter`, `ProcessMode`, `FBBeautyEffectEngine` singleton).
- Version placeholders: **2.0.0**. Changelog: `intro/release-note.mdx`（六语）+ GitHub `pixpark/facebetter-sdk` Release，见 `.cursor/rules/release-notes.mdc`
- Favicon: 换图标必须**改文件名 + 同步改 `docs.json` 的 `favicon` 字段**（如 `favicon-v2.png` / `favicon-v3.png`）。Mintlify 生成的图标 URL 与 ETag 固定不变，原地覆盖 `favicon.png` 不会让浏览器更新——老访客会一直拿到 304 缓存里的旧图。保留 `favicon.png` 作为原始文件与 `/favicon.png` 直链。

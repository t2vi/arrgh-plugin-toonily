# arrgh-plugin-toonily

[Toonily](https://toonily.com) source plugin for [*ARRgh](https://github.com/t2vi/arrgh) —
manhwa (search, chapter list, page images). Cloudflare-protected — requires CloakBrowser.

Split from the arrgh monorepo's `plugins/toonily/` (spec 031 phase C), built from
[arrgh-plugin-template](https://github.com/t2vi/arrgh-plugin-template).

```bash
npm install
npm test            # contract + parser tests
npm run typecheck
npm run build       # → dist/toonily.js + dist/toonily.js.sha256
```

## Try it in a running *ARRgh

```bash
npm run build
docker cp dist/toonily.js <plugin-host container>:/community-bundles/
```

For a local dev stack, copy it to `plugin-host/community-bundles/` in the arrgh checkout.

## Release

1. Bump `version` in `package.json` and commit.
2. Tag and push it: `git tag v1.2.3 && git push origin v1.2.3`.
3. The **Release** workflow checks the tag matches `package.json`, runs the tests, builds, and
   publishes a GitHub Release with `toonily.js`, `toonily.js.sha256` and `catalog-entry.json`.
4. Open a PR on [t2vi/arrgh](https://github.com/t2vi/arrgh) updating `toonily`'s entry in
   `plugin-index/index.json`. Once merged, *ARRgh admins see **Update** in Settings. The download
   is sha256-checked before it loads.

## License

GPL-3.0, same as *ARRgh.

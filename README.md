# lightning4plebs

**Understand Lightning. From the specification, not the marketing.**

**Live site: https://hotpixelgroup.github.io/lightning4plebs/**

This repository contains **no source code**. It is a publishing target.

lightning4plebs and [bitcoin4plebs](https://github.com/hotpixelgroup/bitcoin4plebs)
are one codebase built twice: the same quest engine, the same design system,
the same verification discipline, with a build-time flag choosing which
curriculum and which brand. GitHub Pages serves one site per repository,
which is the only reason this repository exists.

The workflow here checks out
[hotpixelgroup/bitcoin4plebs](https://github.com/hotpixelgroup/bitcoin4plebs),
builds it with `VITE_SITE=lightning`, and deploys the result. Because the
source repository is public, that needs no tokens and no deploy keys.

## Where to actually go

- **Issues, pull requests and all source**: [hotpixelgroup/bitcoin4plebs](https://github.com/hotpixelgroup/bitcoin4plebs)
- **The Lightning quests**: `packages/quests/src/lib/quest-ln-*.ts`
- **The cryptography**: `packages/lightning-logic` — secp256k1, ChaCha20,
  BOLT-3 key derivation, BOLT-11 and the BOLT-4 sphinx onion, written from
  scratch with no dependencies and checked in CI against the Lightning
  specification's own published test vectors.

## Reproduce this build yourself

```sh
git clone https://github.com/hotpixelgroup/bitcoin4plebs.git
cd bitcoin4plebs && npm ci
VITE_SITE=lightning VITE_BASE=/lightning4plebs/ npx nx build web
```

Then compare `apps/web/dist-lightning/` against what this site actually
serves. Asset filenames are content-hashed, so verifying `index.html`
transitively pins the bundles it references.

## License

[MIT](https://github.com/hotpixelgroup/bitcoin4plebs/blob/main/LICENSE) for
the site's code. Specification excerpts © the Lightning RFC authors,
CC-BY 4.0. Node source © the LND authors, MIT License.

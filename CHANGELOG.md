# @capacitor/assets

## 4.0.0

### Major Changes

- 52eb67e: Upgrade sharp from 0.32.6 to ^0.35.5 and raise the Node floor to >=20.9.0.

  sharp 0.32 installed its native libvips binary through an `install` script. npm 12
  blocks that script by default, leaving sharp on disk but unable to load, so
  `npx @capacitor/assets generate` failed at require time. sharp 0.35 has no install
  script and resolves platform binaries through optional dependencies instead.

  This also clears three high-severity advisories inherited through sharp:
  GHSA-f88m-g3jw-g9cj (libvips), GHSA-rgj7-g3m4-5g8c (libheif) and
  GHSA-wq5f-xc86-pv6w (librsvg).

  Breaking: `engines.node` is now `>=20.9.0`, matching sharp's own floor. Capacitor's
  CLI already requires a newer Node than this, so supported setups are unaffected.

  Generated assets are unchanged in format, dimensions, channel count and colourspace.
  Pixel values differ by at most 2/255 in antialiased edges, from the newer libvips
  (8.18.7) and its image encoders. Larger raw differences exist only in the RGB
  channels of fully transparent pixels, which are never rendered.

### Minor Changes

- f1b68e8: Moved @capacitor/cli to Test dependencies

### Patch Changes

- 52eb67e: Declare `@ionic/cli-framework-output` as a runtime dependency.

  `src/util/log.ts` and `src/util/cli.ts` import it directly, but it was never listed
  in `dependencies`. It happened to be installed because `@capacitor/cli` depended on
  it. Once `@capacitor/cli` moved to `devDependencies`, nothing pulled it into a
  consumer's tree, and `capacitor-assets` failed at startup with
  `Cannot find module '@ionic/cli-framework-output'`.

## 3.0.4

### Patch Changes

- 5f42c57: fix sharp vulnerability by bumping patch version

## 3.0.3

### Patch Changes

- 3c5ecbe: Fix the path discovered for Angular and Vue project when --pwa option used

## 3.0.1

### Patch Changes

- 2c19107: fix: properly configure the single 1024x1024 iOS icon

## 3.0.0

### Major Changes

- 99a87f4: Only generate 1024x1024 for iOS icons for xcode 14 compatibility

### Patch Changes

- c5138af: Fix critical dependency issues and update Cap Cli dependency

## 2.0.4

### Patch Changes

- Fix Android drawable issue

## 2.0.3

### Patch Changes

- General all iOS sub-icons from main icon

## 2.0.2

### Patch Changes

- Android non-density asset generation

## 2.0.1

### Patch Changes

- Android launcher padding #424

## 2.0.0

### Major Changes

- Fixed icon generation issue on iOS and normalized argument format"

## 1.0.14

### Patch Changes

- Fixed android legacy icon sizes

## 1.0.13

### Patch Changes

- Added logoSplashScale and logoTargetWidth to Android

## 1.0.12

### Patch Changes

- Fixed PWA icon source path

## 1.0.11

### Patch Changes

- Added flags to support custom iOS and Android folders

## 1.0.10

### Patch Changes

- Support loading icon.png for easy mode

## 1.0.9

### Patch Changes

- Fixed iOS and Android logo generation

## 1.0.8

### Patch Changes

- Add --logoSplashTargetWidth and --logoSplashScale

## 1.0.7

### Patch Changes

- Fixed icon backgrounds for iOS

## 1.0.6

### Patch Changes

- Fixed Contents.json for iOS icons

## 1.0.5

### Patch Changes

- Fixed iOS Assets

## 1.0.4

### Patch Changes

- Fixed iOS asset generation #325

## 1.0.3

### Patch Changes

- Fixed iOS image sizes

## 1.0.2

### Patch Changes

- Updated Trapeze library and better project root handling

## 1.0.1

### Patch Changes

- Moved to Trapeze

# NodeCG Bundler

## What is it?

NodeCG-Bundler is a wrapper around Vite that makes it super easy to bundle your NodeCG bundles.

## Installation

```bash
# npm
npm install --save-dev nodecg-bundler
# or yarn
yarn add --dev nodecg-bundler
```

## File Structure

---

The file structure of a NodeCG bundle compiled by **nodecg-bundler** is by default:

```bash
src/
| dashboard/
|   index.html # Entry Point
|   ...        # JS, CSS, Images
| extension/
|   index.ts   # Entry Point
|   ...
| graphics/
|   index.html # Entry Point
|   ...
package.json
```

## Usage

In your package.json file, add the following to your scripts section:

```json
"scripts": {
  "dev": "nodecg-bundler watch",
  "build": "nodecg-bundler build"
}
```

## Command Options

You also have the option to _specify_ the folders to watch and build:

```bash
nodecg-bundler [watch|build] [options]

options:
  -e, --extension
  -d, --dashboard
  -g, --graphics
```

With no options, nodecg-bundler will select all folders.

You can combine all options to pick and choose what you want to build.

Examples:

- `nodecg-bundler build -e -d` will build the extension and the dashboard. (equivalent to `nodecg-bundler build -ed` and `nodecg-bundler build --extension -dashboard`)

- `nodecg-bundler build -E` is the negation of -e, so it will build everything except the extension. (equivalent to `nodecg-bundler build -dg`)

## Configuration

Configuration is the same as with Vite. The catch is, however, that you must place a _vite.config.[js/ts]_ file for each dashboard/graphics/extension directory.

The file structure looks like this:

```bash
src/
  dashboard/
    vite.config.ts
    index.ts
    ...
  graphics/
    vite.config.ts
    index.ts
    ...
  extension/
    vite.config.ts
    index.ts
    ...
```

## References

- [Vite](https://vitejs.dev)
- [Create Vite](https://vite.dev/guide/create-vite)
- [NodeCG CLI](https://github.com/nodecg/nodecg-cli)

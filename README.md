# Totum

## Overview

This library lets you compile a URL (https://, ethereum://, and more) into a THREE.js app representing it, written against the Metaversefile API. 

You can use this library to translate your avatars, models, NFTs, web pages (and more) into a collection of `import()`-able little web apps that interoperate with each other.

Totum is intended to be driven by a server framework (like vite.js/rollup.js), and game engine client (like Webaverse) to provide a complete immersive world (or metaverse) to the user.

It is easy to define your own data types and token interpretations by writing your own app template. If you would like to support a new file format or Ethereum Token, we would appreciate a PR.

Although this library does not provide game engine facilities, the API is designed to be easy to hook into game engines, and to be easy to drive using AIs like OpenAI's Codex.

---


Totum is composed of two major parts:


## API



API part exposes `setAPI` a dynamic routine that can be used to set the methods which can be then used by loaded modules/apps. API is based on [Singleton Design Pattern](https://en.wikipedia.org/wiki/Singleton_pattern)


## Usage `setAPI`

```js

	metaversefile.setApi({
		async load() =>{}

		async import() =>{}

		useApp() =>{}

		.
		.
		.
		can be anything

	})

```

### Inputs 
* object with key/value pairs can be anything even an async/Promise based function.

### Returns 
* Based on the methods used in setAPI

### Example Usage


#### Initialisation

```js
    
    import metaversefile from 'metaversefile';

    metaversefile.setApi({
        helloWorld() =>{
          return 'Hello World'
        }
    })

```

#### Usage in other modules


```js
    
    import metaversefile from 'metaversefile';

    metaversefile.helloWorld()

```


---

## Rollup.JS

Totum also provides a [Rollup.JS](https://rollupjs.org/) plugin located under `plugins/rollup.js` that provides transformation, loading and resolution based on the different module/asset loaders registered in totum.

### Supported Loaders by totum/rollup.js 

* `VRM`
* `VOX`
* `JS`
* `SCN`
* `IMAGE`
* `HTML`
* `GLB`
* `GIF`
* `Relative/Absolute URL`


### Motivations for loaders

- A system which takes any URL (or token) and manifests it as an object in a 3D MMO
- Totum transmutes data on the backend, serving composable little WASM+JS apps your browser can import()
- Object description language (`.metaversefile`) to declare game presentation. Sword? Wearable loot? Pet is aggro? Think CSS/JSON for the metaverse.
- Totum works completely permissionlessly. It provides a virtual lens into data, and you control the lens.
- Totum supports declaring per-object components, which can have gameplay effects
- Pure open source web tech
- Moddable; make your metaverse look and work the way you want
- Totum integrates into game engines, which provide the game.
- Totum works with 2D ($1K jpg) and 3D ($15K fbx) assets.
- Totum accepts PRs to improve the resolution of the metaverse
- It's called Totum because it snaps together your objects into a total experience

---
## Architecture

### Flow Diagram

![Totum diagram 02](https://user-images.githubusercontent.com/51108458/144339720-354aa56d-aa61-4e96-b49c-bf9e652d1f48.png)



---

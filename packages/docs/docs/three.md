---
image: /generated/articles-docs-three.png
id: three
title: "@remotion/three"
sidebar_label: Overview
---

import Tabs from "@theme/Tabs";
import TabItem from "@theme/TabItem";
import { ThreeDPlayer } from "../components/3DPhonePlayer.tsx";

is a package for integrating [React Three Fiber](https://github.com/pmndrs/react-three-fiber) with Remotion.

- [`<ThreeCanvas />`](/docs/three-canvas) will allow you to use `useCurrentFrame()` and other Remotion hooks within a R3F Canvas. Animations are now not inside a `useFrame()` hook, but directly rendered into the markup.

- [`useVideoTexture()`](/docs/use-video-texture) allows you to use a Remotion [`<Video />`](/docs/video) as a texture map.

These are the only two APIs provided - for everything else you can use the standard [React Three Fiber](https://github.com/pmndrs/react-three-fiber) APIs.

## Starter template

Check out [remotion-template-three](https://github.com/remotion-dev/template-three), a minimal boilerplate for Remotion and React Three Fiber. It is a template repository, you can click "Use this template" on the GitHub repo to get started.

<ThreeDPlayer />

The template features a 3D phone with a video inside which you can effortlessly swap out. Just as easily, you can change properties like the color, size, thickness, corner radius of the phone.

The template serves as a soft introduction on how to use `<ThreeCanvas />` and `useVideoTexture()`. You can easily delete everything inside the canvas to start working on a different idea.

## Installation

<Tabs
defaultValue="npm"
values={[
{ label: 'npm', value: 'npm', },
{ label: 'yarn', value: 'yarn', },
{ label: 'pnpm', value: 'pnpm', },
]
}>
<TabItem value="npm">

```bash
npm i three @react-three/fiber @remotion/three @types/three
```

  </TabItem>

  <TabItem value="yarn">

```bash
yarn add three @react-three/fiber @remotion/three @types/three
```

  </TabItem>
  <TabItem value="pnpm">

```bash
pnpm i three @react-three/fiber @remotion/three @types/three
```

  </TabItem>
</Tabs>

You are now set up and can render a [`<ThreeCanvas />`](/docs/three-canvas) in your project.

## Note on `<Sequence>`

A [`<Sequence>`](/docs/sequence) by default will return a `<div>` component, which is not allowed inside a `<ThreeCanvas>`. To avoid an error, pass `layout="none"` to `<Sequence>`.

## Note on server-side rendering

Three.JS does not render with the default OpenGL renderer - we recommend to set it to `angle`. The config file of new projects includes by default:

```ts twoslash
import { Config } from "remotion";

Config.setChromiumOpenGlRenderer("angle");
```

Since the config file does not apply to server-side rendering, you need to explicitly add

```json
"chromiumOptions": {
  "gl": "angle"
}
```

to server-side rendering APIs like [`renderMedia()`](/docs/renderer/render-media), [`renderFrames()`](/docs/renderer/render-frames), [`getCompositions()`](/docs/renderer/get-compositions) and [`renderMediaOnLambda()`](/docs/lambda/rendermediaonlambda).

## Thanks

A big thanks to [Björn Zeutzheim](https://github.com/olee) for researching and discovering the techniques needed for React Three Fiber integration and for doing the initial implementation of the @remotion/three APIs.

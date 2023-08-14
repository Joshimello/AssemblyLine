<script lang="ts">
  import { Canvas } from '@threlte/core'
  import Scene from './Scene.svelte'
  import Gui from './Gui.svelte'
</script>

<Gui/>

<Canvas
  rendererParameters={{
    powerPreference: 'high-performance',
    antialias: false,
    stencil: false,
    depth: false,
  }}>
  <Scene />
</Canvas>
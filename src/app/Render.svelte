<script lang="ts">
  import { useThrelte, useRender } from '@threlte/core'
  import {
    EffectComposer,
    EffectPass,
    RenderPass,
    SMAAEffect,
    SMAAPreset,
    BloomEffect,
    KernelSize
  } from 'postprocessing'

  const { scene, renderer, camera, size } = useThrelte()

  const composer = new EffectComposer(renderer)

  const setupEffectComposer = (camera) => {
    composer.removeAllPasses()
    composer.addPass(new RenderPass(scene, camera))
    composer.addPass(new EffectPass(camera, new BloomEffect({
      intensity: 1,
      luminanceThreshold: 0.15,
      height: 512,
      width: 512,
      luminanceSmoothing: 0.08,
      mipmapBlur: true,
      kernelSize: KernelSize.MEDIUM
    })))
    composer.addPass(new EffectPass(camera, new SMAAEffect({
      preset: SMAAPreset.LOW
    })))
  }

  $: setupEffectComposer($camera)
  $: composer.setSize($size.width, $size.height)

  useRender((_, delta) => {
    composer.render(delta)
  })
</script>
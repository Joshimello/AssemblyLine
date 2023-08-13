<script>
  import { onMount } from 'svelte'
  import { tweened } from 'svelte/motion'
  import { quadInOut } from 'svelte/easing'
  import { T } from '@threlte/core'

  const route = [
    [0, 0, 0],
    [1, 0, 0],
    [1, 0, 1],
    [0, 0, 1]
  ]

  let cur = 0

  let pos = tweened(route[cur], {
    duration: 500,
    easing: quadInOut
  })

  onMount(() => {
    const interval = setInterval(() => {
      cur = (cur + 1) % route.length
      pos.set(route[cur])
    }, 500)

    return () => {
      clearInterval(interval)
    }
  })
</script>

<T.Mesh position={$pos}>
  <T.BoxGeometry/>
  <T.MeshStandardMaterial/>
</T.Mesh>
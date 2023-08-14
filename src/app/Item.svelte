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

  let rPos = tweened(route[cur], {
    duration: 500,
    easing: quadInOut
  })

  export let position = [0, 0, 0]

  $: aPos = [
    $rPos[0] + position[0],
    $rPos[1] + position[1],
    $rPos[2] + position[2]
  ]

  onMount(() => {
    const interval = setInterval(() => {
      cur = (cur + 1) % route.length
      rPos.set(route[cur])
    }, 500)

    return () => {
      clearInterval(interval)
    }
  })
</script>

<T.Mesh position={aPos}>
  <T.BoxGeometry/>
  <T.MeshStandardMaterial/>
</T.Mesh>
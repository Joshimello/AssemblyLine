<script lang="ts">
  import { T } from '@threlte/core'
  import { OrbitControls, Grid, Environment } from '@threlte/extras'

  import Render from './Render.svelte'
  import Item from './Item.svelte'
</script>

<Item/>

<Grid
  position={[0.5, -0.5, 0.5]}
  infiniteGrid={true}
  fadeDistance={50}
  cellColor={'#777777'}
  cellThickness={1}
  sectionSize={0}
/>

<T.DirectionalLight
  args={[0xfff0dd, 1]}
  position={[10, 10, 0]}
/>

<Environment
  path="./"
  files="kloofendal_43d_clear_puresky_1k.hdr"
/>

<T.PerspectiveCamera
  makeDefault
  position={[5, 5, 5]}
  on:create={({ ref }) => {
    ref.lookAt(0, 0, 0)
  }}>
  <OrbitControls/>
</T.PerspectiveCamera>

<Render/>
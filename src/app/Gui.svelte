<script>
  import { board } from './stores'

  let i = 0, j = 0
  const add = () => {
    $board[i++][j++] = 'I'
  }
</script>

<div class="absolute bottom-0 w-full box-border p-2">
  <div class="bg-gray/50 w-full rounded-full box-border p-2">
    <button class="bg-white h-20 w-20 rounded-full border-0 outline-0" on:click={add}>
      Block
    </button>
  </div>
</div>
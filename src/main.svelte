<script>
  import App from './app/App.svelte'
</script>

<div>
  <App/>
</div>

<style>
  :global(body, html) {
    margin: 0;
    padding: 0;
  }

  div {
    position: absolute;
    height: 100%;
    width: 100%;
  }
</style>
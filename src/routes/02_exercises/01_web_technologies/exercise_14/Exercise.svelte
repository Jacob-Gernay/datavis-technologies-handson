<script>
  let current = "";
</script>

<button
  class="btn btn-secondary {current === 'messi' ? 'myClass' : ''}"
  on:click={() => (current = "messi")}>
    Messi
</button>

<button
  class="btn btn-secondary {current === 'ronaldo' ? 'myClass' : ''}"
  on:click={() => (current = "ronaldo")}>
    Ronaldo
</button>

<button
  class="btn btn-secondary {current === 'neymar' ? 'myClass' : ''}"
  on:click={() => (current = "neymar")}>
    Neymar
</button>

<style>
  button.myClass {
    background-color: crimson;
  }
</style>

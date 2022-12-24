<script>
  export let filter = "all";
</script>

<div id="filter-buttons">
  <button on:click={() => (filter = "all")}>All</button>
  <button on:click={() => (filter = "active")}>Active</button>
  <button on:click={() => (filter = "completed")}>Completed</button>
</div>

<style>
  #filter-buttons {
    margin-top: 15px;
    margin-bottom: 30px;
    text-align: center;
  }
</style>

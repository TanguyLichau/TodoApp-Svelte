<script>
  export let todolists;

  $: completedLength = todolists.filter(
    (todo) => todo.isChecked === true
  ).length;
</script>

{#if todolists.length === 0}
  <h2>You have no todos at the moment</h2>
{:else if completedLength === todolists.length}
  <h2>You have completed all of your current todos !</h2>
{:else}
  <h2>
    There are {completedLength} completed todos out of {todolists.length}
  </h2>
{/if}

<style>
  h2 {
    text-align: center;
  }
</style>

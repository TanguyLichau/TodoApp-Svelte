<script>
  export let todolists;
</script>

<h2>
  There are {todolists.filter((todo) => todo.isChecked === true).length} completed
  todos out of {todolists.length}
</h2>

<style>
  h2 {
    text-align: center;
  }
</style>

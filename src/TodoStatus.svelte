<script>
  export let todolists;

  const completedTodos = () => {
    return todolists.filter((todo) => todo.isChecked === true).length;
  };
</script>

<h2>There are {completedTodos} completed todos out of {todolists.length}</h2>

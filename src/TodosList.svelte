<script>
  import Todo from "./Todo.svelte";
  import AddTodo from "./AddTodo.svelte";
  let todolists = [];

  const deleteATodo = (event) => {
    todolists.splice(event.detail.todoIndex, 1);
    todolists = todolists;
  };

  const addATodo = (event) => {
    todolists = [...todolists, event.detail.value];
  };
</script>

<AddTodo on:add={addATodo} />
{#each todolists as todoValue, indx}
  <Todo on:delete={deleteATodo} {todoValue} {indx} />
{/each}

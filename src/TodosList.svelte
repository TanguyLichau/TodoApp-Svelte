<script>
  import Todo from "./Todo.svelte";
  import AddTodo from "./AddTodo.svelte";
  let todolists = [];

  const deleteATodo = (event) => {
    const index = todolists.indexOf(event.detail.todoValue);
    todolists.splice(index, 1);
    todolists = todolists;
  };

  const addATodo = (event) => {
    todolists = [...todolists, event.detail.value];
  };
</script>

<AddTodo on:add={addATodo} />
{#each todolists as todoValue}
  <Todo on:delete={deleteATodo} {todoValue} />
{/each}

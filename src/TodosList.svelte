<script>
  import Todo from "./Todo.svelte";
  import AddTodo from "./AddTodo.svelte";
  let todolists = [];

  const deleteATodo = (event) => {
    todolists.splice(event.detail.todoIndex, 1);
    todolists = todolists;
  };

  const addATodo = (event) => {
    todolists = [...todolists, { ...event.detail }];
  };

  // A FAIRE : AJOUT FILTRE CHECK PAS CHECK / AJOUT EDIT / AJOUT CHECK ALL ET REMOVE ALL CHECK
</script>

<AddTodo on:add={addATodo} />
{#each todolists as todo, indx}
  <Todo
    on:delete={deleteATodo}
    todoValue={todo.todoValue}
    isChecked={todo.isChecked}
    {indx}
  />
{/each}

<script>
  import Todo from "./Todo.svelte";
  import AddTodo from "./AddTodo.svelte";
  import MoreActions from "./MoreActions.svelte";
  let todolists = [];
  let isAllChecked = false;

  const deleteATodo = (event) => {
    todolists.splice(event.detail.todoIndex, 1);
    todolists = todolists;
  };

  const addATodo = (event) => {
    todolists = [...todolists, { ...event.detail }];
  };

  const checkAllTodos = (event) => {
    //console.log(JSON.stringify(todolists));
    if (!isAllChecked) {
      todolists.forEach((item, index) => {
        if (item.isChecked === false) {
          todolists[index].isChecked = true;
        }
      });
      todolists = todolists;
      isAllChecked = true;
    } else {
      todolists.forEach((item, index) => {
        todolists[index].isChecked = false;
      });
      todolists = todolists;
      isAllChecked = false;
    }
  };
  const deleteAllTodos = (event) => {};
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
<MoreActions on:checkAll={checkAllTodos} on:deleteAll={deleteAllTodos} />

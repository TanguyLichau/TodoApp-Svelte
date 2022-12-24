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

  const checkAllTodos = () => {
    if (!isAllChecked) {
      todolists.forEach((element) => {
        if (!element.isChecked) {
          element.isChecked = true;
        }
      });
      isAllChecked = true;
    } else {
      todolists.forEach((element) => {
        element.isChecked = false;
      });
      isAllChecked = false;
    }
    todolists = todolists;
  };
  const deleteAllTodos = () => {
    console.log(JSON.stringify(todolists));
    todolists = todolists.filter(function (a) {
      return a.isChecked !== true;
    });
  };

  const updateCheck = (currentTodo) => {
    currentTodo.isChecked = !currentTodo.isChecked;
  };
  // A FAIRE : AJOUT FILTRE CHECK PAS CHECK / AJOUT EDIT / AJOUT CHECK ALL ET REMOVE ALL CHECK
</script>

<AddTodo on:add={addATodo} />
{#each todolists as todo, indx}
  <Todo
    on:delete={deleteATodo}
    on:check={updateCheck(todo)}
    todoValue={todo.todoValue}
    isChecked={todo.isChecked}
    {indx}
  />
{/each}
<MoreActions on:checkAll={checkAllTodos} on:deleteAll={deleteAllTodos} />

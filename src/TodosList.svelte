<script>
  import Todo from "./Todo.svelte";
  import AddTodo from "./AddTodo.svelte";
  import MoreActions from "./MoreActions.svelte";
  import FilterTodos from "./FilterTodos.svelte";
  import TodoStatus from "./TodoStatus.svelte";
  let todolists = [];
  let isAllChecked = false;
  let filter = "all";

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
    todolists = todolists.filter(function (a) {
      return a.isChecked !== true;
    });
    isAllChecked = false;
  };

  const updateCheck = (currentTodo) => {
    currentTodo.isChecked = !currentTodo.isChecked;
    todolists = todolists;
  };

  const filterTodos = (filter, todos) =>
    filter === "active"
      ? todos.filter((t) => !t.isChecked)
      : filter === "completed"
      ? todos.filter((t) => t.isChecked)
      : todos;
  // A FAIRE : AJOUT EDIT / STYLE / AJOUT NOMBRE DE TODO COMPLETES
</script>

<AddTodo on:add={addATodo} />
<TodoStatus {todolists} />
<FilterTodos bind:filter />
{#each filterTodos(filter, todolists) as todo, indx}
  <Todo
    on:delete={deleteATodo}
    on:check={updateCheck(todo)}
    bind:todoValue={todo.todoValue}
    isChecked={todo.isChecked}
    {indx}
  />
{/each}
<MoreActions on:checkAll={checkAllTodos} on:deleteAll={deleteAllTodos} />

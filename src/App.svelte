<script>
  let todos = [
    {
      text: "Get breakfasst",
      checked: false,
    },
    {
      text: "Get lunch",
      checked: false,
    },
  ];

  let newText = "";

  const addTodo = (e) => {
    e.preventDefault();
    todos = [...todos, { text: newText, checked: false }];

    newText = "";
  };

  function deleteTodo(index) {
    todos.splice(index, 1);

    todos = todos;
  }
</script>

<h1>Todo</h1>

<form on:submit={addTodo}>
  <input placeholder="Add todo" bind:value={newText} />
  <button type="submit">Add</button>
</form>

{#each todos as todo, index}
  <div class:status={todo.checked}>
    <input type="checkbox" bind:checked={todo.checked} />
    {todo.text}
    <button on:click={() => deleteTodo(index)}>❌</button>
  </div>
{/each}

<style>
  div.status {
    text-decoration: line-through;
  }
</style>

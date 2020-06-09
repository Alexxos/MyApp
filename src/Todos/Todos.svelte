<script>
  import TodoItem from "../Todos/TodoItem.svelte";
  import Textinput from "../UI/TextInput.svelte";
  import Button from "../UI/Button.svelte";
  import Modal from "../UI/Modal.svelte";

  export let todos = [];
  let id;
  let task = "";
  let dateDue = "";
  let comments = "";
  let showModal = false;

  function addTodo() {
    let newTodo = {
      id: Math.random(),
      task: task,
      dateDue: dateDue,
      comments: comments,
      id: Math.random()
    };
    todos = [...todos, newTodo];
  }

  function deleteTodo(event) {
    console.log(event.detail);
    let idx = event.detail;
    console.log(idx);
    todos = todos.filter(function(todo) {
      return todo.id !== idx;
    });
  }
</script>

<style>
  .grid-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  gap: 1px 1px;
  grid-template-areas: ". inputs inputs ." "Tasks Tasks Tasks Tasks" "Tasks Tasks Tasks Tasks";
}

.inputs { grid-area: inputs; 
 display: flex;
    flex-direction: column;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    width: 25rem;
    border-radius: 5px;
    color: white;
    padding: 0.5rem;
    background: teal;
    height: 16rem;}
.Tasks { grid-area: Tasks; }

  .form {
   
  }
  button {
    margin-left: 2rem;
    background-color: #cf0056;
    width: 20rem;
    color: white;
    border-radius: 5px;
  }

  #first-button {
    margin-top: 5rem;
  }
</style>

<div class="grid-container">
  <form class="inputs">
    <input type="text" bind:value={task} placeholder="Task to do" />
    <input type="text" bind:value={dateDue} placeholder="Due Date" />
    <textarea rows={2} bind:value={comments} placeholder="comments" />
    <button on:click|preventDefault={addTodo}>Add Todo</button>
  </form>
  <div class='Tasks'>
  {#each todos as todo, index (todo.id)}
  <TodoItem
    task={todo.task}
    dateDue={todo.dateDue}
    comments={todo.comments}
    id={todo.id}
    on:delete={deleteTodo} />
{/each}
</div>
</div>



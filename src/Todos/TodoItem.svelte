<script>
  import Button from "../UI/Button.svelte";
  import {createEventDispatcher} from 'svelte';

  export let task;
  export let dateDue;
  export let comments;
  export let id;
  export let checked = false;

  const dispatch = createEventDispatcher();

  function deleteTodo() {
   dispatch('delete', id);
  }
</script>

<style>
  .card {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    padding-left: 1rem;
    justify-content: center;
    width: 20rem;
    height: 17rem;
    border-radius: 5px;
    color: white;
    background: teal;
    margin-left: 1rem;
  }
  button {
    margin-left: 2rem;
    background-color: #cf0056;
    width: 15rem;
    color: white;
    border-radius: 5px;
  }
  .done {
    
    background: rgb(226, 64, 14);
  }
</style>

<div class="card" class:done={checked}>
  <h1>{task}</h1>
  <h2>Date Due :{dateDue}</h2>
  <h2>Comments :{comments}</h2>
  <button  on:click={deleteTodo}>Delete</button>
  Done?
  <input type="checkbox" bind:checked/>
</div>

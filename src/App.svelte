<script>
  import Navbar from "./UI/NavBar.svelte";
  import Todos from "./Todos/Todos.svelte";
  import Timer from "./Timer/Timer.svelte";
  import Habits from "./Habits/Habits.svelte";
  import Calendar from "./Calendar/Calendar.svelte";

  let current = "Todos";
  let todos = [
    {
      task: "Finish TodoList",
      dateDue: "This week",
      comments: "You can do it",
      id: Math.random()
    },
    {
      task: "Be nice to dog",
      dateDue: "Now",
      comments: "Has to happens",
      id: Math.random()
    }
  ];
</script>

<style>
  button {
   
    width: 20%;
    border-color: steelblue;
    margin-left: 2rem;
    border-radius: 5px;
    padding: 0.5rem 1rem;
    background: transparent;
    color: #cf0056;
    box-shadow: none;
  }
  .active {
    background-color: #cf0056;
    color:white;
    box-shadow: 1px 1px 8px rgba(77, 51, 51, 0.26);
  }
    #margin-top {
    margin-top: 5rem;
    height: 5rem;
  }
</style>

<Navbar />

<div id="margin-top">
  <button
    class:active={current === 'Todos'}
    on:click={() => (current = 'Todos')}>
    Todos
  </button>
  <button
    caption="Timer"
    class:active={current === 'Timer'}
    on:click={() => (current = 'Timer')}>
    Timer
  </button>
  <button
    caption="Habits"
    class:active={current === 'Habits'}
    on:click={() => (current = 'Habits')}>
    Habits
  </button>
  <button
    caption="Calendar"
    class:active={current === 'Calendar'}
    on:click={() => (current = 'Calendar')}>
    Calendar
  </button>
</div>

{#if current === 'Todos'}
<Todos {todos} />
{:else if current === 'Timer'}
<Timer />
{:else if current === 'Habits'}
<Habits />
{:else}
<Calendar />
{/if}
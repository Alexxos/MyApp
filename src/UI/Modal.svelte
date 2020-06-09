<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  let id;
  let task = "";
  let dateDue = "";
  let comments = "";
  let done;
  let showModal = false;
  let agreed = false;

</script>

<style>
  .backdrop {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, 0.75);
    z-index: 10;
  }

  .modal {
    padding: 1rem;
    position: fixed;
    top: 30vh;
    left: 10%;
    width: 80%;
    max-height: 45vh;
    background: white;
    border-radius: 5px;
    z-index: 100;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    overflow: scroll;
  }

  header {
    border-bottom: 1px solid #ccc;
  }
</style>

<div class="backdrop" on:click={()=> dispatch('cancel')}/>
  <div class="modal">
    <slot name='Habits'/>
    <button on:click={()=> agreed = true}>Agree</button>
    <button on:click={()=> dispatch('close')} disabled={!agreed}>Close </button>
</div>



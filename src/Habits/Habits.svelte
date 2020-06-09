<script>
  import Modal from "../UI/Modal.svelte";

  let showModal = false;
  let closable = true;
  let toggle = false;
  
</script>

<h1>Habits</h1>

<button on:click={() => (showModal = true)}>ShowModal</button>

{#if showModal}
  <Modal
    on:cancel={() => (showModal = false)}
    on:close={() => (showModal = false)}
  >
    <div slot="Habits">
      <label for="">New habits?</label>
      <input type="text" />
      
      {#if toggle}
        <button on:click={() => (toggle = false)}>Toggle off</button>
      {:else}
        <button on:click={() => (toggle = true)}>Toggle on</button>
      {/if}
    </div>
  </Modal>
{/if}

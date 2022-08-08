<script>
  export let showTodoModal;
</script>

<style>
  .backdrop {
    width: 100%;
    height: 100%;
    position: fixed;
    z-index: 100;
    top: 0;
    left: 0;
    background-color: rgba(0,0,0, 0.8);
  }
  .modal {
    padding: 10px;
    border-radius: 10px;
    max-width: 400px;
    margin: 10% auto;
    text-align: center;
    background: white;
  }
</style>

{#if showTodoModal}
<div class="backdrop" on:click|self>
  <div class="modal">
    <slot />
  </div>
</div>
{/if}
<script>
  export let showSlotModal = false;
</script>

<style>
  /* your styles go here */
  .backdrop {
    background: rgba(0,0,0,0.8);
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
  .modal {
    padding: 10px;
    margin: 10% auto;
    border-radius: 10px;
    background: white;
    max-width: 400px;
  }
</style>

{#if (showSlotModal)}
<div class="backdrop" on:click|self>
  <div class="modal">
      <slot />
  </div>
</div>
{/if}


<script>
  let num = 25;
</script>

<style>
  /* your styles go here */
</style>

<!-- markup (zero or more items) goes here -->
{#if num > 20}
  <p>Greater than 20</p>
{:else if num > 5}
  <p>Greater than 5</p>
{:else}
  <p>Not greater than 5</p>
{/if}

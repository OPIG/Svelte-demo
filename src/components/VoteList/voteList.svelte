<script>
  import Detail from './detail.svelte'

  export let data
</script>

  {#each data as voteItem}
    <Detail {voteItem} on:updateVote></Detail>
  {:else}
  <p>There is no data yet</p>

  {/each}
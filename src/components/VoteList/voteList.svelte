<script>
  import {fade, slide, scale} from 'svelte/transition'
  import {flip} from 'svelte/animate'
  import Detail from './detail.svelte'

  export let data
</script>

{#each data as voteItem (voteItem.id)}
  <div class='card-box' in:fade out:scale|local animate:flip={{duration: 500}}>
    <Detail {voteItem} on:updateVote on:handelDel></Detail>
  </div>
{:else}
  <p>Oops! There is no data yet</p>
{/each}

<style>
  .card-box {
    width: 20%;
  }
  p {
    text-align: center;
    width: 100%;
    font-weight: bold;
    font-size: 14px;
  }
</style>

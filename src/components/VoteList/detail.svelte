<script>
  import { createEventDispatcher } from 'svelte'
  const dispatch = createEventDispatcher()

  import Card from '../../shared/card.svelte'
  
  export let voteItem

  $: totalVote = voteItem.voteA + voteItem.voteB

  const handelVote = (option, id) => {
    dispatch('updateVote', {option,id})
  }

</script>

<Card>
  <div class="detail-content">
    <h3>{ voteItem.question }</h3>
    <p>Total votes: { totalVote }</p>
    <div class="answer" on:click={() => handelVote('a', voteItem.id)}>
      <span>{ voteItem.answerA } { voteItem.voteA }</span>
    </div>
    <div class="answer" on:click={() => handelVote('b', voteItem.id)}>
      <span>{ voteItem.answerB } { voteItem.voteB }</span>
    </div>
  </div>
</Card>

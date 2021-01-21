<script>
  import { tweened } from 'svelte/motion'
  import { createEventDispatcher } from 'svelte'
  const dispatch = createEventDispatcher()

  import Card from '../../shared/card.svelte'
  
  export let voteItem

  $: totalVote = voteItem.voteA + voteItem.voteB
  $: percentA = Math.floor(voteItem.voteA / totalVote * 100) || 0
  $: percentB = Math.floor(voteItem.voteB / totalVote * 100) || 0

  let tweenedA = tweened(0)
  let tweenedB = tweened(0)
  $: tweenedA.set(percentA)
  $: tweenedB.set(percentB)

  const handelVote = (option, id) => {
    dispatch('updateVote', {option,id})
  }

  const handelDel = (id) => {
    dispatch('handelDel', id)
  }

</script>

<Card>
  <div class="detail-content">
    <h3>{ voteItem.question }</h3>
    <p>Total votes: { totalVote }</p>
    <div class="answer" on:click={() => handelVote('a', voteItem.id)}>
      <div class="percent percent-a" style='width:{$tweenedA}%'></div>
      <span>{ voteItem.answerA } { voteItem.voteA }</span>
    </div>
    <div class="answer" on:click={() => handelVote('b', voteItem.id)}>
      <div class="percent percent-b" style='width:{$tweenedB}%'></div>
      <span>{ voteItem.answerB } { voteItem.voteB }</span>
    </div>
  </div>
  <div class='close-btn' slot='del' on:click={handelDel(voteItem.id)}>X</div>
</Card>

<style>
  h3{
    margin: 0 auto;
    color: #555;
  }
  p{
    margin-top: 6px;
    font-size: 14px;
    color: #aaa;
    margin-bottom: 30px;
  }

  .answer {
    background: #fafafa;
    cursor: pointer;
    margin: 10px auto;
    position: relative;
  }

  .answer:hover {
    opacity: .6;
  }

  span {
    display: inline-block;
    padding: 10px 20px;
  }

  .percent {
    height: 100%;
    position: absolute;
    box-sizing: border-box;
  }

  .percent-a {
    border-left: 4px solid #900;
    background: rgba(217,27,66,.2)
  }

  .percent-b {
    border-left: 4px solid #ff0;
    background: rgba(69,296,150, .2);
  }

  .close-btn {
    position: absolute;
    top: 6px;
    right: 6px;
    width: 10px;
    height: 10px;
    font-size: 14px;
    cursor: pointer;
  }
</style>

<script>
  import Nav from './shared/nav.svelte'
  import Foot from './shared/foot.svelte'
  import VoteList from './components/VoteList/voteList.svelte'

  let data = [
    {
      id: 0,
      question: 'this is a demo question',
      answerA: 'Answer A',
      answerB: 'Answer B',
      voteA: 0,
      voteB: 0,
    },
    {
      id: 1,
      question: 'this is a question',
      answerA: 'Answer A',
      answerB: 'Answer B',
      voteA: 10,
      voteB: 0,
    }
]

  const handelUpdateVote = (e) => {
    const {id, option} = e.detail
    const copyData = [...data]
    const findData = copyData.find((item) => item.id === id)
    if(option === 'a') {
      findData.voteA++
    } else if (option === 'b') {
      findData.voteB++
    }

    data = copyData

  }
</script>

<main>
  <Nav></Nav>
  <section class="content">
    <VoteList {data} on:updateVote={handelUpdateVote}></VoteList>
  </section>
  <Foot></Foot>
</main>

<style>
  main{
    /* display: flex;
    flex-direction: column;
    align-items: space-between;
    width: 100%;
    height: 100%;
    min-height: 800px; */
  }

  .content {
    display: flex;
    flex-flow: row wrap;
    justify-content: flex-start;
  }
</style>
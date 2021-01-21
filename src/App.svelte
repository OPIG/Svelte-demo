<script>
  import Nav from './shared/nav.svelte'
  import Foot from './shared/foot.svelte'
  import VoteList from './components/VoteList/voteList.svelte'
  import Tab from './shared/tabs.svelte'
  import AddVoteItem from './components/VoteList/addVoteItem.svelte'

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

  const navItems = ['Show Items', 'Add Item']
  let currentNav = navItems[0]
  const hancelNavClick = (e) => {
   currentNav = e.detail
  }

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

  const addItem = (e) => {
    const newData = e.detail
    console.log(newData);
    data = [newData, ...data]
    currentNav =  navItems[0]
  }

  const delItem = (e) => {
    const copyData = [...data]
    let newData = copyData.filter(item => item.id !== e.detail)
    data = newData

  }
</script>

<main>
  <Nav></Nav>
  <section class="content">
    <Tab {navItems} {currentNav} on:clickNav={hancelNavClick}></Tab>
    {#if currentNav === navItems[0]}
      <VoteList {data} on:updateVote={handelUpdateVote} on:handelDel={delItem}></VoteList>
    {:else if currentNav == navItems[1]}
      <AddVoteItem on:handelSubmit={addItem}/>
    {/if}
    
  </section>
  <Foot></Foot>
</main>

<style>
  .content {
    display: flex;
    flex-flow: row wrap;
    justify-content: flex-start;
  }
</style>
<script>
  import {createEventDispatcher} from 'svelte'
  import Button from '../../shared/Button.svelte'
  const dispatch = createEventDispatcher()

  const fieldData = ['Question', 'AnswerA', 'AnswerB']
  let formData = {question: '', answerA:'', answerB:''}
  let error = {question: '', answerA:'', answerB:''}
  let valid = false
  const handelSubmit = () => {
    valid = true

    if(formData.question.trim().length < 5) {
      valid = false;
      error.question = 'Question must be at leath 5 characters long'
    } else {
      error.question = ''
    }

    if(formData.answerA.trim().length < 5) {
      valid = false;
      error.answerA = 'answerA must be at leath 5 characters long'
    } else {
      error.answerA = ''
    }

    if(formData.answerB.trim().length < 5) {
      valid = false;
      error.answerB = 'answerB must be at leath 5 characters long'
    } else {
      error.answerB = ''
    }

    if (valid) {
      let data = {...formData, voteA: 0, voteB: 0, id: Math.floor(Math.random()*1000)}
      dispatch('handelSubmit', data)
    }
  }

</script>

<form on:submit|preventDefault={handelSubmit}>
  <p>
    <label for="question-name">Question Name:</label>
    <input type="text" id="question-name" bind:value={formData.question} placeholder='please input {fieldData[0]}'>
    <span class='error'>{ error.question }</span>
  </p>

  <p>
    <label for="answer-a">Answer A:</label>
    <input type="text" id="answer-a" bind:value={formData.answerA} placeholder='please input {fieldData[1]}'>
    <span class='error'>{ error.answerA }</span>
  </p>

  <p>
    <label for="answer-b">Question Name:</label>
    <input type="text" id="answer-b" bind:value={formData.answerB} placeholder='please input {fieldData[2]}'>
    <span class='error'>{ error.answerB }</span>
  </p>

  <p>
    <Button >Add Item</Button>
  </p>
</form>

<style>
  form {
    width: 400px;
    margin: 0px auto;
  }

  p {
    text-align: center;
  }
   
  label {
    font-weight: bold;
    font-size: 14px;
    line-height: 30px;
    text-align: left;
  }

  input {
    width: 100%;
    height: 40px;
    border-radius: 6px;
  }
  .error {
    display: inline-block;
    width: 100%;
    color: #900;
    text-align: left;
  }
</style>
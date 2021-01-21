<div class="card">
  <slot></slot>
  <slot class="del-close" name='del'></slot>
</div>

<style>
  .card{
    background: #fff;
    padding: 20px;
    border-radius: 6px;
    box-shadow: 0 2px 4px rgba(0,0,0,.1);
    margin: 10px;
    position: relative;
  }
  .card:hover{
    box-shadow: 0 2px 8px rgba(0,0,0,.4);
  }
</style>
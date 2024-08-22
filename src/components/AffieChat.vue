<template>
  <div>
    <div class="p-4">
      <input type="checkbox" class="toggle" />
      <input type="checkbox" class="toggle toggle-primary" />
      <input type="checkbox" class="toggle toggle-secondary" />
      <input type="checkbox" class="toggle toggle-accent" />
      <br/>
      <input type="checkbox" class="checkbox" />
      <input type="checkbox" class="checkbox-primary checkbox" />
      <input type="checkbox" class="checkbox-secondary checkbox" />
      <input type="checkbox" class="checkbox-accent checkbox" />
      <br/>
      <input type="radio" name="radio" class="radio" />
      <input type="radio" name="radio" class="radio-primary radio" />
      <input type="radio" name="radio" class="radio-secondary radio" />
      <input type="radio" name="radio" class="radio-accent radio" />
    </div>
    <details class="dropdown">
      <summary class="btn m-1">open or close</summary>
      <ul class="menu dropdown-content bg-base-100 rounded-box z-[1] w-52 p-2 shadow">
        <li><a>Item 1</a></li>
        <li><a>Item 2</a></li>
      </ul>
    </details>

    <div class="chat chat-start">
      <div class="chat-bubble">
        It's over Anakin,
        <br />
        I have the high ground.
      </div>
    </div>
    <div class="chat chat-end">
      <div class="chat-bubble">You underestimate my power!</div>
    </div>

  </div>
</template>

<script setup lang="ts">


</script>

<style scoped lang="postcss">
</style>

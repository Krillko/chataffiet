<template>
  <div class="w-1/2">
    <div v-for="(msg, index) in chat" :key="index">
      <div class="chat"
      :class="{
        'chat-start': msg.part === 'user',
        'chat-end': msg.part === 'affie',
      }">
        <div class="chat-image avatar">
          <div class="w-24 rounded-full">
            <img
              v-if="msg.part === 'user'"
              src="/icons/user.jpg"
            >
            <img v-else :src="msg.img">
          </div>
        </div>
        <div class="chat-header text-xs">
          <span v-if="msg.part === 'user'">Du:</span>
          <span v-if="msg.part === 'affie'">Affie:</span>
        </div>
        <div class="chat-bubble">{{ msg.message }}</div>
      </div>
    </div>
<!--    <div class="chat chat-start">
      <div class="chat-image avatar">
        <div class="w-10 rounded-full">
          <img
            alt="Tailwind CSS chat bubble component"
            src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" />
        </div>
      </div>
      <div class="chat-header">
        Obi-Wan Kenobi
        <time class="text-xs opacity-50">12:45</time>
      </div>
      <div class="chat-bubble">You were the Chosen One!</div>
      <div class="chat-footer opacity-50">Delivered</div>
    </div>-->
<!--
    <div class="chat chat-end">
      <div class="chat-image avatar">
        <div class="w-10 rounded-full">
          <img
            alt="Tailwind CSS chat bubble component"
            src="https://img.daisyui.com/images/stock/photo-1534528741775-53994a69daeb.webp" />
        </div>
      </div>
      <div class="chat-header">
        Anakin
        <time class="text-xs opacity-50">12:46</time>
      </div>
      <div class="chat-bubble">I hate you!</div>
      <div class="chat-footer opacity-50">Seen at 12:46</div>
    </div>
-->


    <label class="form-control w-full max-w-xs">
      <div class="label">
        <span class="label-text">Skriv till Affie</span>
      </div>
      <div class="flex"><input type="text" placeholder="Här alltså" class="input input-bordered w-full max-w-xs"
                                v-model="input" @keydown.enter="submitChat"/>
        <button class="btn btn-primary" @click="submitChat">&gt;</button>
      </div>
    </label>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

type Chat = {
  part: 'user' | 'affie';
  message: string;
  img: string;
}
const input = ref('')
const chat = ref<Chat[]>([])

const randn = () => {
  return Math.floor(Math.random() * 5) + 1;
}
const endSentence = () => {
  const rand = Math.random();
  if (rand < 0.25) return "";   // 50% chance
  else if (rand < 0.75) return "?";  // 25% chance
  else return "!";   // 25% chance
}

const submitChat = () => {
  chat.value.push({
    part: 'user',
    message: input.value,
    img: ''
  })
  input.value = ''
  setTimeout(()=> {
    chat.value.push({
      part: 'affie',
      message: '...',
      img: `/icons/${randn()}.jpg`
    })

    setTimeout(()=>{
      console.log(chat.value.length)
      console.log(chat.value)
      const index = chat.value.length - 1;
      chat.value[index] = {
        ...chat.value[index],
        message: "Mjau ".repeat(Math.floor(Math.random() * 5) + 1) + endSentence()
      }
    }, 1500)


  }, 250)

}

</script>

<style scoped lang="postcss">
</style>

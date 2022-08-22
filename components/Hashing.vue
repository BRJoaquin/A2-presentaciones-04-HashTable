<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps({
  text: {
    default: '',
  },
  text1: {
    default: '',
  },
  text2: {
    default: '',
  },
  text3: {
    default: '',
  },
})

const text = ref(props.text)
const text1 = ref(props.text1)
const text2 = ref(props.text2)
const text3 = ref(props.text3)



// sumatoria de los caracteres de un string
function hash1(text: string) : number {
  let sum = 0
  for (let i = 0; i < text.length; i++) {
    sum += text.charCodeAt(i)
  }
  return sum
}

// sumatoria de los caracteres de un string
function hash2(text: string) : number {
  let sum = 0
  for (let i = 0; i < text.length; i++) {
    sum += text.charCodeAt(i)  * (i + 1)
  }
  return sum
}

// https://cseweb.ucsd.edu/~kube/cls/100/Lectures/lec16/lec16-15.html
function hash3(text: string) : number {
  let sum = 0
  for (let i = 0; i < text.length; i++) {
    sum = sum * 31 + text.charCodeAt(i)
  }
  return sum
}

function hash() {
  text1.value = hash1(text.value).toString()
  text2.value = hash2(text.value).toString()
  text3.value = hash3(text.value).toString()

}


</script>

<template>
  <div flex="~" w="min">
    <input type="text" v-model="text" v-on:keyup="hash"/>
  </div>
  <br/>
  hash 1: {{ text1 }}
  <br/>
  <br/>
  hash 2: {{ text2 }}
  <br/>
  <br/>
  hash 3: {{ text3 }}
</template>

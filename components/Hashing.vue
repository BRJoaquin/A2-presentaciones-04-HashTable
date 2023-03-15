<script setup lang="ts">
import { ref } from 'vue'
import './Hashing.css'

const props = defineProps({
  text: {
    default: '',
  },
  bucektSize: {
    default: 10,
  },
  text1: {
    default: 0,
  },
  text2: {
    default: 0,
  },
  text3: {
    default: 0,
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
  text1.value = hash1(text.value)
  text2.value = hash2(text.value)
  text3.value = hash3(text.value)

}


</script>

<template>
  <div >
    Elemento (string)
    <input  class="input-hash" type="text" v-model="text" v-on:keyup="hash" placeholder="key"/>
    <br><br>
    Número de buckets
    <input class="input-hash" type="number"  v-model=bucektSize />
  </div>
  <br/>
  hash 1: {{ text1 }} 
  <br/>
  index 1: {{ text1 % bucektSize }}
  <br/>
  <br/>
  hash 2: {{ text2 }}
  <br/>
  index 2: {{ text2 % bucektSize }}
  <br/>
  <br/>
  hash 3: {{ text3 }}
  <br/>
  index 3: {{ text3 % bucektSize }}
</template>
<script setup lang="ts">
import { ref, watchEffect } from 'vue'

// Define las props
const props = defineProps({
    text: String,
    bucketSize: Number
})

// Refs para los valores reactivos
const text = ref(props.text || '')
const bucketSize = ref(props.bucketSize)
const computedHash1 = ref(0)
const computedHash2 = ref(0)
const computedHash3 = ref(0)
const index1 = ref(0)
const index2 = ref(0)
const index3 = ref(0)

// Reacciona a los cambios de las props inmediatamente
watchEffect(() => {
    computeHashes()
})

// sumatoria de los caracteres de un string
function hash1(text: string): number {
    let sum = 0
    for (let i = 0; i < text.length; i++) {
        sum += text.charCodeAt(i)
    }
    return sum
}

// sumatoria de los caracteres de un string
function hash2(text: string): number {
    let sum = 0
    for (let i = 0; i < text.length; i++) {
        sum += text.charCodeAt(i) * (i + 1)
    }
    return sum
}

// https://cseweb.ucsd.edu/~kube/cls/100/Lectures/lec16/lec16-15.html
function hash3(text: string): number {
    let sum = 0
    for (let i = 0; i < text.length; i++) {
        sum = sum * 31 + text.charCodeAt(i)
    }
    return sum
}


function computeHashes() {
    // Calcula y actualiza los valores hash y de índice
    computedHash1.value = hash1(text.value)
    computedHash2.value = hash2(text.value)
    computedHash3.value = hash3(text.value)

    index1.value = computedHash1.value % (bucketSize.value ?? 1)
    index2.value = computedHash2.value % (bucketSize.value ?? 1)
    index3.value = computedHash3.value % (bucketSize.value ?? 1)
}

</script>

<template>
    <div>
        Clave/Key (string)
        <input class="input-hash" type="text" v-model="text" @input="computeHashes" placeholder="key" />
        <br><br>
        Número de buckets
        <input class="input-hash" type="number" v-model.number="bucketSize" @input="computeHashes" />
    </div>
    <br />
    hash 1: {{ computedHash1 }}
    <br />
    index 1: {{ index1 }}
    <br />
    <br />
    hash 2: {{ computedHash2 }}
    <br />
    index 2: {{ index2 }}
    <br />
    <br />
    hash 3: {{ computedHash3 }}
    <br />
    index 3: {{ index3 }}
</template>
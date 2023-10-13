<template>
  <div>{{ userInfo }} | Repositories</div>
  <span>Fecha de nacimiento: {{ birthday }}</span>
  <div>
    <p>{{ text }}</p>
    <span>counter: {{ counter }}</span>
  </div>
  <div>
    <p>{{ fullName }}</p>
    <span>value: {{ obj.counter }}</span>
  </div>
  <button ref="btn">Click!!</button>
</template>
<script>
import { ref, toRefs, reactive, onMounted, computed, watch, inject } from 'vue'
export default {
  props: {
    user: {
      type: String,
      required: true
    },
    email: {
      type: String,
      required: true 
    }
  },
  // setup(props, context) {
  setup(props, context) {
    console.log(context)
    const btn = ref(null)
    const { user, email } = toRefs(props)
    const text = ref('')
    const counter = ref(0)
    const obj = reactive({ firstName: "Cristian", lastName: "Pisco", counter: 0 })
    const birthday = inject("birthday")

    text.value = "Esto es un ejemplo"
    setInterval(() => {
      counter.value++
      obj.counter++
    }, 1000)

    // watch(counter, (newValue, oldValue) => {
    //   console.log(`old: ${oldValue} - new: ${newValue}`)
    // })
    // watch(() => obj.counter, (newValue, oldValue) => {
    //   console.log(`obj counter old: ${oldValue} - new: ${newValue}`)
    // })
    watch(btn, (newValue) => {
      console.log(newValue)
    })

    const fullName = computed(() => {
      return `${obj.firstName} ${obj.lastName}`
    })
    const userInfo = computed(() => {
      return `${user.value} - ${email.value}`
    })
    // se puede colocar el toRefs a la variable que guarda el computed
    // toRefs(userInfo)

    onMounted(() => {
      console.log('mounted')
    })

    context.expose({
      fullName
    })

    return {
      text,
      counter,
      obj,
      fullName,
      userInfo,
      birthday,
      btn
    }
  }
}
</script>

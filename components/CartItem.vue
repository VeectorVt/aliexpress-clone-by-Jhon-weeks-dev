<template>
  <div>

  </div>
</template>

<script setup>
import { useUserStore } from '~/stores/user'

const userStore = useUserStore()
const props = defineProps(["product", 'selectedArray']);
const { product, selectedArray } = toRefs(props);

const emit = defineEmits(['selectedRadio'])

const isHover = ref(false)
const isSelected = ref(false)

const removeFromCart = () => {
  userStore.cart.forEach((prod, index) => {
    userStore.cart.splice(index, 1)
  })
}

watch(() => isSelected.value, (val) => {
  emit('selectedRadio', { id: product.value.id, val: val })
})


// Gusttanu
</script>

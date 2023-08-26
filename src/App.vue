<template>
  <div :id="$style.app">
    <h2>Input: {{ text }}</h2>
    <CastomInput :modelValue="text" @update:modelValue="text = $event" />
    <ApartmentsList :items="apartments">
      <template v-slot:title>New Title</template>
      <template v-slot:apartment="{ apartment }">
        <ApartmentsItem :key="apartment.id" :descr="apartment.descr" :rating="apartment.rating" :imgSrc="apartment.imgUrl"
          :price="apartment.price" @click="handleItemClick" />
      </template>
    </ApartmentsList>
  </div>
</template>

<script>
import ApartmentsList from './components/apartment/ApertmentsList.vue'
import ApartmentsItem from './components/apartment/ApartmentsItem.vue';
import apartments from './components/apartment/apartments'
import CastomInput from './components/shared/CustomInput'

export default {
  name: 'App',
  components: {
    ApartmentsList,
    ApartmentsItem,
    CastomInput
  },
  data() {
    return {
      text: '',
      apartments,
    }
  },
  methods: {
    handleItemClick() {
      console.log('item click');
    }
  }
}
</script>

<style module>
#app {
  font-family: Montserrat, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

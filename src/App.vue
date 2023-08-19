<template>
  <div :id="$style.app">
    <ApartmentsItem :rating="apartment.rating" :descr="apartment.descr" :price="apartment.price"
      imgSrc="https://grandstail.ru/assets/cache/Pic/user/images/noimage.jpg/05cc9918f9e7391e26ac979e8560f6a1.jpg" />
  </div>
</template>

<script>
import ApartmentsItem from './components/apartment/ApartmentsItem'

export default {
  name: 'App',
  components: {
    ApartmentsItem
  },
  data() {
    return {
      apartment: {
        id: "ljhbslhafbljHSBF;KJB",
        title: "lorem nskjnkjadnlk",
        descr: "Роскошные апартаменты в скайндинавском стиле с панорамным видом на реку и бесплатным Wi-Fi.",
        price: 2032,
        rating: 4.7,
        location: {
          city: "Sassnitz"
        },
        owner: {
          name: "Ellen",
          phone: "1234654",
          email: "ownermail@post.com"
        }
      }
    }
  },
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

<template>
  <div class="about">
    <div class="photo">
      <Loader v-if="imageLoading" absolute/>
      <img :src="image" alt="">
    </div>
    <div class="name">{{ name }}</div>
    <div>{{ email }}</div>
    <div>{{ blog }}</div>
  </div>
</template>

<script>
import Loader from '~/components/Loader'

export default {
  data(){
    return{
      imageLoading:true
    }
  },
  computed :{
    image(){
      return this.$store.state.about.image
    },
    name(){
      return this.$store.state.about.name  
    },
    email(){
      return this.$store.state.about.email  
    },
    blog(){
      return this.$store.state.about.blog  
    }
  },
  mounted(){
    this.init()
  },
  methods:{
    async init(){
      await this.$loadImage(this.image)
      this.imageLoading = false
    }
  }
}
</script>

<style lang="scss" scoped>
@import "~/scss/main.scss";

.about{text-align: center;padding-top:40px;font-size:20px;
  .photo{
    width:300px;height:300px;margin:40px auto 20px;border:10px solid $gray-300;border-radius:50%;box-sizing: border-box;background-color:$gray-200;position:relative;
    img{width:280px;border-radius:50%;}
  }
  .name{
    font-size:50px;font-weight:bold;font-family: 'Oswald', sans-serif;margin-bottom:20px;
  }
}
</style>
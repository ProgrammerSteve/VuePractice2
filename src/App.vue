<template>
  <h2>{{title}}</h2>
 <input type="text" ref="name"/>
 <button @click="handleClick">click me</button> 
   <p>Welcome...</p> 


 <teleport to=".modals" v-if="showModal">
  <Modal :header="header" :text="text" theme="sale" @close="toggleModal">
    <template v-slot:links>
      <a href="#">sign up now</a>
      <a href="#">more info</a>
    </template>
      <h1>Sign up for the Giveaway</h1>
      <p>Grab your ninja swag for half price!</p>
  </Modal>
</teleport>

 <teleport to=".modals" v-if="showModalTwo">
  <Modal :header="header" :text="text" @close="toggleModalTwo">
      <h1>Sign up to the newsletter</h1>
      <p>For updates and promo codes!</p>
  </Modal>
</teleport>

<button @click.alt="toggleModal">Open Modal (alt)</button>  
<button @click="toggleModalTwo">Open Modal Two</button>  
</template>

<script>
import Modal from './components/Modal.vue'
export default {
  name: 'App',
  data(){
    return{
      title:"My first Vue app :)",
      header:"Sign up for the Giveaway",
      text:"Grab your ninja swag for half price!",
      showModal:false,
      showModalTwo:false,
    }
  },
 
  methods:{
    handleClick(){
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus()
    },
    toggleModal(){
      this.showModal=!this.showModal
    },
    toggleModalTwo(){
      this.showModalTwo=!this.showModalTwo
    }
  },

  components:{
    Modal,
  }
}
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h2{
  padding-bottom:10px;
  border-bottom:1px solid #ddd;
  display: inline-block;
}
</style>

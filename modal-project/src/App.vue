<template>
  <!-- practice ---------------------------------  -->
  <!-- <div>
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <h1 class="red">{{ title }}</h1>
    <input type="text" ref="name" >
    <button @click="handleClick">submit</button>
  </div> -->
  <!-- practice ----------------------------------  -->
  {{ title }}
  <teleport to=".modals" v-if="showModal">
    <!-- *********************** CLICK EVENT MODIFIER *********************  -->
    <!-- <Model :data="data" @close="toggleModal" /> -->
    <!-- SLOTS EXAMPLE -----------------------  -->
    <Model @close="toggleModal">
      <h1>hey this is the example of slots</h1>
      <template v-slot:namedSlot>
        <p>hi this is me namedSlot</p>
      </template>
    </Model>
  </teleport>
   <div v-if="showModal2">
    <Model @close="toggleModal2">
      <h1>hey this is the example 2nd of slots</h1>
      <template v-slot:namedSlot>
        <p>hi this is me 2nd namedSlot</p>
      </template>
    </Model>
  </div>
  <br />
  <button @click="toggleModal">open modal</button>
  <button @click="toggleModal2">open model two</button>
</template>

<script>
import Model from "./components/Model.vue";
export default {
  name: "App",
  data() {
    return {
      title: "hello swostika! how are you",
      data: "swostika lamichhane",
      showModal: false,
      showModal2:false
    };
  },

  components: {
    Model,
},
  methods: {
    handleClick() {
      console.log(this.$refs.name.value);
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModal2(){
      this.showModal2= !this.showModal2
    }
  },
};
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
.red {
  color: red;
}
</style>

<!--<template>
  <div>
    <HelloWorld msg="Welcome to Your Vue.js App" /> 
    <h1 class="red">{{ title }}</h1>
    <input type="text" ref="name" >
    <button @click="handleClick">submit</button>
  </div>
</template> 

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  data() {
    return { title: "hello swostika! how are you" };
  },

  // components: {
  //   HelloWorld,
  // },
  methods: {
    handleClick() {
      console.log(this.$refs.name.value);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.red {
  color: red;
}
</style>-->

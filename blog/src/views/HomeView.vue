<template>
  <div>
    <h1>Home</h1>
    <div v-if="error" class="err">
      <h5>{{ error }}</h5>
    </div>
    <div v-if="posts.length">
      <PostList v-if="showpost" :posts="posts" />
    </div>
    <div v-else><p>Loading...</p></div>
    <button class="btn" @click="showpost = !showpost">toggle post</button><br />
    <button class="btn" @click="posts.pop()">delete post</button>
  </div>
</template>

<script>
import { ref } from "@vue/reactivity";
import PostList from "../components/PostList.vue";
import getPosts from "../composables/getPosts";
export default {
  name: "Home",
  setup() {
    const { posts, error, load } = getPosts();
    load();
    const showpost = ref(true);
    return { posts, showpost, error };
  },
  components: { PostList },
};
</script>

<style>
.btn{
  margin:8px 0px;
}
.err {
  color: red;
}
</style>
<!--  practice 1----------------------->

<!--<template>
  <div>
    <h2>REF</h2>
    <p>I am {{ obj1.name }}. My name is {{ obj1.age }}</p>
    <button @click="handleObj1">update obj1</button>
    <input type="text" placeholder="search" v-model="search" />
    <h2>Matching names:</h2>
    <div v-if="matching.length !== 0">
      <p v-for="name in matching" :key="name">{{ name }}</p>
    </div>
    <div v-else><p>no match found</p></div>
    <h2>REACTIVE</h2>
    <p>{{ obj2.name }}- {{ obj2.age }}</p>
    <button @click="handleObj2">update obj2</button>
    <button @click="handleWatch">stop watching</button>
  </div>
</template>

<script>
import { reactive, ref, computed, watch, watchEffect } from "vue";

export default {
  name: "HomeView",

  setup() {
    const obj1 = ref({
      name: "",
      age: null,
    });
    const names = ref(["swos", "kri", "abi", "riti", "suru", "asmi"]);
    const search = ref("");
    const stopwatch = watch(search, () => {
      console.log("watch function run");
    });
    const stopwatchEffect = watchEffect(() => {
      console.log("watch effect function run");
    });
    const handleWatch = () => {
      stopwatch();
      stopwatchEffect();
    };
    const matching = computed(() => {
      return names.value.filter((jj) => jj.includes(search.value));
    });
    const handleObj1 = () => {
      console.log(obj1.value.name);
      obj1.value.name = "swosti";
      obj1.value.age = 23;
    };
    const obj2 = reactive({
      name: "",
      age: null,
    });
    const handleObj2 = () => {
      console.log(obj1.name);
      obj2.name = "swosti";
      obj2.age = 23;
    };
    return {
      obj1,
      handleObj1,
      obj2,
      handleObj2,
      names,
      matching,
      search,
      handleWatch,
    };
  },
};
</script>

<style></style>-->
<!--  practice 1----------------------->
<!-- <template>
  <div class="home">
    <h1>home</h1>
    <p ref="demo">Hi! my name {{ name }} and age is {{ age }}</p>
    <button @click="handleClick">Click me</button>
    <button @click="age++">age++</button>
    <button @click="age--">age--</button>
    <input type="text" v-model="name" />
  </div>
</template>-->

<!-- <script>
@ is an alias to /src

import { ref } from "vue";

export default {
  name: "HomeView",
  setup() {
    console.log("setup");
    // without using ref===> (
    // let name = "seostika";
    // let age = 39;)<===
    let name = ref("");
    let age = ref();
    const handleClick=()=>{
      console.log(demo.value);
      // demo.value.innerHTML="hello"<---- without using ref
      name.value="swos"
      age.value=23
    }
    const demo = ref(null);
    return { name, age, demo, handleClick };
  },
  created() {
    console.log("created");
  },
  mounted() {
    console.log("mounted");
  },
};

</script> -->

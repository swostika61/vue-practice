<template>
  <div>
    <router-link :to="{ name: 'details', params: { id: post.id } }">
      <h3>{{ post.title }}</h3>
    </router-link>
    <p>{{ snippet }}</p>
    <span class="tag" v-for="tag in post.tags" :key="tag">#{{ tag }}</span>
  </div>
</template>

<script>
import { computed } from "@vue/runtime-core";
export default {
  props: ["post"],
  setup(props) {
    const snippet = computed(() => {
      return `${props.post.body.substring(0, 50)} .....`;
    });
    return { snippet };
  },
};
</script>

<style>
.tag {
  border-radius: 8px;
  background: #7e7d7b;
  padding: 4px 6px;
  margin: 10px 5px;
}
</style>

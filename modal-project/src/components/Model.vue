<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal">
      <!-- <p>welcome to {{ title }}</p>
      <h5>{{ data }}</h5> -->
      <!-- --------------- SLOTS EXAMPLE ---------------------- -->
     <div>
       <slot name="namedSlot"></slot>
     </div>
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: ["data"],
  data() {
    return { title: "modal page" };
  },
  methods:{
    closeModal(){
      this.$emit('close')
    }
  }
};
</script>

<style>
.backdrop {
  height: 100%;
  width: 100%;
  top:0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
}
.modal {
  width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: #fff;
  border-radius: 0.5rem;
}
</style>

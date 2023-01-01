<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <div class="card">
        <img v-if="gender === 'ชาย'" src="https://cdn-icons-png.flaticon.com/512/3750/3750011.png"/>
        <img v-else src="https://cdn-icons-png.flaticon.com/512/2995/2995633.png"/>
        <hr>
        <slot name="card-header"></slot>
        <slot name="card-content"></slot>
        <slot name="card-button"></slot>
    </div>
</template>

<script>
export default {
    name: "CardStudent",
    props:["gender"]
}
</script>

<style scoped>
.card {
  margin: 1rem 1rem;
  display: inline-block;
  font-size: 1.25rem;
  /* font-weight: bold; */
  background: orangered;
  padding: 2rem;
  color: #fff;
  border-radius: 25px;
}
img{
    width:100px;
    height: 100px;
}
</style>
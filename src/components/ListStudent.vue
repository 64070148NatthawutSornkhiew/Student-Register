<template>
  <div >
    <EachStudent
      v-for="(item, index) in student"
      :key="index"
      :name="item.name"
      :id="item.id"
      :branch="item.branch"
      :saka="item.saka"
      :gender="item.gender"
      :isVisible="item.isVisible"
      @del="removeData"
      @show="showDes"
    />
  </div>
</template>

<script>
import EachStudent from "./EachStudent.vue";
export default {
  name: "ListStudent",
  components: {
    EachStudent,
  },
  props: ["student"],
  methods:{
    removeData(id){
      this.$emit("delete", id)
    },
    showDes(id){
      this.$emit("showit", id)
    }
  }
};
</script>

<style scoped>



</style>

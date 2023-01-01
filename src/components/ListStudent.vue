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
      @del="removeData"
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
    }
  }
};
</script>

<style scoped>



</style>

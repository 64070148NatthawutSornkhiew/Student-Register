
<template>

    <CardStudent :gender="gender">
      <template v-slot:card-header>
        <p> {{ gender === "ชาย" ? "นาย" : "นาง" }}  {{ name }}</p>
        <p>รหัสนักศึกษา {{ id }}</p>
      </template>

      <template v-slot:card-content>
        <p>{{ branch }}</p>
        <p>{{ saka }}</p>
      </template>
      <template v-slot:card-button>
        <button @click="delData(id)">ลบข้อมูล</button>
      </template>

    </CardStudent>
</template>

<script>
import CardStudent from './CardStudent.vue'
export default {
  name : "EachStudent",
  components:{
    CardStudent
  },
  props: {
    name: {
      type: String,
    },
    id: {
      type: Number,
    },
    branch: {
      type: String,
    },
    saka:{
      type:String
    },
    gender:{
      type: String,
    }
    
  },
  methods:{
    delData(id){
      this.$emit("del", id)
      // console.log(id)

    }
  }
};
</script>

<style scoped>
  p{
    font-size: 1rem;
  }
  button{
    font:inherit;
    background: rgb(237, 195, 180);
    color:black;
    cursor: pointer;
    margin-top: 1rem ;
    padding: 0.25rem 2rem;
    border-radius: 15px;
    font-size: 1rem;
  }

</style>
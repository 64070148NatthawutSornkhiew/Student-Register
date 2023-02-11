<template>
  <div>
    <header>
      <h1>Student Registor</h1>
    </header>
    <FormComponent @save="addToList"></FormComponent>
    <section class="student-content" v-if="student.length > 0">
      <h2>ข้อมูลนักศึกษา</h2>
      <ListStudent
      :student="student"
       @delete="remove"
       @showit="show"
       ></ListStudent>
    </section>
  </div>
</template>

<script>
import FormComponent from "./components/FormComponent.vue";
import ListStudent from "./components/ListStudent.vue";
export default {
  name: "App",
  components: {
    FormComponent,
    ListStudent,
  },
  data() {
    return {
      student: [],
    
    };
  },
  methods: {
    addToList(data) {
      this.student.push(data);
    },
    remove(id){
      // console.log(id+"1");
      this.student = this.student.filter(item=>{
        return item.id !== id
      })
    },
    show(id){
      // console.log(id+ this.student.name)
      this.student = this.student.map((item)=>{
        if(item.id === id){
          return {...item,isVisible: !item.isVisible};
        }
        return item
      })
    }
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Slabo+27px&display=swap');
* {
  box-sizing: border-box;
}
body {
  margin: 0;
  font-family: 'Slabo 27px', serif;
}
header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  background-color: orangered;
  color: #fff;
  text-align: center;
}
.student-content {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}
.student-content h2 {
  padding-bottom: 0.5rem;
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: orangered;
  margin: 0 0 0.75rem 0;
}
</style>

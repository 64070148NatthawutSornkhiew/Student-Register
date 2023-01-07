<template>
  <CardStudent :gender="gender">
    <template v-slot:card-header>
      <h5>{{ gender === "ชาย" ? "นาย" : "นาง" }} {{ name }}</h5>
      <h5>{{ id }}</h5>
    </template>

    <template v-slot:card-content>
      <button class="btn-des" @click="showData(id)">
        {{ isVisible ? "ซ่อน" : "แสดง" }}รายละเอียด</button
      ><br />
      <transition name="fade">
        <div v-show="isVisible">
          <p>{{ branch }}</p>
          <p>{{ saka }}</p>
        </div>
      </transition>
    </template>

    <template v-slot:card-button>
      <button class="btn-remove" @click="delData(id)">Delete</button>
    </template>
  </CardStudent>
</template>

<script>
import CardStudent from "./CardStudent.vue";
export default {
  name: "EachStudent",
  components: {
    CardStudent,
  },
  props: {
    name: {
      type: String,
    },
    id: {
      type: Number,
      // default: 12345
    },
    branch: {
      type: String,
    },
    saka: {
      type: String,
    },
    gender: {
      type: String,
    },
    isVisible: {
      type: Boolean,
    },
  },
  methods: {
    delData(id) {
      this.$emit("del", id);
      // console.log(id)
    },
    showData(id) {
      this.$emit("show", id);
      // console.log(id)
    },
  },
};
</script>

<style scoped>
.fade-enter-from{
  opacity: 0;
}
.fade-enter-active {
    transition: all .3s linear;
  }

p,
h5 {
  margin: 0.5rem;
}
p {
  font-size: 0.85rem;
}
.btn-remove {
  font: inherit;
  background: rgb(237, 195, 180);
  color: black;
  cursor: pointer;
  margin-top: 0.5rem;
  padding: 0.25rem 2rem;
  border-radius: 15px;
  font-size: 1rem;
}
.btn-des {
  cursor: pointer;
  margin: 0 0 0.5rem 0.5rem;
  float: left;
  text-decoration: underline;
  border: none;
  background-color: transparent;
}
</style>

<template>
  <div class="dynamic-component">
    <h1>LocalStorage demo &emsp;&emsp;&emsp;</h1>
    <br />
    <button @click="listComponent" type="button" class="btn btn-success space">
      List Data
    </button>
    <button @click="addComponent" type="button" class="btn btn-primary">
      Add Data
    </button>
    <br />
    <br />

    <component
      :is="component"
      @eventDeleteData="eventDelData"
      @eventAddData="eventAddData"
      :listData="message"
    ></component>
  </div>
</template>

<script>
import ListData from "./listData.vue";
import AddData from "./addData.vue";
export default {
  components: { ListData, AddData },
  name: "DynamicComponent",
  data() {
    return {
      component: ListData,
      message: [],
    };
  },
  computed: {
    currentComponent() {
      return this.component;
    },
  },
  mounted() {
    if (localStorage.getItem("data")) {
      const a = localStorage.getItem("data");
      const obj = JSON.parse(a);
      this.message = obj;
    }
  },
  methods: {
    listComponent() {
      this.component = ListData;
    },
    addComponent() {
      this.component = AddData;
    },
    eventAddData(mess) {
      //   console.log(mess);
      this.message.push(mess);
      const myJSON = JSON.stringify(this.message);
      localStorage.setItem("data", myJSON);
      this.component = ListData;
    },
    eventDelData(mess) {
    //   console.log(mess);
      var removeIndex = this.message
        .map(function (item) {
          return item.time;
        })
        .indexOf(mess);
      this.message.splice(removeIndex, 1);
      const myJSON = JSON.stringify(this.message);
      localStorage.setItem("data", myJSON);
    },
  },
};
</script>

<style scoped>
.space {
  margin-right: 20px;
}
</style>

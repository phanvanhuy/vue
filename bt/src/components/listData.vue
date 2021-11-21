<template>
  <div class="listdata">
      <div class="listcard my-4 py-2 px-2 d-flex justify-content-between" v-for="(list, index) in listData" :key=index>
          <div>
                <div>Title: {{list.title}}</div>
                <div>Text: {{list.text}}</div>
                <div>Url: {{list.url}}</div>
          </div>
        
        <button type="button" class="btn btn-warning" @click="deldata(list.time)">Delete</button>

          <!-- <div>delete: {{list.time}}</div> -->
        
      </div>
      <br>
  </div>
</template>

<script>
export default {
  name: "ListData",
  props: {
        listData: {
        type: Object,
        default: () => {}
    },
  },
  methods: {
      deldata(time){  
          this.$emit('eventDeleteData', time);
      }
  }
   
};
</script>

<style scoped>
    .listdata{
        max-width: 600px;
    }
    .listcard{
        border-radius: 8px;
        border: 2px solid chocolate;
    }
</style>
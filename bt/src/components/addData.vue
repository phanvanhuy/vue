<template>
  <div class="adddata">
    <form>
        <div class="form-group">
        <label for="exampleFormControlInput1">Title </label>
        <input 
             required
            type="text"
            class="form-control"
            id="exampleFormControlInput1"
            v-model="title"
        />
        </div>

        <div class="form-group">
        <label for="exampleFormControlTextarea1">Description</label>
        <textarea

            v-model="text"
            class="form-control"
            id="exampleFormControlTextarea1"
            rows="3"
            required
        ></textarea>
        </div>

         <div class="form-group">
        <label for="exampleFormControlInput2">URL</label>
        <input 
            required
            type="text"
            class="form-control"
            id="exampleFormControlInput2"
            v-model="url"
        />
        </div>
        <br>

       <button  type="submit" class="btn btn-primary mb-2" @click="getdata()">Confirm</button>
    </form>

  </div>
</template>

<script>
export default {
  name: "AddData",
  data() {
      return {
          email: '',
          text: '',
          url: '',
      }
  },
  methods:{
      getdata(){
          if(this.title==''||this.text==''||this.url==''){
              return 0;
          }
          const mess = {time: Date.now(),title: this.title, text: this.text, url: this.url}
          this.$emit('eventAddData', mess);
      },

     
  }
  
};
</script>

<style >
 .adddata{
     max-width: 600px;
 }
</style>
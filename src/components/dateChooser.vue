<template>
    <div>
        <Datepicker v-model="customDate" format="dd-MM-yyyy" placeholder="Choose Task deadline"></Datepicker>
    </div>
  </template>
   
  <script>
  import Datepicker from 'vue3-datepicker';
  
  export default {
    name: "chooserApp",
    components: {
            Datepicker
        },
        data: function(){
            return {
              customDate: new Date()
            }
        }
    }

  </script>
  
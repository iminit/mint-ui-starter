<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <h1>{{ msg }}</h1>
      <mt-button @click.native="startHacking">Let's do it</mt-button>
      <mt-progress :value="progress">
        <div slot="start">0%</div>
        <div slot="end">100%</div>
      </mt-progress>
    <mt-button @click.native="progressAdd">进度条增加<mt-badge size="small">{{progress}}</mt-badge></mt-button>
    <br>
    <mt-datetime-picker
        ref="picker"
        type="time"
        v-model="pickerValue">
      </mt-datetime-picker>
      <h1>日期：{{ pickerValue }}</h1>
    <mt-button @click.native="openPicker">日期选择</mt-button>
    
    <mt-switch v-model="switchValue">开关:{{switchValue}}</mt-switch>

    <br>
    <mt-checklist
      title="复选框列表"
      align="right"
      v-model="checklistValue"
      :options="['选项A', '选项B', '选项C']">
    </mt-checklist>
    checklistValue:{{checklistValue}}


    <br>
    <br>
    
    <mybutton @click.native="getData"></mybutton>
  
  </div>
  


</template>

<script>
import mybutton from './mybutton.vue'
import axios from 'axios'
export default {
  components: {
    mybutton
  },
  name: "app",
  data() {
    return {
      msg: "Welcome",
      progress: 10,
      switchValue: true,
      checklistValue: [],
      pickerValue: '',
      username: "",
      email: "",
      password: "",
      phone: "",
      website: "",
      number: "",
      birthday: "",
      introduction: "",
      searchValue: ""
    };
  },
  mounted() {
    // this.getData();
    console.log("welecome to vue");
  },
  methods: {
    getData(){
      // alert("1234");
      axios.get("README.md")
      .then(function(res){
        alert(res.data);
        console.log(res);
      }.bind(this)).catch(function(err){
        console.log(err);
      });
    },
    openPicker() {
      this.$refs.picker.open();
    },
    startHacking() {
      this.$toast("It Works!");
    },
    progressAdd() {
      this.progress < 100 && (this.progress += 10);
    },
    main_log(val) {
      console.log("main_log", val);
    },
    sub_log(val) {
      console.log("sub_log", val);
      this.$refs.target_1.collapse();
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

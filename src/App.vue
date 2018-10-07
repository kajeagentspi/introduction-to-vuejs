<template>
  <div id="app">
    <select v-model="demo">
      <option>Conditionals</option>
      <option>Computed Values</option>
      <option>Lists</option>
      <option>Event Handling</option>
    </select>
    <br/>
    <h2>{{demo}}</h2>
    <div v-show="demo==='Conditionals'">
      <span>Kamusta na SP mo pre? </span>
      <br/>
      <input type="text" v-model="spAnswer" />
      <br/>
      {{spAnswer}}
      <br/>
      <span v-if="spAnswer==='ok lang'">Wow Lodi</span>
      <span v-else-if="spAnswer==='medyo hirap'">Kaya pa yan</span>
      <span v-else>Fighting!!!</span>
      <br/>
      <span v-show="spAnswer==='hindi pa ko nagcoconsult'">consult ka na pre</span>
    </div>
    <div v-show="demo==='Computed Values'">
      <input type="number" v-model="number"/>
      <span>{{factorial}}</span>
    </div>
    <div v-show="demo==='Lists'">
      <span v-for="subject in subjects" :key="subject.classCode">
      {{subject.classCode}} - {{subject.description}}
      <br/>
    </span>
    </div>
    <div v-show="demo==='Event Handling'">
      <span v-for="subject in subjects" :key="subject.classCode">
      {{subject.classCode}} - {{subject.description}}
        <br/>
      </span>
      <input type="text" v-model="subject"/>
      <button @click="addSubject">Submit</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      demo:"Conditionals",
      number:5,
      spAnswer:"ok lang",
      subject:"",
      subjects:[
        {classCode:"CMSC137", description:"Data Communications and Networking"},
        {classCode:"CMSC142", description:"Design and Analysis of Algorithms"},
        {classCode:"CMSC150", description:"Numerical and Symbolic Computations"},
        {classCode:"CMSC165", description:"Digital Image Processing"},
        {classCode:"CMSC190", description:"Special Problems"},
        {classCode:"CMSC199", description:"Undergraduate Seminar"},
      ],
    }
  },
  computed: {
    factorial(){
      let result = this.number
      let num = result
      console.log(result,num)
      if (num === 0 || num === 1) 
        return 1; 
      while (num > 1) { 
        num--;
        result *= num;
      }
      return result;
    }
  },
  methods: {
    addSubject(){
      const [classCode,description] = this.subject.split(": ")
      this.subjects.push({classCode,description})
    }
  }
}
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
</style>

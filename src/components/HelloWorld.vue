<template>
  <div class="hello">
    <h3>这是子组件</h3>
    <table border="1px">
      <slot></slot>
      <tr v-for="(item,i) in tabdata" :key="i" @click="slotcomit(item,i)">
        <slot name="test" :row="item"></slot>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      
    }
  },
  methods:{
     slotcomit(val,i){
      this.$emit('testcommit',val,i);
    }
  },
  props:{
    tabdata:{
      type:Array
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
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

<template>
  <div id="app">
     <hello-world  @testcommit="changerow" :tabdata="tableData">
       <thead>
         <tr>
           <td style="width:150px">a</td>
           <td style="width:150px">b</td>
           <td style="width:150px">c</td>
           <td style="width:150px">d</td>
         </tr>
       </thead>
         <template slot="test" slot-scope="scope">
           <!-- <td>{{scope.row.name}}</td>
           <td>{{scope.row.date}}</td>
           <td>{{scope.row.address}}</td> -->
             <td>
              <input type="text" v-model="scope.row.name" placeholder="请输入内容" v-show="scope.row.flag" />
                <span v-show="!scope.row.flag" > {{scope.row.name}}</span>
              </td>
             <td>{{scope.row.date}}</td>
             <td>{{scope.row.address}}</td>
         <!-- <h4>这是命名插槽---{{tableData.name}}</h4> -->
         <!-- <li v-for="(item,index) of row" :key="index">{{item.name}}</li> -->
       </template>
     </hello-world>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
export default {
  data() {
      return {
        tableData: [{
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1517 弄'
        }, {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1519 弄'
        }, {
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1516 弄'
        }],
        lastRow:null
      }
    },
    components:{
      HelloWorld
    },
    methods: {
      handleEdit(index, row) {
        console.log(index, row);
      },
      handleDelete(index, row) {
        console.log(index, row);
      },
      handleCurrentChange(row,event,colom){
        console.log(row,event,colom);
        if (this.lastRow) {
          this.lastRow.flag = false;
        }
        row.flag=true;
        this.lastRow=row;
      },
      changerow(row,i){
        // console.log(row,i);
        if (this.lastRow) {
          this.lastRow.flag = false;
        }
        row.flag = true;
        this.$set(this.tableData,i,row);
        this.lastRow=row;
      }
    }
}
</script>

<style>
</style>

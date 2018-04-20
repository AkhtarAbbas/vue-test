<template>
  <div id="app">
  	<navbar></navbar>
  	<div class="container">
  		<div class="content mt-5">
  			<div class="row">
  				<div class="col-md-6">
  					<h1>data</h1>
  				</div>
  				<div class="col-md-6">
      		<b-btn v-b-modal.modal1>Add</b-btn>
          <b-modal id="modal1" @ok="handleSubmit" size="lg">
            <b-form inline v-for="(field, index) in fields" class="mt-2">
              <label>field name </label>
              <b-input class="mr-3 ml-3" v-model="fields[index].field_name" />
              <label>field value </label>
              <b-input-group class="ml-3 mr-3">
                <b-input v-model="fields[index].field_value"/>
              </b-input-group>
            </b-form>
            <b-button @click="handleAddItems" variant="primary" >+</b-button>
          </b-modal>
  				</div>
  			</div>
	  		<dataTable :fields="data" :handleDelete="handleDelete"></dataTable>
	  	</div>
  	</div>
  </div>
</template>

<script>
import navbar from './components/navbar'
import dataTable from './components/table'
export default {
  data(){
    return{
      data: [],
      fields:[
        {field_name: '',field_value:'',create_date: new Date().toString(), status: 1,actions:'',}
      ]
    }
  },
	components:{
		navbar,dataTable
	},
  methods: {
    handleAddItems () {
      this.fields.push({
        field_name: '',
        field_value: '',
        status: 1,
        create_date: new Date(),
        actions: ''
      })
    },

    handleSubmit () {
      this.fields.map(item => {
        this.data.push(item);
      });
      this.fields = [
          {
            field_name: '',
            field_value:'',
            create_date: new Date().toString(),
            status: 1,
            actions:'',
        }
      ]
    },
    handleDelete (index) {
      this.data.splice(index,1)
    }
  }

}
</script>

<style>
</style>

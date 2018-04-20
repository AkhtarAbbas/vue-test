<template>
  <div>
    <b-form inline v-for="field in fields">
      <label>field name </label>
      <b-input class="mr-3 ml-3" v-model="field.name" />
      <label>field value </label>
      <b-input-group class="ml-3 mr-3">
        <b-input placeholder="Akhtar" v-model="field.value"/>
      </b-input-group>
      <b-button variant="primary" >+</b-button>
    </b-form>
  </div>
</template>

<script>
  export default{
    data(){
      return{
      }
    }
  }
</script>
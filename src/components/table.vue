<template>
  <div>
  	<b-table hover :items="paginated">
  		<template slot="actions" slot-scope="data">
  			<button class="btn btn-danger" @click="handleDelete()">delete</button>
      </template>
  	</b-table>
  	<b-pagination :total-rows="fields.length" size="md" v-model="page" :per-page="perPage">
    </b-pagination>
  </div>
</template>

<script>


	export default {
		props: ['fields','handleDelete'],

	  data () {
	    return {
	      paginated: [],
	      page: 1,
	      perPage:2
	    }
	  },
	  mounted() {
	  	this.get();
	  },
	  watch: {
	  	page: function () {
	  		this.get();
	  	},
	  	fields: function () {
	  		this.get();
	  	}
	  },
	  methods: {
		paginate (array, page_size, page_number) {
			--page_number;
			return array.slice(page_number * page_size, (page_number + 1) * page_size);
		},
		get() {
			this.paginated = this.paginate(this.fields, this.perPage, this.page);
		}

	  }
	}
</script>
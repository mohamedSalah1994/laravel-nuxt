<template>
  <div class="container">
    <div>
      <loading v-if="loading"/>
      <Row v-else>
        <Col  span="24" >

            <h1>Name</h1>
          <p>{{row.name}}</p>

          <div >
            <h1 style="margin-top: 20px">Image</h1>
            <img :src="$images(row.image , 'org')" >
          </div>
          <h1 style="margin-top:20px">Description</h1>
          <p v-html="row.description"></p>
        </Col>
      </Row>
    </div>
  </div>
</template>

<script>
import loading from "@/components/loading";
export default {
  comments:{
    loading
  },
  data() {
    return {
      row: [],
      loading:true,

    }
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    fetchData() {
      this.loading=true;
      let url = process.env.MODULE_URL+'services/'+this.$route.params.id;

      this.$axios.$get(url).then((res) => {
          this.row = res.payload;
          this.loading = false;
      })


    }
  }


}

</script>



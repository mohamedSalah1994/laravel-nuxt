<template>
  <div>
    <Divider>Services</Divider>
    <Row>
      <Col  span="8" v-for="row in rows">

        <Card style="margin: 28px" >
          <p slot="title"><nuxtLink :to="'/services/'+row.id">{{row.name}} </nuxtLink></p>
          <nuxtLink :to="'/services/'+row.id">
            <img :src="$images(row.image)" >
          </nuxtLink>
        </Card>
      </Col>
    </Row>
  </div>
</template>
<script>
export default {
  data () {
    return {
      rows:[],
      loading:true,

    }
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    fetchData() {
      this.loading=true;
      let url = process.env.MODULE_URL+'services';

      this.$axios.$get(url).then((res) => {
        this.rows = res.payload.data;
        this.loading = false;
      })


    }
  }
}
</script>

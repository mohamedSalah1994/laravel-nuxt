<template>
<div>
  <Divider>Testmonial</Divider>
  <Row>
    <Col  span="4" v-for="row in rows">
      <Card style="margin: 10px" >
        <div style="text-align:center">
          <Avatar :src="$images(row.image)" size="large"/>
          <h3>{{ row.name}}</h3>
          <p>{{row.job_title}}</p>
          <p>{{row.comment}}</p>
        </div>
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
      let url = process.env.MODULE_URL+'testmonials';

      this.$axios.$get(url).then((res) => {
        this.rows = res.payload.data;
        this.loading = false;
      })


    }
  }
}
</script>

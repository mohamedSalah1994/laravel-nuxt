<template>
  <div class="container">
    <div>
      <h1>Clients</h1>
      <Row>

        <Card style="margin: 10px" v-for="row in rows">
          <div style="text-align:center">
            <img :src="'http://127.0.0.1:8000/storage/'+row.image" width="250">
          </div>
        </Card>

      </Row>


    </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
      rows: []
    }
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    fetchData() {

      this.$axios.$get('http://127.0.0.1:8000/api/module/clients').then((res) => {
              this.rows = res.payload.data;

      })


    }
  }


}

</script>



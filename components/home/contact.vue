<template>
  <div>
    <Divider>Contact Us</Divider>
    <form action="">

      <Row style="">
        <Col span="20">
          <Input v-model="name" placeholder="Enter Your Name"></Input>
          <template v-if="errors.name">
            <Alert type="error">{{errors.name[0]}}</Alert>
          </template>
        </Col>
        <Col span="20" style="margin-top: 20px">
          <Input v-model="email" type="email" placeholder="Enter Your Email"></Input>
          <template v-if="errors.email">
            <Alert type="error">{{errors.email[0]}}</Alert>
          </template>
        </Col>
        <Col span="20" style="margin-top: 20px">
          <Input v-model="mobile" placeholder="Enter Your Mobile"></Input>
          <template v-if="errors.mobile">
            <Alert type="error">{{errors.mobile[0]}}</Alert>
          </template>
        </Col>
        <Col span="20" style="margin-top: 20px">
          <Input v-model="message"  placeholder="Enter Your Name" type="textarea"></Input>
          <template v-if="errors.message">
            <Alert type="error">{{errors.message[0]}}</Alert>
          </template>
        </Col>
        <Col span="20" style="margin-top: 20px">
          <Button type="primary" @click.prevent="contact">Send Message</Button>


        </Col>
      </Row>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {

      loading: true,
      value1: 0,
      name:'',
      email:'',
      mobile:'',
      message:'',
      response:[],
      errors:{}
    }
  },
  mounted() {

  },
  methods: {
    contact() {
      this.loading = true;
      let url = process.env.BASE_URL + '/api/contacts';
      let data = {
         name : this.name ,
         email : this.email,
         mobile : this.mobile,
         message : this.message,
      }
      this.$axios.post(url , data).then((res) => {
          this.response = res.data;

          if (this.response.status === true){
            this.errors={};
            this.$Message.success(this.response.message);
            this.name = '';
            this.email = '';
            this.mobile = '';
            this.message = '';
          }else {
            this.$Message.error(this.response.message);
            this.errors = res.data.payload;
          }
      })


    }
  }
}
</script>

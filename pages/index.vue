<template>
  <div class="container">
    <div>
      <slider />
      <test />
      <service />
      <contact />
    </div>
  </div>
</template>

<script>
import slider from "~/components/home/slider";
import test from "~/components/home/test";
import service from "~/components/home/service";
import contact from "~/components/home/contact";

export default {
    comments:{
      slider,
      test,
      service,
      contact
    }
}
</script>



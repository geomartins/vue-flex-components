<script>
import { defineComponent } from "vue";
import FlexInnerLoading from "@/lib-components/FlexLoading";
//import FlexInnerLoading from '../src/lib-components/FlexInnerLoading.vue';
// Uncomment import and local "components" registration if library is not registered globally.
// import { VueFlexComponentSample } from '@/entry.esm';

export default defineComponent({
  name: "ServeDev",
  components: {
    FlexInnerLoading,
  },
  data() {
    return {
      visible: false,
    };
  },
});
</script>

<template>
  <div id="app">
    <flex-inner-loading
      ref="inner"
      label="Pls Wait while we process ur transaction ..."
      labelColor="teal"
      labelSize="1.1rem"
      labelWeight="bold"
      bgColor="#80808014"
      iconColor="red"
      icon="fas fa-spinner"
      iconSize="50px"
      :showing="visible"
      speed="6s"
      transition="4s"
    >
      ffjfhjhfjhfjhfh fjfjfjfg
    </flex-inner-loading>

    <div
      @click="visible = !visible"
      style="position: absolute; z-index: 500000000; top: 0px"
    >
      Toggle Now
    </div>
  </div>
</template>

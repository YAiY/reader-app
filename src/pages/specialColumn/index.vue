<!--  -->
<template>
  <div class="wrapper">
    
		<uni-file-picker 
			v-model="imageValue" 
			fileMediatype="image" 
			mode="grid" 
			@select="select" 
			@progress="progress" 
			@success="success" 
			@fail="fail" 
		/>
  </div>
</template>

<script>
import uniFilePicker from "@/uni_modules/uni-file-picker/components/uni-file-picker/uni-file-picker";
export default {
  components: {
    uniFilePicker
  },

  data () {
    return {
    }
  },

  computed: {},

  methods: {},

  created() {}
}

</script>
<style lang='scss' scoped>
</style>
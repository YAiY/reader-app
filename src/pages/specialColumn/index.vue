<!--  -->
<template>
  <div class="wrapper">
    
		<uni-file-picker 
      return-type="object"
      limit="1"
      ref="files"
      :auto-upload="false"
			v-model="fileValue"
      file-mediatype="all"
      file-extname="txt,pdf,word"
      @select="select"
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
      fileValue: {},

    }
  },

  computed: {},

  methods: {
    select(e) {
      console.log(e);
      // console.log(this.fileValue);
      const readerFile = new FileReader()
      readerFile.readAsText(e.tempFiles[0].file);
      // 文件内容
      const fileContent = readerFile.result
      console.log(readerFile);
    },

  },

  created() {}
}

</script>
<style lang='scss' scoped>
</style>
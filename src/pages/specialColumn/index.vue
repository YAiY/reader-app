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
    <button @click="selectFile">按钮</button>
    <!-- <view>{{filePath}}</view> -->
    <!-- <view>{{filePath2}}</view> -->
    <view>{{fileContent}}</view>
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
      filePath: '',
      filePath2: '',
      fileContent: ''
    }
  },

  computed: {},

  methods: {
    select(e) {
      console.log(e);
      const _this = this
		  /* #ifdef APP-ANDROID */
        this.filePath = e.tempFilePaths
        this.filePath2 = e.tempFiles[0].cloudPath
        // console.log(this.fileValue);
        const readerFile = new FileReader()
        readerFile.readAsText(e.tempFiles[0].file);
        // 文件内容
        const fileContent = readerFile.result
        console.log(readerFile);
      /* #endif */
		  /* #ifdef MP-WEIXIN */
        const fs = wx.getFileSystemManager()
        const fd = fs.openSync({filePath: e.tempFiles[0].path})
        fs.readFile({
          filePath: e.tempFiles[0].path,
          encoding: 'utf8',
          // position: 0,
          // length: 100,
          success(res) {
            // fs.fstat({
            //   fd,
            //   success(res) {
            //     console.log(res)
            //   }
            // })
            _this.fileContent = res.data
            console.log(res);
          }
        })
      /* #endif */
    },
    selectFile() {
      wx.chooseMessageFile({
        count: 1,
        type: 'file',
        extension: ['pdf','txt','word'],
        success: (res) => {
          this.select(res);
        }
      })
    }
  },

  created() {}
}

</script>
<style lang='scss' scoped>
</style>
 <template>
	<view class="content">
		<!-- #ifdef APP-IOS -->
		<text class="title">ios</text>
		<!-- #endif -->
		<!-- #ifdef APP-ANDROID -->
		<text class="title">ANDROID</text>
		<!-- #endif -->
		<!-- <image class="logo" src="/static/logo.png"></image> -->
		<uni-file-picker 
			v-model="imageValue" 
			fileMediatype="image" 
			mode="grid" 
			@select="select" 
			@progress="progress" 
			@success="success" 
			@fail="fail" 
		/>
		<view>
			<text class="title">{{title}}</text>
		</view>
	</view>
</template>

<script>
import uniFilePicker from "@/uni_modules/uni-file-picker/components/uni-file-picker/uni-file-picker";
	export default {
		data() {
			return {
				imageValue: [],
				title: 'Hello'
			}
		},
		components: {
			uniFilePicker
		},
		onLoad() {

		},
		methods: {
			select() {},
			progress() {},
			success() {},
			fail() {},
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin: 200rpx auto 50rpx auto;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>

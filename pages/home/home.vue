<template>
	<view>
		<navbar></navbar>
		<view v-for="item in 100">
			内容 {{item}}item
		</view>
	</view>
</template>

<script>
	export default {
		name: 'Home',
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="scss">

</style>

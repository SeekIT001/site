<template>
	<div class="banner" v-lazy:background-image="bg">
		<div class="text-box">
			<h2><slot name="subtitle" /></h2>
			<h1><slot name="title" /></h1>
			<p><slot name="text" /></p>
			<div class="buttons">
				<slot name="buttons" />
			</div>
		</div>
		
	</div>
</template>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
	props: ["bg"],
});
</script>

<style lang="less" scoped>
.banner {
	z-index: -2;
	height: 500px;
	width: 100%;
	display: flex;
	align-items: center;
	background-position: center;
	background-size: cover;
	background-repeat: no-repeat;
	background-color: black;

	&[fullscreen] {
		height: 100vh;
		@media (max-width: 800px) {
			height: calc(100vh * 0.9);
		}
	}
}

.text-box {
	color: white;
	@media screen and (min-width: 800px) {
		margin-left: 48px;
	}

	@media screen and (max-width: 800px) {
		padding: 32px;
	}

	h1,
	h2,
	p {
		margin: 8px 0;
		text-shadow: 0px 2px 4px #00000050;
	}

	h1 {
		font-size: 58px;
		@media screen and (max-width: 800px) {
			font-size: 40.5px;
		}
	}

	h2 {
		font-size: 38.4px;
		font-weight: normal;
		margin-bottom: 8px;
		@media screen and (max-width: 800px) {
			font-size: 26.88px;
		}
	}

	p {
		font-size: 21.6px;
		margin-top: 16px;
		line-height: 1.8;
		@media screen and (max-width: 800px) {
			font-size: 16.7px;
		}
	}
}

.buttons {
	display: flex;
	align-items: stretch;
	margin-top: 32px;
}
</style>
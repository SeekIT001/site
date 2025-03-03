<template>
	<button
		@click="go()"
		class="btn"
		:class="
			type + ' ' + size + ' ' + (isPCSize() && !isIOS() ? 'pc' : 'mobile')
		"
	>
		<div class="content">
			<slot />
			<mdicon v-if="icon" :name="icon" class="icon" />
		</div>
	</button>
</template>

<script lang="ts">
import Vue from "vue";
import { isPCSize, isIOS } from "@/fn";
export default Vue.extend({
	props: ["type", "size", "icon", "to", "href"],
	methods: {
		go() {
			if (this.to) this.$router.push(this.to);
			if (this.href) window.open(this.href);
		},
		isPCSize,
		isIOS() {
			let nav = window.navigator;
			if (/iPad|iPhone|iPod/.test(nav.platform)) {
				return true;
			} else {
				return (
					nav.maxTouchPoints &&
					nav.maxTouchPoints > 2 &&
					/MacIntel/.test(nav.platform)
				);
			}
		},
	},
});
</script>

<style lang="less" scoped>
.btn {
	display: block;
	border-radius: 5px;
	padding: 8px 12px;
	border: none;
	transition: all 0.2s ease;
	cursor: pointer;
	font-family: inherit;

	&.large {
		@media screen and (max-width: 1000px) {
			font-size: 14px;
		}
		@media screen and (min-width: 1000px) {
			padding: 10px 20px;
		}
		font-size: 18px;
	}

	&.small {
		padding: 2px 8px;
		font-size: 12px;
	}

	&.shadow {
		box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.3);
	}

	&.hover {
		&:hover {
			box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.5);
		}
	}

	&.hover-light {
		&:hover {
			box-shadow: 0px 3px 5px rgba(0, 0, 0, 0.1);
		}
	}

	&.primary-outlined {
		border: 1px solid #fcd307;
		background: linear-gradient(94deg, #fcd307 29.88%, #ffb526 67.68%);
		background-clip: text;
		color: transparent;

		svg {
			color: #fcd307;
		}
	}

	&.primarylight.pc {
		background: linear-gradient(94deg, #fcd307 29.88%, #ffb526 67.68%);
		background-clip: text;
		color: transparent;
	}

	&.primarylight.mobile {
		color: @primarydark;
	}

	&.mobile {
		color: @primarydark;
	}

	&.primarylight {
		position: relative;
		svg {
			color: @primarydark;
		}
		&:hover {
			&::after {
				background: #eee;
			}
		}

		&::after {
			transition: all 0.5s ease;
			content: " ";
			display: block;
			position: absolute;
			left: 0;
			top: 0;
			border-radius: inherit;
			width: 100%;
			height: 100%;
			background: white;
			z-index: -20;
		}
	}

	&.primary {
		background-image: linear-gradient(
			to right,
			#fcd307 29.88%,
			#ffb526 67.68%
		);
		background-size: 140% auto;
		&:hover {
			background-position: right center;
		}
		color: white;
	}

	&.outlined {
		background: transparent;
		color: white;
		border: 1px solid rgba(255, 255, 255, 0.5);

		&:hover {
			border-color: white;
		}
	}

	&.arrow {
		@media screen and (min-width: 1000px) {
			svg {
				transition: all 0.2s ease;
			}

			&:hover svg {
				transform: translateX(4px);
			}
		}
	}

	&.dark {
		border-color: @textmidgray;
		color: @textmidgray;

		&:hover {
			border-color: black;
			color: black;
		}
	}
}

.content {
	display: flex;
	align-items: center;

	.icon {
		margin-left: 0.3em;
		svg {
			width: 20px;
		}
	}
}
</style>
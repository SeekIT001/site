<template>
	<footer>
		<div class="footer-container">
			<div class="col first">
				<logo class="footer light" />
				<p class="copyright">
					&copy; 2022 SEATiDE Modded Minecraft Server<br />
					<small>网站基于 Vue 2 · GitHub Pages · 我们❤️开源</small>
				</p>
				<p>
					SEATiDE 致力于以简单的方式获得高质量的 Minecraft
					服务器体验和社区气氛。我们随时欢迎你成为 SEATiDE 一员 ;)
				</p>
				<p>
					注：如无特殊说明，所有文字的著作权和游戏摄影作品使用权归
					SEATiDE 所有。侵权必究。
				</p>
			</div>
			<div class="links">
				联系服主 — <a href="mailto:christophersubilan@gmail.com">christophersubilan@gmail.com</a>
				<br/>
				友链 —
				<a href="https://sotap.org" target="_blank">SoTap</a> ·
				<a href="https://i.teriri.cc/" target="_blank"
					>桜酱的温馨小窝</a
				>
				· <a href="https://subilan.win" target="_blank">服主博客</a> ·
				<a href="https://www.mcnav.net/" target="_blank">MCNav</a>
			</div>
			<div class="button-list">
				<icon-btn
					@click.native="$open('https://github.com/seatidemc')"
					icon="github"
					class="dark"
				/>
				<icon-btn
					@click.native="$open('https://w.seatide.top')"
					icon="book-outline"
					class="dark"
				/>
			</div>
		</div>
	</footer>
</template>

<script lang="ts">
import Vue from "vue";
import Logo from "./Logo.vue";
import IconBtn from "@/components/IconBtn.vue";

export default Vue.extend({
	components: { Logo, IconBtn },
});
</script>

<style lang="less" scoped>
footer {
	box-shadow: 0px -2px 10px rgba(0, 0, 0, 0.4);
	background: #212121;
	color: white;
	.links {
		@media (max-width: 1000px) {
			position: static;
			text-align: center;
			margin: 8px 0;
		}
		
		position: absolute;
		right: 0;
		bottom: calc(32px + 14px);
		text-align: right;
		color: @textmidwhite;
		font-size: 14px;
		a {
			margin-top: 5px;
			border-bottom: 1px solid rgba(255, 255, 255, 0.3);
			transition: all 0.2s ease;
			display: inline-block;
			&:hover {
				color: white;
				border-color: white;
			}
		}
	}

	.footer-container {
		display: block;
		margin: auto;
		padding: 32px 56px;
		width: 70%;
		position: relative;

		.col {
			&.first {
				p {
					color: @textmidwhite;
					font-size: 14px;
					max-width: 400px;
				}

				.copyright {
					color: white;
				}

				.light {
					margin-bottom: 32px;
				}
			}
		}
	}
}

.button-list {
	display: flex;
	> * {
		margin: 8px 5px;
	}
	@media (max-width: 1000px) {
		justify-content: center;
	}
	@media screen and (min-width: 1000px) {
		position: absolute;
		top: 32px;
		right: 0;
	}
}
</style>

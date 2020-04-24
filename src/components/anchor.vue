<template>
	<div class="app-container">
		
		<div style="height: 293px;"></div>
		
		<!-- 基本信息 -->
		<div class="profile-content content-one">
			基本信息
		</div>

		<!-- 工作信息 -->
		<div class="profile-content content-two">
			工作信息
		</div>

		<!-- 个人信息 -->
		<div class="profile-content content-three">
			个人信息
		</div>

		<!-- 学历信息 -->
		<div class="profile-content content-four">
			学历信息
		</div>

		<!-- 工资信息 -->
		<div class="profile-content content-five">
			工资信息
		</div>

		<!-- 银行卡信息 -->
		<div class="profile-content content-six">
			银行卡信息
		</div>

		<!-- 紧急联系人 -->
		<div class="profile-content content-seven">
			紧急联系人
		</div>

		<!-- 家庭信息 -->
		<div class="profile-content content-eight">
			家庭信息
		</div>

		<!-- 个人材料 -->
		<div class="profile-content content-nine">
			个人材料
		</div>

		<div class="left-anchor">
			<ul>
				<li class="anchor-item" @click="anchors(1)">
					<span class="anchor-item-title" :class="steps == 1?'title-color':''">基本信息</span>
					<div class="dot" :class="steps == 1?'dot-color':'no-dot-color'"></div>
				</li>
				<li class="lines"></li>
				<li class="anchor-item" @click="anchors(2)">
					<span class="anchor-item-title" :class="steps == 2?'title-color':''">工作信息</span>
					<div class="dot" :class="steps == 2?'dot-color':'no-dot-color'"></div>
				</li>
				<li class="lines"></li>
				<li class="anchor-item" @click="anchors(3)">
					<span class="anchor-item-title" :class="steps == 3?'title-color':''">个人信息</span>
					<div class="dot" :class="steps == 3?'dot-color':'no-dot-color'"></div>
				</li>
				<li class="lines"></li>
				<li class="anchor-item" @click="anchors(4)">
					<span class="anchor-item-title" :class="steps == 4?'title-color':''">学历信息</span>
					<div class="dot" :class="steps == 4?'dot-color':'no-dot-color'"></div>
				</li>
				<li class="lines"></li>
				<li class="anchor-item" @click="anchors(5)">
					<span class="anchor-item-title" :class="steps == 5?'title-color':''">工资信息</span>
					<div class="dot" :class="steps == 5?'dot-color':'no-dot-color'"></div>
				</li>
				<li class="lines"></li>
				<li class="anchor-item" @click="anchors(6)">
					<span class="anchor-item-title" :class="steps == 6?'title-color':''">银行卡信息</span>
					<div class="dot" :class="steps == 6?'dot-color':'no-dot-color'"></div>
				</li>
				<li class="lines"></li>
				<li class="anchor-item" @click="anchors(7)">
					<span class="anchor-item-title" :class="steps == 7?'title-color':''">紧急联系人</span>
					<div class="dot" :class="steps == 7?'dot-color':'no-dot-color'"></div>
				</li>
				<li class="lines"></li>
				<li class="anchor-item" @click="anchors(8)">
					<span class="anchor-item-title" :class="steps == 8?'title-color':''">家庭信息</span>
					<div class="dot" :class="steps == 8?'dot-color':'no-dot-color'"></div>
				</li>
				<li class="lines"></li>
				<li class="anchor-item" @click="anchors(9)">
					<span class="anchor-item-title" :class="steps == 9?'title-color':''">个人材料</span>
					<div class="dot" :class="steps == 9?'dot-color':'no-dot-color'"></div>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>
	export default {
		components: {
		},
		data() {
			return {
				steps: 0,
				scrolltop: 0, //滑轮 距顶部的距离
				floorOne: 0,
				floorTwo: 0,
				floorThree: 0,
				floorFour: 0,
				floorFive: 0,
				floorSix: 0,
				floorSeven: 0,
				floorEight: 0,
				floorNine: 0
			}
		},
		watch: {
			// 监听轮滑到顶端的距离，动态设置锚点的位置
			scrolltop(val) {
				val += 200 // +200 是因为第一个DIV到顶部有距离，轮滑需要加上
				if (val > 0 && val <= this.floorOne) {
					this.steps = 0
				} else if (val > this.floorOne && val <= this.floorTwo) {
					this.steps = 1
				} else if (val > this.floorTwo && val <= this.floorThree) {
					this.steps = 2
				} else if (val > this.floorThree && val <= this.floorFour) {
					this.steps = 3;
				} else if (val > this.floorFour && val <= this.floorFive) {
					this.steps = 4
				} else if (val > this.floorFive && val <= this.floorSix) {
					this.steps = 5
				} else if (val > this.floorSix && val <= this.floorSeven) {
					this.steps = 6
				} else if (val > this.floorSeven && val <= this.floorEight) {
					this.steps = 7
				} else if (val > this.floorEight && val <= this.floorNine) {
					this.steps = 8
				} else if (val > this.floorNine) {
					this.steps = 9
				}
			},
		},
		created() {
		},
		mounted() {
			this.getFloorDistance();
			this.getPulleyTopDistance();
		},
		methods: {
			// 拿到所有DIV到窗体顶部的距离
			getFloorDistance() {
				this.floorOne = document.getElementsByClassName("content-one")[0].offsetTop;
				this.floorTwo = document.getElementsByClassName("content-two")[0].offsetTop;
				this.floorThree = document.getElementsByClassName("content-three")[0].offsetTop;
				this.floorFour = document.getElementsByClassName("content-four")[0].offsetTop;
				this.floorFive = document.getElementsByClassName("content-five")[0].offsetTop;
				this.floorSix = document.getElementsByClassName("content-six")[0].offsetTop;
				this.floorSeven = document.getElementsByClassName("content-seven")[0].offsetTop;
				this.floorEight = document.getElementsByClassName("content-eight")[0].offsetTop;
				this.floorNine = document.getElementsByClassName("content-nine")[0].offsetTop;
			},
			// 滑轮滚动事件 返回滑轮距顶部的距离
			getPulleyTopDistance() {
				let that = this
				// onscroll 轮滑的监听事件 返回轮滑到顶端的距离
				window.onscroll = function() {
					that.scrolltop = document.documentElement.scrollTop || document.body.scrollTop;
					that.getFloorDistance()
				}
			},
			// 滑轮 向上滚动和向下滚动的函数
			pulleyRoll(top, distance) {
				// top是楼层距窗体顶部的距离,distance当前滚动条与窗体顶部的距离
				// 向下滚动
				// distance -= 200
				if (distance < top) {
					var i1 = 0
					// 分割成20份 平滑
					var smallInterval1 = (top - distance - 200) / 20
					var timer1 = setInterval(() => {
						i1++
						distance += smallInterval1
						// 一次平滑的距离
						document.documentElement.scrollTop = distance
						if (i1 == 20) {
							// +1是因为除以20的时候，每份的距离可能是小数，如果是小数锚点的显示会有问题
							document.documentElement.scrollTop = distance + 1
							clearInterval(timer1)
						}
					}, 10)
				}
				/*向上滚动*/
				else if (distance > top) {
					var i2 = 0
					// 分割成20份 平滑
					var smallInterval2 = (distance - top + 200) / 20
					var timer2 = setInterval(() => {
						i2++
						distance -= smallInterval2
						// 一次平滑的距离
						document.documentElement.scrollTop = distance
						if (i2 == 20) {
							// +1是因为除以20的时候，每份的距离可能是小数，如果是小数锚点的显示会有问题
							document.documentElement.scrollTop = distance + 1
							clearInterval(timer2)
						}
					}, 10)
				}
			},
			anchors(val) {
				this.getFloorDistance()
				switch (val) {
					case 1:
						this.pulleyRoll(this.floorOne, this.scrolltop);
						break;
					case 2:
						this.pulleyRoll(this.floorTwo, this.scrolltop);
						break;
					case 3:
						this.pulleyRoll(this.floorThree, this.scrolltop);
						break;
					case 4:
						this.pulleyRoll(this.floorFour, this.scrolltop);
						break;
					case 5:
						this.pulleyRoll(this.floorFive, this.scrolltop);
						break;
					case 6:
						this.pulleyRoll(this.floorSix, this.scrolltop);
						break;
					case 7:
						this.pulleyRoll(this.floorSeven, this.scrolltop);
						break;
					case 8:
						this.pulleyRoll(this.floorEight, this.scrolltop);
						break;
					case 9:
						this.pulleyRoll(this.floorNine, this.scrolltop);
						break;
				}
			},
		}
	}
</script>

<style scoped="scoped">
	ul,
	ol {
		list-style: none;
	}

	.app-container {
		margin: 5px 20%;
		height: 4500px;
		border-left: 1px solid #999999;
		border-right: 1px solid #999999;
		background-color: #ffffff;
	}

	.left-anchor {
		position: fixed;
		left: 18%;
		top: 30%;
		width: 150px;
		height: 200px;
		z-index: 999;
	}
	
	.dot {
		width: 12px;
		height: 12px;
		border-radius: 100%;
		cursor: pointer;
	}

	.anchor-item {
		display: flex;
		flex-direction: row;
		float: right;
	}

	.anchor-item-title {
		font-size: 14px;
		margin-right: 15px;
		cursor: pointer;
	}

	.dot-color {
		background: #3296fa;
	}

	.no-dot-color {
		background: #9e9e9e;
	}

	.title-color {
		color: #3296fa;
	}

	.lines {
		width: 2px;
		height: 60px;
		background: #acacac;
		margin-left: 103px;
	}

	.profile-content {
		margin: 40px 0px 0px 150px;
		height: 300px;
	}

	.content-one {
		background-color: red;
	}

	.content-two {
		background-color: green;
	}

	.content-three {
		background-color: skyblue;
	}

	.content-four {
		background-color: black;
	}

	.content-five {
		background-color: pink;
	}

	.content-six {
		background-color: gray;
	}

	.content-seven {
		background-color: #3572d3;
	}

	.content-eight {
		background-color: yellow;
	}

	.content-nine {
		background-color: yellowgreen;
	}
</style>

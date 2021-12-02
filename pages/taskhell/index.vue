<template>
	<view>
		life页面
		<one></one>
		<canvas class="mycanvas" canvas-id="mycanvas" @touchstart="touchstart" @touchmove="touchmove" @touchend="touchend"></canvas>
		
		<!-- 底部操作按钮 -->
		<view class="footer">
		        <view class="left" @click="finish">保存</view>
		        <view class="right" @click="clear">清除</view>
		        <view class="close" @click="close">关闭</view>
		</view>
		
		
		<view @click='createCanvas()'>点击触发写字板</view>
	</view>
</template>

<script>
	export default {
		
		data(){
			return {
				//绘图图像
				ctx: '', 
				//路径点集合
				points: [], 
				//签名图片
				SignatureImg: '',
			}
		},
		//页面加载时触发
		onLoad() {
			console.log('onloda')
		},
		//页面初始渲染完成触发
		onReady() {
			console.log('ready')
		},
		//页面显示时触发
		onShow() {
			console.log('show')
		},
		//页面隐藏时触发
		onHide() {
			console.log('hide')
		},
		//页面卸载时触发
		onUnload() {
			console.log('unloda')
		},
		methods: {
		    createCanvas() {
				console.log(111)
		        //创建绘图对象
		        this.ctx = uni.createCanvasContext('mycanvas', this);
		        //设置画笔样式
		        this.ctx.lineWidth = 4;
		        this.ctx.lineCap = 'round';
		        this.ctx.lineJoin = 'round';
		        },
		    touchstart(e) {
		        let startX = e.changedTouches[0].x;
		        let startY = e.changedTouches[0].y;
		        let startPoint = { X: startX, Y: startY };
		        this.points.push(startPoint);
		        //每次触摸开始，开启新的路径
		        this.ctx.beginPath();
			},
		   touchmove(e) {
		        let moveX = e.changedTouches[0].x;
		        let moveY = e.changedTouches[0].y;
		        let movePoint = { X: moveX, Y: moveY };
		        this.points.push(movePoint); //存点
		        let len = this.points.length;
		        if (len >= 2) {
		                this.draw(); //绘制路径
		        }
			},
		   touchend() {
		        this.points = [];
			},
		   draw() {
		        let point1 = this.points[0];
		        let point2 = this.points[1];
		        this.points.shift();
		        this.ctx.moveTo(point1.X, point1.Y);
		        this.ctx.lineTo(point2.X, point2.Y);
		        this.ctx.stroke();
		        this.ctx.draw(true);
		        },
		   clear() {
		        let that = this;
		        uni.getSystemInfo({
		                success: function(res) {
		                    let canvasw = res.windowWidth;
		                    let canvash = res.windowHeight;
		                    that.ctx.clearRect(0, 0, canvasw, canvash);
		                    that.ctx.draw(true);
		                }
		        });
		        },
		   finish() {
		        let that = this;
		        uni.canvasToTempFilePath({
		            canvasId: 'mycanvas',
		            success: function(res) {
		                     //这里的res.tempFilePath就是生成的签字图片
		                    console.log(res.tempFilePath);
		            }
		        });
		   }
		}
		

	}
</script>

<style lang="scss" scoped>
	
</style>

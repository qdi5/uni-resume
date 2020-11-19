<template>
	 <view class="uni-padding-wrap" :style="{height: windowHeight + 'px'}">
		<view class="page-section">
			<view class="page-section-spacing">
				<swiper class="swiper">
					<swiper-item>
						<view class="content">
							<view class="name-wrapper">
								<text class="name">{{ resume.name }}</text>
								<text class="name-spell">{{ resume.spell }}</text>
							</view>
							<view class="naigation">
								我的简历
								<image class="arrow-right" src="/static/arrow-right.png" mode="aspectFit"></image>
							</view>
							<image class="photo" src="/static/photo.jpg" mode="widthFit"></image>
							<veiw class="job-info">
								<view class="font-end">{{ resume.job }}</view>
								<view class="job-year">{{ resume.exp }}</view>
							</veiw>
							<view class="large-circle"></view>
							<view class="medium-circle"></view>
							<view class="small-circle"></view>
						</view>
					</swiper-item>
					<swiper-item>
						<view class="swiper-item uni-bg-green base-info">
							<scroll-view scroll-y="true" class="scroll-Y" :style="{height: windowHeight + 'px'}">
								<div class="content-wrapper">
									<view class="area">
										<view class="theme d-flex horizontal v-center">
											<text class="number">1</text>基本资料
										</view>
										<view class="row d-flex dashed-border horizontal justify fill">
											<view class="left fill">
												<text class="label">姓名：</text>
												<text class="item">{{ resume.name }}</text>
											</view>
											<view class="right fill">
												<text class="label">电话：</text>
												<text class="item">{{ resume.tel }}</text>
											</view>
										</view>
										<view class="row d-flex dashed-border horizontal justify">
											<view class="left fill">
												<text class="label">性别：</text>
												<text class="item">{{ resume.sex }}</text>
											</view>
											<view class="right fill">
												<text class="label">年龄：</text>
												<text class="item">{{ resume.age }}</text>
											</view>
										</view>
										<view class="row dashed-border">
											<view class="left">
												<text class="label">邮箱：</text>
												<text class="item">{{ resume.email }}</text>
											</view>
										</view>
										<view class="row dashed-border">
											<view class="left">
												<text class="label">住址：</text>
												<text class="item">{{ resume.address }}</text>
											</view>
										</view>
									</view>
									<view class="area">
										<view class="theme d-flex horizontal v-center">
											<text class="number">2</text>主要技能
										</view>
										<view class="uni-padding-wrap uni-common-mt">
											<view class="progress-box" v-for="(skill, index) in resume.skill" :key="index">
												{{ skill.name }}
												<progress :percent="skill.percent" show-info stroke-width="10" />
											</view>
										</view>
									</view>
									<view class="area">
										<view class="theme d-flex horizontal v-center">
											<text class="number">3</text>教育经历
										</view>
										<view class="edu-wrapper" :class="{'dashed-border': index < resume.education.length - 1}" v-for="(edu, index) in resume.education" :key="index">
											<view class="school">
												<image class="school-img" src="../../static/icon_school.png" mode="widthFix"></image>
												{{ edu.school }}
											</view>
											<view class="content d-flex horizontal justify v-center">
												<view class="left">
													<image class="comm-img" src="../../static/icon_book.png" mode="widthFix"></image>
													{{ edu.major }}
												</view>
												<view class="right">
													<image class="comm-img" src="../../static/icon_calendar.png" mode="widthFix"></image>
													{{ edu.year }}
												</view>
											</view>
											<rich-text class="desc">
												{{ edu.desc }}
											</rich-text>
										</view>
									</view>
									<view class="page">1/4</view>
								</div>
							</scroll-view>
						</view>
					</swiper-item>
					<swiper-item>
						<view class="swiper-item uni-bg-blue base-info">
							<scroll-view scroll-y="true" class="scroll-Y" :style="{height: windowHeight + 'px'}">
								<div class="content-wrapper">
									<view class="area">
										<view class="theme d-flex horizontal v-center">
											<text class="number">4</text>工作经历
										</view>
										<view class="edu-wrapper" :class="{'dashed-border': index < resume.work.length - 1}" v-for="(work, index) in resume.work" :key="index">
											<view class="school">
												<image class="school-img" src="../../static/icon_company.png" mode="widthFix"></image>
												{{ work.company }}
											</view>
											<view class="content d-flex horizontal justify v-center">
												<view class="left">
													<image class="comm-img" src="../../static/icon_job.png" mode="widthFix"></image>
													{{ work.job }}
												</view>
												<view class="right">
													<image class="comm-img" src="../../static/icon_calendar.png" mode="widthFix"></image>
													{{ work.year }}
												</view>
											</view>
											<rich-text class="desc">
												{{ work.desc }}
											</rich-text>
										</view>
									</view>
									<view class="page">2/4</view>
								</div>
							</scroll-view>
						</view>
					</swiper-item>
					<swiper-item>
						<view class="swiper-item uni-bg-blue base-info">
							<scroll-view scroll-y="true" class="scroll-Y" :style="{height: windowHeight + 'px'}">
								<div class="content-wrapper">
									<view class="area">
										<view class="theme d-flex horizontal v-center">
											<text class="number">5</text>项目经历
										</view>
										<view class="edu-wrapper" :class="{'dashed-border': index < resume.project.length - 1}" v-for="(project, index) in resume.project" :key="index">
											<view class="school">
												<image class="school-img" src="../../static/icon_computer.png" mode="widthFix"></image>
												{{ project.name }}
											</view>
											<view>
												<rich-text class="desc">
													{{ project.desc }}
												</rich-text>
											</view>
										</view>
									</view>
									<view class="page">3/4</view>
								</div>
							</scroll-view>
						</view>
					</swiper-item>
					<swiper-item>
						<view class="swiper-item uni-bg-blue">
							<view class="swiper-item uni-bg-blue base-info">
								<view class="area">
									<view class="theme d-flex horizontal v-center">
										<text class="number">6</text>自我评价
									</view>
									<view class="edu-wrapper">
										<rich-text class="desc">
											{{ resume.introduction }}
										</rich-text>
									</view>
								</view>
							</view>
						</view>
						<view class="page">4/4</view>
					</swiper-item>
				</swiper>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				windowHeight: 0,
				resume: {
				  name:"吴哲",
				  spell:"Wu Zhe",
				  job:"WEB前端工程师",
				  exp:"3年工作经验",
				  tel: "18588750850",
				  sex: "男",
				  age: 27,
				  email: "wuzhe_@aliyun.com",
				  address: "深圳市福田区上沙街道龙秋路5巷24号",
				  skill:[
				    { name: "Java", percent:85},
				    { name: "PHP", percent: 40 },
				    { name: "HTML/CSS/JavaScript", percent: 90 },
				    { name: "Python", percent: 70 },
				    { name: "大数据", percent: 60 }
				  ],
				  education:[
				    {
				      school:"荆州职业技术学院",
				      major:"软件工程",
				      year:"2014-2018",
				      desc:"本专业培养掌握计算机软件基本理论知识，熟悉软件开发和管理技术、能够在计算机软件领域中从事软件设计、开发和管理的高级人才。"
				    }
				  ],
				  work:[
				    {
				      company:"北京XX公司",
				      job:"程序员",
				      year:"2019/01-至今",
				      desc:"参与开发了XXX电商系统，担任程序员角色。主要的工作是负责广告投放、商品秒杀、商品拼团等模块的开发与维护，并且负责管理该项目的运维工作。"
				    },
				    {
				      company: "北京XX公司",
				      job: "实习生",
				      year: "2018/03-2019/01",
				      desc: "参与了K13在线教育系统的开发和测试，维护腾讯云点播的API接口调用，并实现在线转码、添加水印、防盗链和盗播，并且开发和维护K13教育的微信小程序"
				    },
				    {
				      company: "北京航空航天大学创客学院",
				      job: "项目组长",
				      year: "2017/05-2018/01",
				      desc: "参与本校创新学院的Litemall微商城系统的开发，担任项目组长职务，参与了商品管理、订单管理、微信支付、购物车等模块的设计与开发。"
				    }
				  ],
				  project:[
				    {
				      name:"XXX电商系统",
				      desc:"该电商系统是O2O类型的新零售电商系统，分为购物子系统、支付子系统、数据库子系统、安全子系统、库存子系统、物流子系统和财务子系统。核心架构采用了SpringCloud微服务架构，整合了上述若干子系统。技术栈包括了SpringMVC、MyBatis、Activiti、Shiro、QuartZ、Sculptor Boot、jabdp、jee-weapp、RocketMQ、Kafka、Selenium、Echart、Vue、Element-UI、Uni-APP、Swagger、ElasticSearch、Druid、Zookeeper，数据平台选择的是两种MySQL集群（Replication、PXC），由MyCat管理，同时对MyCat做双机热备。NoSQL采用的是Redis Cluster集群和MongoDB集群"
				    },
				    {
				      name:"XXX K13在线教育系统",
				      desc:"该系统是针对中小学生提供的K13在线教育系统，采用的是视频点播形式，分为B/S形式和C/S形式。我主要负责的是教学视频管理业务。授课教师向K13平台上传教学视频后，经过专业人员剪辑之后，由K13平台调用腾讯云点播API接口，来实现在线转码和压缩，并且添加水印，最后生成防盗播的URL路径，渲染到HTML网页或者APP上面。该系统使用的技术栈包括SpringBoot、SpringMVC、MyBatis、SpringSecurity、Kafka、QuartZ、Flowable，该系统最终部署在腾讯云平台。"
				    },
				    {
				      name:"北京航空航天大学创客学院",
				      desc:"Litemall微商城系统是本校创新学院联合北京XX商超集团联合打造的B2C电商系统，该系统采用前后端分离的架构设计，一共分为5个子系统，分别是微商城前后台系统、商城管理前后台系统、商城核心系统。业务上具备微商城所有的功能，包括微信支付。技术架构上面后台项目选择的SpringBoot、SpringMVC和MyBatis组成的SSM框架，并且融合了Shiro、Swagger、PowerMock、阿里云等技术。前端项目采用了VUE+ElementUI技术架构，小程序采用的微信原生框架。Litemall微商城采用分布式集群部署，发布在DockerSwarm环境中，并且实现高负载、高性能和高可用。"
				    }
				  ],
				  introduction:"本人性格开朗、稳重、有活力，待人热情、真诚；对待工作认真负责，善于沟通、协调有较强的组织能力与团队精神；上进心强、勤于学习能不断提高自身的能力与综合素质。在未来的工作中，我将以充沛的精力，刻苦钻研的精神来努力工作，稳定地提高自己的工作能力，与企业同步发展。"
				}
			}
		},
		onShow() {
			const sysIfno = uni.getSystemInfoSync()
			const width = sysIfno.windowWidth
			const height = sysIfno.windowHeight
			this.windowHeight = height
		},
		onLoad() {

		},
		// 分享给朋友
		onShareAppMessage () {
			return {
				title: '吴哲的简历',
				path: '/pages/index/index'
			}
		},
		// 分享到朋友圈
		onShareTimeline () {
			return {
				title: '吴哲的简历'
			}
		},
		methods: {

		}
	}
</script>
<style>
	page {
		height: 100%;
		word-wrap: break-word;
		word-break: break-all;
	}
</style>
<style lang="scss" scoped>
.uni-padding-wrap
.page-section,
.page-section-spacing,
.swiper,
.content
.swiper-item {
	height: 100%;
}

.arrow-right {
	width: 20px;
	height: 20px;
}
.photo {
	position: absolute;
	bottom: 0;
	display: block;
	height: 80%;
	margin: 0 auto;
}
.name-wrapper {
	position: absolute;
	left: 50px;
	top: 30px;
	& > .name,
	& > .name-spell {
		display: block;
		letter-spacing: 1px;
	}
	& > .name {
		font-size: 30px;
		font-weight: bold;
		letter-spacing: 10px;
	}
	& > .name-spell {
		font-size: 18px;
	}
}
.naigation {
	position: absolute;
	top: 40px;
	right: 10px;
	font-size: 18px;
}
.large-circle,
.medium-circle,
.small-circle {
	position: absolute;
	background-color: rgba(0, 165, 34, 0.7);
	border-radius: 50%;
}
.large-circle {
	width: 260px;
	height: 260px;
	left: -150px;
	top: 110px;

}
.medium-circle {
	width: 160px;
	height: 160px;
	right: -80px;
	top: 110px;

}
.small-circle {
	width: 50px;
	height: 50px;
	left: -10px;
	bottom: 110px;
}
.arrow-right {
	display: inline-block;
	vertical-align: middle;
}
.job-info {
	width: 100%;
	position: absolute;
	bottom: 200px;
	padding: 20px 0;
	text-align: center;
	color: #fff;
	background-color: rgba(0,0,0,0.2);
	.font-end {
		font-size: 30px;
		font-weight: bold;
	}
	.job-year {
		font-size: 20px;
	}
}

.school-img {
	width: 26px;
}
.comm-img {
	width: 16px;
	margin-right: 3px;
}

/* 基本资料 */
.dashed-border {
	border-bottom: dashed 1px #333;
}
.base-info {
	.area {
		margin-bottom: 30px;
	}
	.row {
		padding: 10px 0;
		.fill {
			text-align: left;
		}
	}
}
.content-wrapper {
	padding: 0 20px;
}
.theme {
	margin: 10px 0;
	padding-bottom: 5px; 
	border-bottom: 1px solid #333;
	font-size: 20px;
	.number {
		display: block;
		width: 22px;
		height: 22px;
		font-size: 16px;
		line-height: 22px;
		text-align: center;
		font-weight: bold;
		background-color: #444;
		color: #fff;
		margin-right: 10px;
	}
}
.edu-wrapper {
	padding: 10px 0;
	.school {
		margin-bottom: 10px;
		.school-img {
			vertical-align: -6px;
			margin-right: 3px;
			
		}
	}
	.content {
		margin-bottom: 10px;
	}
	.desc {
		color: #999;
		line-height: 1.5;
	}
}
.page {
	width: 100%;
	font-size: 16px;
	text-align: center;
	padding-bottom: 15px;
}
</style>

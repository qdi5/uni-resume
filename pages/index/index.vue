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
									<view class="page">1/3</view>
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
									<view class="page">2/3</view>
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
									<view class="page">3/3</view>
								</div>
							</scroll-view>
						</view>
					</swiper-item>
					<!-- <swiper-item>
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
					</swiper-item> -->
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
				  exp:"5年工作经验",
				  tel: "18588750850",
				  sex: "男",
				  age: 28,
				  email: "ahafe@wo.cn",
				  address: "深圳市福田区沙头街道上沙龙秋村",
				  skill:[
				    { name: "Vue", percent: 85 },
				    { name: "HTML/CSS/JavaScript/jQuery", percent: 80 },
                    { name: "Webpack", percent: 65 },
				    { name: "Node", percent: 60 },
				    { name: "MySql", percent: 50 }
				  ],
				  education:[
				    {
				      school:"荆州职业技术学院",
				      major:"国际信息技术",
				      year:"2012-2015",
				      desc:"软件技术专业，Java Web方向。"
				    }
				  ],
				  work:[
				    {
				      company:"深圳市窝库新实业有限公司",
				      job:"前端开发工程师",
				      year:"2019/05-至今",
				      desc:"负责公司的app、ERP、微信公众号和小程序的开发。"
				    },
				    {
				      company: "深圳市畅飞扬信息系统有限公司",
				      job: "前端开发工程师",
				      year: "2018/03-2019/04",
				      desc: "参与公司电子档案管理系统开发"
				    },
				    {
				      company: "广州聚超软件科技有限公司",
				      job: "前端开发工程师",
				      year: "2015/08-2017/06",
				      desc: "参与公司物料管理系统开发"
				    }
				  ],
				  project:[
				    {
				      name:"窝库APP",
				      desc:"这是一个租房类的混合app，主要功能有实名认证、预约看房、在线签约、在线支付，维修保洁、智能门锁。"
				    },
				    {
				      name:"窝库管家",
				      desc:"这是一个h5 webapp项目，在微信公众号与小程序里面使用。主要是公司的业务员使用，方便管理我司的所有合同，根据公司的业务发展开发对应的功能模块提升业务员的工作效率。主要模块有合同签约、实名审核、电子收据、窝库服务；"
				    },
				    {
				      name:"窝库ERP",
				      desc:"这是公司PC端的内部管理系统；主要功能有房源管理、合同管理、财务管理、账单管理、智能门锁管理。"
				    },
                    {
                      name:"Express博客",
                      desc:"独立实现一个前后端分离的博客项目；主要功能有第三方登录、博客管理、分享、评论和回复。使用的技术栈：Express + Vue + MySQL"
                    },
                    {
                      name:"Vue音乐播放器",
                      desc:"高仿慕课网明星项目音乐Web app；无UI框架，纯手写css、js；核心功能有歌曲播放、歌词同步，快进快退等等。"
                    }
				  ]
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
    min-height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
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

<template>
	<view>
		<!-- date -->
		<button class="margin10px_0" type="primary" @tap="changeShow('QS_Picekr_date')">日期时间</button>
		<QSpicker 
		title="请选择日期时间" 
		mode="bottom" 
		type="date" 
		ref="QS_Picekr_date"
		pickerId="date_1" 
		:dataSet="dateSet" 
		showReset
		:autoHide="false"
		contentColor="#33cc33"
		:lineHeight=".05"
		@hideQSPicker="hideQSPicker($event)" @showQSPicker="showQSPicker($event)" @confirm="confirm($event)" />
		<!-- city -->
		<button class="margin10px_0" type="primary" @tap="changeShow('QS_Picekr_city')">省、市、区</button>
		<QSpicker type="city" ref="QS_Picekr_city" mode="top" top="200px" pickerId="city_1" :dataSet="citySet" showReset @hideQSPicker="hideQSPicker($event)"
		 @showQSPicker="showQSPicker($event)" @confirm="confirm($event)" />
		<!-- provincialStreet -->
		<button class="margin10px_0" type="primary" @tap="changeShow('QS_Picekr_provincialStreet')">省、市、区、街道</button>
		<QSpicker type="provincialStreet" ref="QS_Picekr_provincialStreet" mode="middle" pickerId="provincialStreet_1" :dataSet="provincialStreetSet"
		 @hideQSPicker="hideQSPicker($event)" @showQSPicker="showQSPicker($event)" @confirm="confirm($event)" />
		<!-- custom -->
		<button class="margin10px_0" type="primary" @tap="changeShow('QS_Picekr_custom_1')">custom无联动</button>
		<button class="margin10px_0" type="primary" @tap="changeShow('QS_Picekr_custom_2')">custom二级联动</button>
		<button class="margin10px_0" type="primary" @tap="changeShow('QS_Picekr_custom_3')">custom三级联动</button>
		<QSpicker type="custom" ref="QS_Picekr_custom_1" pickerId="custom_1" :dataSet="customSet_1" showReset @hideQSPicker="hideQSPicker($event)"
		 @confirm="confirm($event)" />
		<QSpicker type="custom" ref="QS_Picekr_custom_2" pickerId="custom_2" :dataSet="customSet_2" showReset @hideQSPicker="hideQSPicker($event)"
		 @confirm="confirm($event)" />
		<QSpicker type="custom" ref="QS_Picekr_custom_3" pickerId="custom_3" :dataSet="customSet_3" @hideQSPicker="hideQSPicker($event)"
		 @showQSPicker="showQSPicker($event)" @confirm="confirm($event)" />
		<!-- custom2 -->
		<button class="margin10px_0" type="primary" @tap="changeShow('QS_Picekr_custom2_1')">custom2无联动</button>
		<button class="margin10px_0" type="primary" @tap="changeShow('QS_Picekr_custom2_2')">custom2二级联动</button>
		<button class="margin10px_0" type="primary" @tap="changeShow('QS_Picekr_custom2_3')">custom2三级联动</button>
		<QSpicker type="custom2" ref="QS_Picekr_custom2_1" pickerId="custom2_1" :dataSet="custom2Set_1" showReset
		 @hideQSPicker="hideQSPicker($event)" @showQSPicker="showQSPicker($event)" @confirm="confirm($event)" />
		<QSpicker type="custom2" ref="QS_Picekr_custom2_2" pickerId="custom2_2" :dataSet="custom2Set_2" showReset
		 @hideQSPicker="hideQSPicker($event)" @showQSPicker="showQSPicker($event)" @confirm="confirm($event)" />
		<QSpicker type="custom2" ref="QS_Picekr_custom2_3" pickerId="custom2_3" :dataSet="custom2Set_3" @hideQSPicker="hideQSPicker($event)"
		 @showQSPicker="showQSPicker($event)" @confirm="confirm($event)" />
	</view>
</template>

<script>
	import QSpicker from '@/components/QuShe-picker/QuShe-picker.vue';
	export default {
		components: {
			QSpicker
		},
		data() {
			return {
				title: 'Hello',
				dateSet: {
					dateMode: 3,
					dateFormatArray: ['/', '/', ' ', ':', ':']
				},
				citySet: {
					defaultValue: [0, 0, 0]
				},
				provincialStreetSet: {
					defaultValue: [0, 0, 0, 0]
				},
				customSet_1: {},
				customSet_2: {
					linkage: true,
					linkageNum: 2,
					itemArray: [{
						value_1: "蔬菜", //value_1变量名需与下方steps.steps_1_value相同
						/*
						可添加多项自定义想要的数据
						*/
						item_2: ["青菜"] //item_2变量名需与下方steps.steps_2_item相同
					}, {
						value_1: "荤菜",
						item_2: ["猪肉"]
					}],
					steps: {
						step_1_value: "value_1",
						step_2_item: "item_2"
					},
				},
				customSet_3: {
					itemArray: [{
						value_1: "江西", //value_1变量名需与下方steps.steps_1_value相同
						/*
						可添加多项自定义想要的数据
						*/
						item_2: [{ //item_2变量名需与下方steps.steps_2_item相同
							value_2: "南昌", //value_2变量名需与下方steps.steps_2_value相同
							/*
							可添加多项自定义想要的数据
							*/
							item_3: [{ //item_3变量名需与下方steps.steps_3_item相同
								name: "东湖", //name变量名需与下方steps.steps_3_value相同
								/*
								可添加多项自定义想要的数据
								*/
							}]
						}, {
							value_2: "九江",
							item_3: [{
								"name": "德安"
							}]
						}]
					}, {
						value_1: "山东",
						item_2: [{
							value_2: "济南",
							item_3: [{
								name: "历下"
							}],
						}, {
							value_2: "青岛",
							item_3: [{
								name: "市南"
							}]
						}]
					}],
					steps: {
						step_1_value: "value_1",
						step_2_value: "value_2",
						step_2_item: "item_2",
						step_3_value: "name",
						step_3_item: "item_3"
					},
					linkageNum: 3, //3 表示为3级联动
					linkage: true //true 表示开启联动
				},
				custom2Set_1: {
					itemArray: [
						[{
							name: "a", //name变量名需与下方steps.steps_1_value相同
							value: "a" //可添加多项自定义想要的数据
						}, {
							name: "b",
							value: "b"
						}, {
							name: "c",
							value: "c"
						}],
						[{
							name: "d",
							value: "d"
						}, {
							name: "e",
							value: "e"
						}, {
							name: "f",
							value: "f"
						}]
					],
					steps: {
						step_1_value: "name", //第一级显示的属性名
						step_2_value: "", //第二级显示的属性名
						step_3_value: "" //第三级显示的属性名
					},
					defaultValue: [0, 0] //初始数据
				},
				custom2Set_2: {
					itemObject: {
						step_1: [{
							name: "蔬菜",
							value: "001"
						}, {
							name: "荤菜",
							value: "002"
						}],
						step_2: [
							["青菜", "白菜"], //对应step_1的蔬菜
							["猪肉", "牛肉"] //对应step_1的荤菜
						]
					},
					steps: {
						step_1_value: "name", //第一级显示的属性名
						step_2_value: "", //第二级显示的属性名
						step_3_value: "" //第三级显示的属性名
					},
					defaultValue: [1, 0], //初始数据
					linkageNum: 2, //3 表示为3级联动
					linkage: true //true 表示开启联动
				},
				custom2Set_3: {
					itemObject: {
						step_1: [{
							name: "江西"
						}, {
							name: "山东"
						}],
						step_2: [
							["南昌", "九江"], //对应step_1的江西
							["济南", "青岛"] //对应step_1的山东
						],
						step_3: [
							[
								[ //对应step_2的南昌
									"东湖"
								],
								[ //对应step_2的九江
									"德安"
								]
							],
							[
								[ //对应step_2的济南
									"历下",
								],
								[ //对应step_2的青岛
									"市南",
								]
							]
						]
					},
					steps: {
						step_1_value: "name", //第一级显示的属性名
						step_2_value: "", //第二级显示的属性名
						step_3_value: "" //第三级显示的属性名
					},
					defaultValue: [1, 0, 0], //初始数据
					linkageNum: 3, //3 表示为3级联动
					linkage: true //true 表示开启联动
				}
			}
		},
		onReady() {
			this.customSet_1 = {
				itemArray: [
					[{
						"name": "a", //name变量名需与下方steps.steps_1_value相同
						"value": "a" //可添加多项自定义想要的数据
					}, {
						"name": "b",
						"value": "b"
					}, {
						"name": "c",
						"value": "c"
					}],
					[{
						"name": "d",
						"value": "d"
					}, {
						"name": "e",
						"value": "e"
					}, {
						"name": "f",
						"value": "f"
					}]
				],
				defaultValue: [0, 0], //初始数据
				steps: {
					step_1_value: "name"
				}
			}
		},
		methods: {
			changeShow(name) {
				this.$refs[name].show();
			},
			showQSPicker(res) {
				console.log(`pickerId为${res.pickerId},类型为${res.type}的QS-picker显示了`);
			},
			hideQSPicker(res) {
				console.log(`pickerId为${res.pickerId},类型为${res.type}的QS-picker隐藏了了`);
			},
			confirm(res) {
				console.log('获取了用户选择----->' + JSON.stringify(res));
			}
		}
	}
</script>

<style scoped>
	.margin10px_0 {
		margin: 10px 0;
	}
</style>

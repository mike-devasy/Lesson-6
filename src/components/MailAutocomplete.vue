<template>
 <label >
	{{ title }}
	<input ref="userMail" v-model.lazy="userMail"   type="email" >
 </label>
</template>

<script>
 import {userNameList} from '../constants/data'
	export default {
		name:'MailAutoComplete',
		props: {
			title:{
				type:String,
				default:'Введіть свій email'
			},
		
			currentMail: {
				type: String,
				required:true,
				default:'' 
			},
			currentMailModifiers:{
				default:() => ({})
			}
		},
		data() {
			return {
				userNameList,
				mailPostfix: '@inv.mn.edu'
		}
	},
		computed:{
			userMail:{
				get(){
					return this.currentMail
				},
				set(val){
 if(this.userNameList.includes(val) && this.currentMailModifiers.check){
	val+= this.mailPostfix
	this.$refs.userMail.value = val
	console.log('val2');
	console.log(val);
 }
 else this.$refs.userMail.style.backgroundColor = 'red'
 return this.$emit('update:currentMail', val)
				}
			}
		},
// 		methods:{
// addPostfix(){
// 	if(this.currentMail){
// 	return 	this.currentMail += this.mailPostfix
// 	}
// }
// 		}
	}
</script>

<style lang="scss" scoped>

</style>
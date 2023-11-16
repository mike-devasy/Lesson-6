<template>
<label >
	{{ title }}
	<input  v-model.lazy="pathValue"   :class="{'error': !isRightPath}"  type="text" >
</label>
</template>

<script>
	export default {
		name:'PathInput',
		props: {
			title:{
				type:String,
				default:'Введіть путь до файлу JS:'
			},
			currentPath: {
				type: String,
				default: ''
			},
			// eslint-disable-next-line vue/require-prop-types
			currentPathModifiers:{
				default:() => ({})
			}
		},
		computed:{
			pathValue:{
				get(){
					return this.currentPath
				},
				set(val){
					console.log('val');
					console.log(val);
					// if(this.currentPathModifiers.checkPath && !(val  && /^\.\/(?:\w+\/)*\w+\.js$/.test(val)) )
					// {this.$refs.pathValue.style.backgroundColor = 'red'}
					// else {this.$refs.pathValue.style.backgroundColor = 'white'} 
					this.$emit('update:currentPath', val)
				}
			},
			isRightPath(){
				if (!this.pathValue)
				{return true}
	    	else if(this.currentPathModifiers.checkPath)
				{return this.getRightPath(this.pathValue)}
				 else return true
				}
		},
		methods:{
			getRightPath(val) {
   return /^\.\/(?:\w+\/)*\w+\.js$/.test(val);
			}
		}
	}
</script>

<style lang="css" scoped>
.error{
	background-color: red;
}
</style>
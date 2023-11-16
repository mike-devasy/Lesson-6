<!-- eslint-disable vue/require-prop-types -->
<template>
    <label>
        {{ title }}
        <input ref="ageValue" v-model="ageValue" type="number" :placeholder="errorMessage" />
    </label>
</template>

<script>
export default {
    name: 'AgeInput',
    props: {
        title: {
            type: String,
            default: '',
        },
        currentUserAge: {
            type: Number,
						default:0
        },
				// eslint-disable-next-line vue/require-prop-types
				currentUserAgeModifiers: {
            default: () => ({}),

        },
    },
		data(){
			return{
				errorMessage:''
			}
		},
		computed:{
 
			ageValue:{
				get(){
					return  this.currentUserAge
				},
				set(val){
					if(val > 150 && this.currentUserAgeModifiers.check) {
            this.errorMessage = ' '
						// val = 0
						this.$refs.ageValue.disabled = true
					}
					else {
						this.$refs.ageValue.disabled = false

					if(val <= 10 && this.currentUserAgeModifiers.setColor){this.$refs.ageValue.style.backgroundColor = 'green'}
					else if(val <= 21 && this.currentUserAgeModifiers.setColor){
						 this.$refs.ageValue.style.backgroundColor = 'yellow'
					}
          else if(this.currentUserAgeModifiers.setColor){
						 this.$refs.ageValue.style.backgroundColor = 'orange'
					}
					this.$emit('update:currentUserAge', val)
					}
				}
				}
			}
}

</script>

<style lang="scss" scoped></style>

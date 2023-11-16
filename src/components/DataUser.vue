<template>
    <div class="user-data">
        <label>
            {{ titleName }}
            <input ref="nameValue" type="text" v-model.lazy="nameValue" />
        </label>
        <label>
            {{ titleAge }}
            <input ref="ageValue" type="number" v-model.lazy="ageValue" />
        </label>
    </div>
</template>

<script>
export default {
    name: 'DataUser',
    props: {
        titleName: {
            type: String,
            default: 'Ваше имя:',
        },
        titleAge: {
            type: String,
            default: 'Ваш вік:',
        },
        currentName: {
            type: String,
            default: '',
        },
        currentNameModifiers: {
            default: () => ({}),
        },
        currentDataUserAge: {
            type: Number,
            default: null,
        },
				currentDataUserAgeModifiers: {
            default: () => ({}),
        },
    },
    computed: {
        ageValue: {
            get() {
                return this.currentDataUserAge
            },
            set(val) {
if(val && this.currentDataUserAgeModifiers.checkAge){
	if (val < 18){
		this.$refs.ageValue.style.backgroundColor = 'red'
	}
	else     this.$refs.ageValue.style.backgroundColor = 'green'
}

return this.$emit('update: currentDataUserAge', val)
						},
        },
        nameValue: {
            get() {
                return this.currentName
            },
            set(val) {
                if (!val && this.currentNameModifiers.checkName) {
                    this.$refs.nameValue.style.backgroundColor = 'red'
                }
                return this.$emit('update: currentName', val)
            },
        },
    },
}
</script>

<style lang="scss" scoped></style>

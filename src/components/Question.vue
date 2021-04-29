<template>
	<div class="question__container">
		<span class="threshold">
			{{ field.low }}
		</span>
		<v-radio-group
			v-model="selected"
			v-validate="'required'"
			row
		>
			<v-radio
				label=""
				value="1"
			></v-radio>
			<v-radio
				label=""
				value="2"
			></v-radio>
			<v-radio
				label=""
				value="3"
			></v-radio>
			<v-radio
				label=""
				value="4"
			></v-radio>
			<v-radio
				label=""
				value="5"
			></v-radio>
			<v-radio
				label=""
				value="6"
			></v-radio>
			<v-radio
				label=""
				value="7"
			></v-radio>
		</v-radio-group>
		<span class="threshold">
			{{ field.high }}
		</span>
	</div>
</template>

<script>
export default{
	inject: ['$validator'],

	props: {
		field: {
			type: Object,
			default: () => {},
		},
	},

	data() {
		return {
			selected: '',
		}
	},
}
</script>

<style lang="scss" scoped>
.question__container {
	display: flex;
	justify-content: space-between;
	align-items: center;
}

.threshold {
	width: 100px;
}
</style>

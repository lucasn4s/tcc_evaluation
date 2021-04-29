<template>
	<v-container>
		<div
			v-for="field in question.fields"
			:key="field.value"
		>
			<question :field="field" />
		</div>
	</v-container>
</template>

<script>
import Question from './Question.vue';

export default {
	inject: ['$validator'],

	components: {
		Question,
	},

	props: {
		question: {
			type: Object,
			default: () => {},
		},
	},
}
</script>

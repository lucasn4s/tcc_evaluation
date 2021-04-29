<template>
	<div>
		<question-block
			ref="programatic"
			v-if="currentStep === 0"
			:question="questions.pq"
		/>
		<question-block
			ref="hedonic-1"
			v-if="currentStep === 1"
			:question="questions.hq_i"
		/>
		<question-block
			ref="hedonic-2"
			v-if="currentStep === 2"
			:question="questions.hq_s"
		/>
		<question-block
			ref="activity"
			v-if="currentStep === 3"
			:question="questions.att"
		/>
		<div class="navigation__buttons">
			<v-btn
				v-if="currentStep !== 0"
				class="mr-5"
				color="secondary"
				elevation="2"
				@click="handleNavigation('back')"
			>
				Anterior
			</v-btn>
			<v-btn
				color="success"
				elevation="2"
				@click="handleNavigation('next')"
			>
				{{ currentStep === 3 ? 'Finalizar' : 'Próximo' }}
			</v-btn>
		</div>
	</div>
</template>

<script>
import QuestionBlock from '../components/QuestionBlock.vue';
import questions from '../utils/constants/questions';

const mapSteps = [
	'programatic',
	'hedonic-1',
	'hedonic-2',
	'activity'
];

export default {
	components: { QuestionBlock },

	data() {
		return {
			questions,
			currentStep: 0,
		};
	},

	methods: {
		handleNavigation(value) {
			if (value === 'next' && this.currentStep !== 3) {
				this.$refs[mapSteps[this.currentStep]].validate()
					.then(valid => {
						if (!valid) {
						// do stuff if not valid.
						}
					})
				this.currentStep += 1;
				return;
			}

			if (value === 'back') {
				this.currentStep -= 1;
				return;
			}

			console.log('last');
		},
	},
}
</script>

<style lang="scss" scoped>
.navigation__buttons {
	display: flex;
	justify-content: flex-end;
	margin-right: 15px;
}
</style>

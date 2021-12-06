<template>
	<div class="cv-header">
		<div class="cv-header-nav">
			<button
				:disabled="!headerProps.previousYear"
				class="previousYear"
				aria-label="Previous Year"
				@click.prevent="onInput(headerProps.previousYear)"
			>
				{{ previousYearLabel }}
			</button>
			<button
				:disabled="!headerProps.previousPeriod"
				class="previousPeriod"
				aria-label="Previous Period"
				@click.prevent="onInput(headerProps.previousPeriod)"
				v-html="previousPeriodLabel"
			/>
			<button
				class="currentPeriod"
				aria-label="Current Period"
				@click.prevent="onInput(headerProps.currentPeriod)"
			>
				{{ headerProps.currentPeriodLabel }}
			</button>
			<button
				:disabled="!headerProps.nextPeriod"
				class="nextPeriod"
				aria-label="Next Period"
				@click.prevent="onInput(headerProps.nextPeriod)"
			>
				{{ nextPeriodLabel }}
			</button>
			<button
				:disabled="!headerProps.nextYear"
				class="nextYear"
				aria-label="Next Year"
				@click.prevent="onInput(headerProps.nextYear)"
			>
				{{ nextYearLabel }}
			</button>
		</div>
		<div class="periodLabel">
			<slot name="label">{{ headerProps.periodLabel }}</slot>
		</div>
	</div>
</template>
<script>
export default {
	name: "CalendarViewHeader",
	props: {
		headerProps: {
			type: Object,
			required: true,
		},
		previousYearLabel: { type: String, default: "<<" },
		previousPeriodLabel: { type: String, default: "<" },
		nextPeriodLabel: { type: String, default: ">" },
		nextYearLabel: { type: String, default: ">>" },
	},
	methods: {
		onInput(d) {
			this.$emit("input", d)
		},
	},
}
</script>

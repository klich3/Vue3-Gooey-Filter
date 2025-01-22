<template>
	<svg aria-hidden="true" xmlns="http://www.w3.org/2000/svg" version="1.1">
		<defs>
			<filter id="goo-effect">
				<feGaussianBlur in="SourceGraphic" stdDeviation="10" result="blur" />
				<feColorMatrix
					in="blur"
					type="matrix"
					values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 31 -12"
					result="goo" />
				<feComposite in="SourceGraphic" in2="goo" operator="atop" />
			</filter>
		</defs>
	</svg>
</template>

<style>
.no-filter {
	filter: none !important;
}

.filter {
	filter: url(#goo-effect);
}

svg:not(:root) {
	overflow: hidden;
}
</style>

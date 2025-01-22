<template>
	<div class="wrap">
		<div class="filter">
			<div class="center-circle" style="top: 10px; left: 80px"></div>
			<div class="center-circle" style="top: 10%; left: 30%; background-color: red"></div>
			<div class="center-circle" style="top: 500px; left: 480px"></div>
			<div ref="pointerRef" class="mouse-pointer"></div>
		</div>

		<div class="container">
			<Logo class="no-filter" />
			<HelloWorld msg="Vite + Vue" class="no-filter" />
		</div>
	</div>

	<BGFilter />
</template>

<script setup>
import { onMounted, onUnmounted, ref } from "vue";
import HelloWorld from "@/components/HelloWorld.vue";
import Logo from "@/components/Logo.vue";
import BGFilter from "@/components/BGFilter.vue";

const pointerRef = ref(null);

onMounted(() => {
	window.addEventListener("pointermove", (event) => {
		pointerRef.value.style.top = event.y + "px";
		pointerRef.value.style.left = event.x + "px";
	});
});

onUnmounted(() => {
	window.removeEventListener("mousemove");
});
</script>

<style scoped>
.wrap {
	position: relative;
	width: 100%;
	height: 100%;
	display: block;
}

.wrap .container {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	min-height: 100vh;
}

.mouse-pointer {
	position: absolute;
	top: 0;
	left: 0;

	display: block;
	width: 20px;
	height: 20px;
	background-color: black;
}

.center-circle {
	position: absolute;

	display: block;
	width: 60px;
	height: 60px;

	background-color: black;
	border-radius: 50%;
}
</style>

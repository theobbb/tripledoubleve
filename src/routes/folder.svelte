<script>
	const { ...props } = $props();

	const viewbox = { w: 64, h: 48 };
	const stroke_width = 5;
	const s = stroke_width / 2;

	const w = viewbox.w - s;
	const h = viewbox.h - s;

	const left = 24 + s;
	const top = 12 - s;
</script>

<svg
	width="100%"
	height="100%"
	viewBox="0 0 {viewbox.w} {viewbox.h}"
	fill="none"
	style="transform: scale(1.5)"
	xmlns="http://www.w3.org/2000/svg"
>
	<path
		d="M{w} {h} V{top}H{left}L{left} {s}H{s}L{s} {top}V{h}H{w}Z"
		class={props.class}
		stroke-width={stroke_width}
	/>
</svg>

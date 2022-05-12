<nav>
	<a href="/">Movie Database</a>
	<div class="circle" />
</nav>

<style>
	nav {
		display: flex;
		min-height: 20vh;
		align-items: center;
		justify-content: center;
		position: relative;
	}
	a {
		font-size: 2rem;
		font-weight: bold;
		font-family: 'Poppins';
		text-decoration: none;
	}
	.circle {
		height: 200vh;
		width: 300vh;
		border-radius: 50%;
		background: linear-gradient(to top, #c4c4c4, #659ed2);
		z-index: -1;
		position: absolute;
		top: 100%;
		filter: blur(2px);
		border-bottom: 13px;
	}
</style>

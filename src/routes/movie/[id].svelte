<script context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=e490f27027a76f819d324df2dc5235cb&language=en-US`
		);
		const movieDetail = await res.json();
		if (res.ok) {
			return {
				props: { movieDetail }
			};
		}
	}
</script>

<script>
	export let movieDetail;
	import { fly } from 'svelte/transition';
</script>

<div
	class="movie-details"
	in:fly={{ y: 50, duration: 500, delay: 500 }}
	out:fly={{ duration: 500 }}
>
	<div class="img-container">
		<img
			src={'https://image.tmdb.org/t/p/original' + movieDetail.backdrop_path}
			alt={movieDetail.title}
		/>
	</div>
	<div class="text-container">
		<h1>{movieDetail.title}</h1>
		<p class="overview">{movieDetail.overview}</p>
		<p>
			<span>Release Date:</span>
			{movieDetail.release_date} <br />
			<span>Budget:</span>
			{movieDetail.budget} <br />
			<span>Rating</span>
			{movieDetail.vote_average} <br />
			<span>Runtime:</span>
			{movieDetail.runtime} mins <br />
		</p>
	</div>
</div>

<style>
	h1 {
		padding: 1rem 0rem 2rem;
	}
	p {
		padding: 1rem 0rem;
	}
	.img-container {
		width: 100%;
	}
	.text-container {
		background-color: #45494e;
		padding: 2rem;
		border-radius: 10px;
		margin-top: 2rem;
	}
	img {
		width: 100%;
		border-radius: 1rem;
	}
	.movie-details {
		margin: 7rem 20%;
	}
	span {
		font-weight: bold;
	}
</style>

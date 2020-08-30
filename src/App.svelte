<script>
	import TailwindStyles from './TailwindStyles.svelte';

	import { Observable } from 'rxjs';

	const message = 'Learn Svelte';



	const observable = new Observable(subscriber => {
	subscriber.next(1);
	subscriber.next(2);
	subscriber.next(3);
	setTimeout(() => {
		subscriber.next(4);
		subscriber.complete();
	}, 1000);
	});
 
	console.log('just before subscribe');
	observable.subscribe({
  		next(x) { console.log('got value ' + x); },
  		error(err) { console.error('something wrong occurred: ' + err); },
  		complete() { console.log('done'); }
	});
	console.log('just after subscribe');

</script>

<style>
	.App-logo {
		animation: App-logo-scale infinite 1.6s ease-in-out alternate;
	}
	@keyframes App-logo-scale {
		from {
			transform: scale(1);
		}
		to {
			transform: scale(1.06);
		}
	}
</style>

<div class="text-center font-serif">
	<header class="bg-gray-100 h-screen flex justify-center items-center flex-col text-3xl">
		<img src="/logo.svg" class="App-logo pointer-events-none m-4 h-64" alt="logo" />
		<p>
			Edit <code>src/App.svelte</code> and save to reload.
		</p>
		<p>Another line of text</p>
		<a
			class="text-orange-500"
			href="https://svelte.dev"
			target="_blank"
			rel="noopener noreferrer"
		>
			{message}
		</a>
	</header>
</div>
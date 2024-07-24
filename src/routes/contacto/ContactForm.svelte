<script lang="ts">
	import { cn } from '$lib/utils';
	import { onMount } from 'svelte';

	let status = '';
	let name = '';
	let email = '';
	let message = '';

	let showEmptyNameFeedback = false;
	let showEmptyEmailFeedback = false;
	let showInvalidEmailFeedback = false;
	let showEmptyMessageFeedback = false;

	const handleSubmit = async (event: Event) => {
		event.preventDefault();

		if (!validateForm()) {
			return;
		}

		status = 'Enviando...';

		const formData = {
			access_key: '26d83811-fc9b-452f-840b-2401d8a67514',
			subject: 'MENSAJE DE CONTACTO WEB DE ESTRUGAMOU',
			name,
			email,
			message
		};

		try {
			const response = await fetch('https://api.web3forms.com/submit', {
				method: 'POST',
				headers: {
					'Content-Type': 'application/json',
					Accept: 'application/json'
				},
				body: JSON.stringify(formData)
			});

			const result = await response.json();
			if (result.success) {
				status = '¡Mensaje Enviado!';
			} else {
				status = 'Ocurrió un error. Intentalo de nuevo.';
			}
		} catch (error) {
			console.error('Error sending message:', error);
			status = 'Ocurrió un error. Intentalo de nuevo.';
		}
	};

	const validateForm = () => {
		showEmptyNameFeedback = false;
		showEmptyEmailFeedback = false;
		showInvalidEmailFeedback = false;
		showEmptyMessageFeedback = false;
		let isValid = true;

		if (!name.trim()) {
			showEmptyNameFeedback = true;
			isValid = false;
		}
		if (!email.trim()) {
			showEmptyEmailFeedback = true;
			isValid = false;
		} else if (!isValidEmail(email.trim())) {
			showInvalidEmailFeedback = true;
			isValid = false;
		}
		if (!message.trim()) {
			showEmptyMessageFeedback = true;
			isValid = false;
		}

		return isValid;
	};

	const isValidEmail = (email: string) => {
		return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
	};

	// Clear status message after 5 seconds
	onMount(() => {
		const clearStatus = setTimeout(() => {
			status = '';
		}, 5000);

		return () => clearTimeout(clearStatus);
	});
</script>

<div class="flex h-fit">
	<div class="mx-auto flex-grow">
		<div
			class="mx-auto mt-10 max-w-xl bg-white/30 bg-opacity-80 p-2 font-jetbrains shadow-lg backdrop-blur-lg"
		>
			<div class="text-center">
				<h1 class="my-3 text-3xl font-semibold text-black">Contactanos</h1>
				<p class="text-black">Llená el formulario para enviarnos un mensaje con tu consulta.</p>
			</div>
			<div class="m-5">
				<form on:submit|preventDefault={handleSubmit} novalidate>
					<div class="mb-6 flex space-x-4">
						<div class="w-full md:w-1/2">
							<label for="full_name" class="mb-2 block text-sm text-black">Nombre completo</label>
							<input
								type="text"
								bind:value={name}
								id="full_name"
								placeholder="Nombre Apellido"
								class={'w-full border-2 border-gray-200 px-3 py-2 text-gray-800 placeholder-gray-300 placeholder:text-gray-700/50  focus:border-indigo-300 focus:outline-none focus:ring focus:ring-indigo-100 ' +
									(showEmptyNameFeedback ? 'border-red-400' : '')}
							/>
							{#if showEmptyNameFeedback}
								<p class="mt-1 text-sm text-red-900">Ingresá tu nombre completo.</p>
							{/if}
						</div>
						<div class="w-full md:w-1/2">
							<label for="email" class="mb-2 block text-sm text-black">Dirección de email</label>
							<input
								type="email"
								bind:value={email}
								id="email"
								placeholder="tu@correo.com"
								class={'w-full border-2 border-gray-200 bg-white/20 px-3 py-2 text-black placeholder:text-gray-700/50 focus:border-indigo-300 focus:outline-none focus:ring focus:ring-indigo-100 ' +
									(showEmptyEmailFeedback || showInvalidEmailFeedback ? 'border-red-400' : '')}
							/>
							{#if showEmptyEmailFeedback}
								<p class="mt-1 text-sm text-red-900">Ingresá tu dirección de email.</p>
							{/if}

							{#if showInvalidEmailFeedback}
								<p class="mt-1 text-sm text-red-900">Ingresá una dirección de email válida.</p>
							{/if}
						</div>
					</div>
					<div class="mb-6">
						<label for="message" class="mb-2 block text-sm text-black">Tu mensaje</label>
						<textarea
							bind:value={message}
							id="message"
							rows="5"
							placeholder="Tu mensaje"
							class={'w-full border-2 border-gray-200 px-3 py-2 text-gray-800 placeholder:text-gray-700/50  focus:border-indigo-300 focus:outline-none focus:ring focus:ring-indigo-100 ' +
								(showEmptyMessageFeedback ? 'border-red-400' : '')}
						></textarea>
						{#if showEmptyMessageFeedback}
							<p class="mt-1 text-sm text-red-900">Ingresá tu mensaje.</p>
						{/if}
					</div>
					<div class="mb-6">
						<button
							type="submit"
							class={'w-full px-3 py-4 text-white ' +
								(status
									? (status === 'Enviando...' || status === '¡Mensaje Enviado!')
										? 'pointer-events-none cursor-not-allowed bg-green-400'
										: 'bg-red-400'
									: 'bg-gray-800')}
						>
							{status ? status : 'Enviar Mensaje'}
						</button>
					</div>
				</form>
			</div>
		</div>
	</div>
</div>

<style>
	input:focus,
	textarea:focus {
		outline: none;
		border-color: #4f46e5;
	}
</style>

<script context="module">
    // export let path;  
	/** @type {import('@sveltejs/kit').Load} */
	export async function load({ params, fetch, session, stuff }) {
		const get_content_url = `https://api.github.com/repos/${params.repo}/contents/`
		const response = await fetch(get_content_url);
		const res = await response.json()
		return {
			status: response.status,
			props: {
				files:res
			}
		};
	}

</script>
<script>
	export let  files;
	console.log(files);

</script>


<div>
{#each files as file (file.name)}
	<a href="{file.download_url}" target="_blank">{file.name}</a>
{/each}
</div>
	
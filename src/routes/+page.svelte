<script>
import Textbox from './Textbox.svelte';
import glab from '$lib/glab.png';
import teaman from '$lib/teaman.png';
let t = '';
</script>

<div class="flex flex-col">
  <div class='p-4 mb-4'>
    <h1 class='text-center mb-2 text-3xl font-bold'>glabophorb</h1>
    <div>
      <img class='max-w-xs mx-auto rounded-xl transition-all duration-300 filter grayscale hover:grayscale-0' src={teaman} alt="glabophorbs" />
    </div>
  </div>
  <div class='mx-auto'>
    <Textbox bind:text={t} />
  </div>
  <p class="mt-4 text-xl text-center">reactive update says you typed: </p>
  <p class="text-center italic">{t}</p>
</div>


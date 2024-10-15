<script lang="ts">
  import { onMount } from 'svelte';
  export let analyticsId:string ='';

  onMount(async () => {
    const script = document.createElement('script');
    script.innerHTML = `
      window.dataLayer = window.dataLayer || [];
      function gtag() { dataLayer.push(arguments); }
      gtag('js', new Date());
      gtag('config', '${analyticsId}');
      `;
    document.head.appendChild(script);
  });
</script>

<svelte:head>
  <meta name="keywords" content="Nexolis, Lab Integration and Configuration Manager">
</svelte:head>
{#if !analyticsId}
  <h2>You need to provide your Google Analytics ID, "ANALYTICS_ID", in .env file.</h2>
  <p>Please read the <a href="https://runatics.codewithshin.com/">docs</a> how to set it up.</p>
{/if}
<script lang="ts">
    import { languageTag, onSetLanguageTag } from "$paraglide/runtime";
    import { page } from "$app/stores";
    import { i18n } from "$lib/utils/i18n";
    import { invalidateAll } from "$app/navigation";
    import { twMerge } from "tailwind-merge";
    import { browser } from "$app/environment";

    let clazz = "";
    export { clazz as class };

    if (browser) {
        onSetLanguageTag(() => {
            invalidateAll();
        });
    }

    let dialog: HTMLDialogElement;

    function show() {
        dialog.showModal();
    }

    function close() {
        dialog.close();
    }
</script>

<button
    class={twMerge("js btn btn-ghost", clazz)}
    on:click={show}
    aria-label="Open language picker"
>
    <span class="i-mdi-language size-6"></span>
</button>

<!--
<a
  class={twMerge("btn btn-ghost", clazz)}
  href={i18n.route($page.url.pathname)}
  hreflang={languageTag() === "sv" ? "en" : "sv"}
>
  <slot>
    {languageTag() === "sv" ? "EN" : "SV"}
  </slot>
</a>
-->

<!--class="h-full max-w-xl rounded-2xl bg-transparent pt-16 text-base-content md:w-full"-->

<dialog bind:this={dialog} on:click={close}>hejj</dialog>

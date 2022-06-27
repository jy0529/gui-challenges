<script setup lang="ts">
import ButtonComponent from "./components/button.vue";
</script>

<template>
    <div>
        <section>
            <h2>9 button types</h2>
            <p>Unified modern style, visual differences reinforce purpose.</p>
        </section>

        <article class="fluid-flex">
            <button-component>Default</button-component>
            <button-component>
                <svg viewBox="0 0 24 24" stroke="currentColor" width="24" height="24" aria-hidden="true">
                    <path
                        d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
                </svg>
                Icon
            </button-component>
            <button-component type="submit">Submit</button-component>
            <button-component type="button">Type Button</button-component>
            <button-component type="reset">Reset</button-component>
            <button-component disabled>Disabled</button-component>
            <button-component class="btn-custom">Custom</button-component>
            <button-component type="file"></button-component>
        </article>

        <section>
            <h2>When inside a <code>&#60;form&#62;</code></h2>
            <p>
                <span class="red-squigly">Untyped buttons</span> visually match their
                new contextual default of type submit.
            </p>
        </section>

        <form action="" class="fluid-flex">
            <button-component>Default</button-component>
            <button-component>Icon <span data-icon="cloud"></span></button-component>
            <button-component type="submit">Submit</button-component>
            <button-component type="button">Type Button</button-component>
            <button-component type="reset">Reset</button-component>
            <button-component disabled>Disabled</button-component>
            <button-component class="btn-custom btn-large" type="button">Large Custom</button-component>
            <button-component type="file"></button-component>
        </form>
    </div>
</template>

<style>
body {
    min-block-size: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 5vmin;
    padding-inline: 5vmin;
}

@media (width <=720px) {
    body {
        padding-block: 10vmin;
    }
}

body,
h2,
p {
    margin: 0;
}

form {
    background: hsl(210deg 16% 93%);
    border: 1px solid hsl(210deg 14% 89%);
    border-radius: .5ch;
}


.fluid-flex {
    display: flex;
    flex-wrap: wrap;
    place-content: center;
    align-items: flex-start;
    padding: 2ch;
    gap: 2ch;
}

section {
    display: grid;
    gap: 1ch;
    text-align: center;
}

.red-squigly {
    text-decoration: red underline wavy;
}

</style>
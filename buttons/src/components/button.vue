<script setup lang="ts">
    enum ButtonType {
        SUBMIT = 'submit',
        BUTTON = 'button',
        RESET = 'reset',
        FILE = 'file',
    };

    interface ButtonProps {
        type?: ButtonType,
    };

    const { type = ButtonType.BUTTON } = defineProps<ButtonProps>();

    const tag = type === ButtonType.FILE ? 'input' : 'button';

</script>

<template>
    <component :is="tag" :type="type">
        <slot></slot>
    </component>
</template>

<style>
:where(button,
    input[type="button"],
    input[type="submit"],
    input[type="reset"],
    input[type="file"]),
:where(input[type="file"])::file-selector-button {
    /* accent color */
    --_accent-light: hsl(210 100% 40%);
    --_accent-dark: hsl(210 50% 70%);
    --_accent: var(var(--_accent-light));

    /* text color */
    --_text-light: hsl(210 10% 30%);
    --_text-dark: hsl(210 5% 95%);
    --_text: var(--_text-light);

    /* bg color */
    --_bg-light: hsl(0 0% 100%);
    --_bg-dark: hsl(210 9% 31%);
    --_bg: var(--_bg-light);

    /* background well */
    --_input-well-light: hsl(210 16% 87%);
    --_input-well-dark: hsl(204 10% 10%);
    --_input-well: var(var(--_input-well-light));

    /* padding */
    --_padding-inline: 1.75ch;
    --_padding-block: .75ch;

    /* border */
    --_border-radius: .5ch;
    --_border-light: hsl(210 14% 89%);
    --_border-dark: var(--_bg-dark);
    --_border: var(--_border-light);

    /* hover highlight effect */
    --_highlight-size: 0;
    --_highlight-light: hsl(210 10% 71% / 25%);
    --_highlight-dark: hsl(210 10% 5% / 25%);
    --_highlight: var(--_highlight-light);

    /* text shadow */
    --_ink-shadow-light: 0 1px 0 var(--_border-light);
    --_ink-shadow-dark: 0 1px 0 hsl(210 11% 15%);
    --_ink-shadow: var(--_ink-shadow-light);

    /* icon */
    --_icon-size: 2ch;
    --_icon-color: var(--_accent);

    /* shadow */
    --_shadow-color-light: 220 3% 15%;
    --_shadow-color-dark: 220 40% 2%;
    --_shadow-color: var(--_shadow-color-light);

    --_shadow-strength-light: 1%;
    --_shadow-strength-dark: 25%;
    --_shadow-strength: var(--_shadow-strength-light);

    --_shadow-1: 0 1px 2px -1px hsl(var(--_shadow-color)/calc(var(--_shadow-strength) + 9%));
    --_shadow-2:
        0 3px 5px -2px hsl(var(--_shadow-color)/calc(var(--_shadow-strength) + 3%)),
        0 7px 14px -5px hsl(var(--_shadow-color)/calc(var(--_shadow-strength) + 5%));

    --_shadow-depth-light: 0 1px var(--_border-light);
    --_shadow-depth-dark: 0 1px var(--_bg-dark);
    --_shadow-depth: var(--_shadow-depth-light);

    /* transition */
    --_transition-motion-reduce: ;
    --_transition-motion-ok:
        box-shadow 145ms ease,
        outline-offset 145ms ease;
    --_transition: var(--_transition-motion-reduce);

    font: inherit;
    letter-spacing: inherit;
    line-height: 1.5;
    border-radius: var(--_border-radius);
}

@media (prefers-color-scheme: dark) {
    :where(button,
        input[type="button"],
        input[type="submit"],
        input[type="reset"],
        input[type="file"]),
    :where(input[type="file"])::file-selector-button {
        --_bg: var(--_bg-dark);
        --_text: var(--_text-dark);
        --_border: var(--_border-dark);
        --_accent: var(--_accent-dark);
        --_highlight: var(--_highlight-dark);
        --_input-well: var(--_input-well-dark);
        --_ink-shadow: var(--_ink-shadow-dark);
        --_shadow-depth: var(--_shadow-depth-dark);
        --_shadow-color: var(--_shadow-color-dark);
        --_shadow-strength: var(--_shadow-strength-dark);
    }
}

@media (prefers-reduced-motion: no-preference) {
    :where(button,
        input[type="button"],
        input[type="submit"],
        input[type="reset"],
        input[type="file"]),
    :where(input[type="file"])::file-selector-button {
        --_transition: var(--_transition-motion-ok);
    }
}

:where(button,
    input[type="button"],
    input[type="submit"],
    input[type="reset"]),
:where(input[type="file"])::file-selector-button {
    cursor: pointer;
    touch-action: manipulation;
    font-size: var(--_size, 1rem);
    font-weight: 700;
    background: var(--_bg);
    color: var(--_text);
    border: 2px solid var(--_border);

    box-shadow:
        var(--_shadow-2),
        var(--_shadow-depth),
        0 0 0 var(--_highlight-size) var(--_highlight);
    text-shadow: var(--_ink-shadow);

    display: inline-flex;
    justify-content: center;
    align-items: center;
    text-align: center;

    gap: 1ch;
    padding-block: var(--_padding-block);
    padding-inline: var(--_padding-inline);

    user-select: none;
    -webkit-tap-highlight-color: transparent;
    -webkit-touch-callout: none;

    transition: var(--_transition);
}

:where(button,
    input[type="button"],
    input[type="submit"],
    input[type="reset"]):where(:not(:active):hover) {
    --_highlight-size: .5rem;
}

:where(button, input):where(:not(:active)):focus-visible {
    outline-offset: 5px;
}

:where(button,
    input[type="button"],
    input[type="submit"],
    input[type="reset"])> :where(svg, [data-icon]) {
    block-size: var(--_icon-size);
    inline-size: var(--_icon-size);
    stroke: var(--_icon-color);
    filter: drop-shadow(var(--_ink-shadow));

    flex-shrink: 0;
    fill: none;
    stroke-linecap: round;
    stroke-linejoin: round;
}

:where([type="submit"],
    form button:not([type], [disabled])) {
    --_text: var(--_accent);
}

:where([type="reset"]) {
    --_border-light: hsl(0 100% 83%);
    --_highlight-light: hsl(0 100% 89% / 20%);
    --_text-light: hsl(0 80% 50%);
    --_text-dark: hsl(0 100% 89%);
}

:where([type="reset"]):focus-visible {
    outline-color: currentColor;
}

:where(button,
    input[type="button"],
    input[type="submit"],
    input[type="reset"])[disabled] {
    --_bg: none;
    --_text-light: hsl(210 7% 40%);
    --_text-dark: hsl(210 11% 71%);

    cursor: not-allowed;
    box-shadow: var(--_shadow-1);
}

:where(input[type="file"]) {
    inline-size: 100%;
    max-inline-size: max-content;
    background-color: var(--_input-well);
}

:where(input[type="button"]),
:where(input[type="file"])::file-selector-button {
    appearance: none;
}

@media (prefers-color-scheme: dark) {

    :where([type="submit"],
        [type="reset"],
        [disabled],
        form button:not([type="button"])) {
        --_bg: var(--_input-well);
    }
}

/* custom button */

.btn-custom {
    --_bg: linear-gradient(hsl(228 94% 67%), hsl(228 81% 59%));
    --_border: hsl(228 89% 63%);
    --_text: hsl(228 89% 100%);
    --_ink-shadow: 0 1px 0 hsl(228 57% 50%);
    --_highlight: hsl(228 94% 67% / 20%);
}

.btn-large {
    --_size: 1.5rem;
}

[data-icon="cloud"] {
    --icon-cloud: url("https://api.iconify.design/mdi:apple-icloud.svg") center / contain no-repeat;

    -webkit-mask: var(--icon-cloud);
    mask: var(--icon-cloud);
    background: linear-gradient(to bottom, var(--_accent-dark), var(--_accent-light));
}
</style>
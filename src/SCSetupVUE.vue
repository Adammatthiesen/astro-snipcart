<template>
    <div 
      hidden
      :data-config-load-css="true"
      id="snipcart"
      :data-api-key="publicApiKey"
      data-config-modal-style="side"
    ></div>
     
</template>
  
<script setup>
  import { onMounted, ref, watchEffect } from "vue";
  import { usePointer } from "@vueuse/core"; 
  const scripLoaded = ref(false);
  const pointer = usePointer();
  const count = ref(0);
  const publicApiKey = import.meta.env.PUBLIC_SNIPCART_API_KEY;
  
  const stop = watchEffect(() => {
    count.value++;
  
    if (
      (count.value > 1 && pointer.y.value) ||
      pointer.x.value ||
      pointer.isInside.value ||
      pointer.pointerType.value ||
      pointer.pressure.value ||
      pointer.tiltX.value ||
      pointer.twist.value ||
      pointer.width.value ||
      pointer.pointerId.value ||
      pointer.tiltY.value
    ) {
      LoadJS(); 
      scripLoaded.value = true;
      stop();
    }
  });
  
  function LoadJS() {
    let script = document.createElement("script");
    script.type = "text/javascript";
    script.src = "https://cdn.snipcart.com/themes/v3.7.1/default/snipcart.js";
    script.async = true;
    if (!scripLoaded.value) {
      document.head.appendChild(script);
    }
  }
  
   
  
  onMounted(() => {
    if (!window.Snipcart) {
      setTimeout(() => {
        LoadJS();
        scripLoaded.value = true;
      }, 2500);
    }
  });
</script>

<style is:global>
  @import url("https://cdn.snipcart.com/themes/v3.7.2/default/snipcart.css");
  #snipcart {
    /* ----------------- 
        Colors
    ----------------- */
    --color-default: hsl(0, 0%, 90%);
    --color-alt: hsl(0, 0%, 50%);
    --color-icon: hsl(200, 90%, 40%);
    --color-success: hsl(144, 50%, 55%);
    --color-error: hsl(6, 55%, 60%);

    --color-link: hsl(220, 70%, 55%);
    --color-link-hover: hsl(220, 70%, 65%);
    --color-link-active: var(--color-link);
    --color-link-focus: var(--color-link);

    --color-input: var(--color-default);
    --color-input-hover: var(--color-input);
    --color-input-focus: var(--color-input);
    --color-input-checked: var(--color-input);
    --color-input-disabled: var(--color-alt);
    --color-input-error: var(--color-error);
    --color-inputLabel: var(--color-default);
    --color-inputLabel-hover: var(--color-inputLabel);
    --color-inputLabel-focus: var(--color-inputLabel);
    --color-inputIcon: var(--color-alt);
    --color-inputIcon-hover: var(--color-default);
    --color-inputIcon-focus: var(--color-inputIcon);
    --color-inputIcon-checked: var(--color-default);
    --color-inputIcon-error: var(--color-error);
    --color-inputPlaceholder: var(--color-alt);

    --color-buttonPrimary: var(--color-default);
    --color-buttonPrimary-hover: hsl(0, 0%, 100%);
    --color-buttonPrimary-active: var(--color-buttonPrimary);
    --color-buttonPrimary-focus: var(--color-buttonPrimary);
    --color-buttonPrimary-disabled: var(--color-alt);
    --color-buttonPrimary-success: var(--color-buttonPrimary);
    --color-buttonPrimary-error: var(--color-buttonPrimary);

    --color-buttonSecondary: var(--color-icon);
    --color-buttonSecondary-hover: hsl(200, 90%, 50%);
    --color-buttonSecondary-active: var(--color-buttonSecondary);
    --color-buttonSecondary-focus: var(--color-buttonSecondary);
    --color-buttonSecondary-disabled: hsl(210, 10%, 25%);
    --color-buttonSecondary-success: var(--color-success);
    --color-buttonSecondary-error: var(--color-error);

    --color-buttonDanger: var(--color-error);
    --color-buttonDanger-hover: hsl(6, 55%, 70%);
    --color-buttonDanger-active: var(--color-buttonDanger);
    --color-buttonDanger-focus: var(--color-buttonDanger);
    --color-buttonDanger-disabled: hsl(210, 10%, 25%);
    --color-buttonDanger-success: var(--color-default);
    --color-buttonDanger-error: var(--color-default);

    --color-badge: var(--color-link);
    --color-badge-active: var(--color-link);
    --color-badge-disabled: var(--color-alt);

    /* ----------------- 
        Border colors
    ----------------- */
    --borderColor-default: hsla(0, 0%, 100%, 10%);
    --borderColor-error: hsl(6, 55%, 30%);

    --borderColor-link: currentColor;
    --borderColor-link-hover: currentColor;
    --borderColor-link-active: currentColor;
    --borderColor-link-focus: currentColor;

    --borderColor-input: hsla(0, 0%, 100%, 10%);
    --borderColor-input-hover: hsl(200, 90%, 40%);
    --borderColor-input-focus: var(--borderColor-input-hover);
    --borderColor-input-checked: var(--borderColor-input-hover);
    --borderColor-input-disabled: hsl(210, 10%, 20%);
    --borderColor-input-error: var(--borderColor-error);

    --borderColor-buttonPrimary: transparent;
    --borderColor-buttonPrimary-hover: transparent;
    --borderColor-buttonPrimary-focus: transparent;
    --borderColor-buttonPrimary-disabled: transparent;
    --borderColor-buttonPrimary-success: transparent;
    --borderColor-buttonPrimary-error: transparent;

    --borderColor-buttonSecondary: transparent;
    --borderColor-buttonSecondary-hover: transparent;
    --borderColor-buttonSecondary-focus: transparent;
    --borderColor-buttonSecondary-disabled: transparent;
    --borderColor-buttonSecondary-success: transparent;
    --borderColor-buttonSecondary-error: transparent;

    --borderColor-badge: transparent;
    --borderColor-badge-active: transparent;
    --borderColor-badge-disabled: transparent;

    /* ----------------- 
        Background colors
    ----------------- */
    --bgColor-default: hsl(210, 10%, 11%);
    --bgColor-alt: hsl(210, 10%, 9%);
    --bgColor-success: hsl(144, 70%, 15%);
    --bgColor-error: hsl(6, 50%, 15%);
    --bgColor-info: hsl(210, 55%, 15%);

    --bgColor-modal: hsl(210, 10%, 7%);
    --bgColor-modalVeil: hsla(210, 10%, 7%, .75);

    --bgColor-link: none;
    --bgColor-link-hover: none;
    --bgColor-link-active: none;
    --bgColor-link-focus: hsl(210, 55%, 10%);

    --bgColor-input: hsl(210, 10%, 10%);
    --bgColor-input-hover: var(--bgColor-input);
    --bgColor-input-focus: var(--bgColor-input);
    --bgColor-input-checked: var(--borderColor-input-hover);
    --bgColor-input-disabled: hsl(210, 10%, 14%);
    --bgColor-input-error: var(--bgColor-input);
    --bgColor-input-autofill: hsl(210, 60%, 15%);

    --bgColor-buttonPrimary: hsl(220, 70%, 22%);
    --bgColor-buttonPrimary-hover: hsl(220, 70%, 30%);
    --bgColor-buttonPrimary-active: var(--bgColor-buttonPrimary);
    --bgColor-buttonPrimary-focus: var(--bgColor-buttonPrimary);
    --bgColor-buttonPrimary-disabled: hsl(210, 10%, 25%);
    --bgColor-buttonPrimary-success: hsl(144, 66%, 30%);
    --bgColor-buttonPrimary-error: hsl(6, 60%, 35%);

    --bgColor-buttonSecondary: var(--bgColor-info);
    --bgColor-buttonSecondary-hover: hsl(210, 60%, 18%);
    --bgColor-buttonSecondary-active: var(--bgColor-buttonSecondary);
    --bgColor-buttonSecondary-focus: var(--bgColor-buttonSecondary);
    --bgColor-buttonSecondary-disabled: hsl(210, 10%, 9%);
    --bgColor-buttonSecondary-success: var(--bgColor-success);
    --bgColor-buttonSecondary-error: var(--bgColor-error);

    --bgColor-buttonDanger: var(--bgColor-error);
    --bgColor-buttonDanger-hover: hsl(6, 50%, 18%);
    --bgColor-buttonDanger-active: var(--bgColor-buttonDanger);
    --bgColor-buttonDanger-focus: var(--bgColor-buttonDanger);
    --bgColor-buttonDanger-disabled: hsl(210, 10%, 9%);
    --bgColor-buttonDanger-success: hsl(144, 66%, 30%);
    --bgColor-buttonDanger-error: hsl(6, 60%, 35%);

    --bgColor-badge: hsl(210, 55%, 10%);
    --bgColor-badge-active: hsl(210, 60%, 15%);
    --bgColor-badge-disabled: hsl(210, 10%, 11%);

    /* ----------------- 
        Shadows
    ----------------- */

    --shadow-default: 0px 20px 24px -20px hsla(0, 0%, 0%, .5);
    --shadow-tooltip: 0px 8px 16px hsla(220, 70%, 22%, .5);

    --shadow-link-focus: 0px 6px 4px -3px hsla(200, 90%, 40%, .5);

    --shadow-input-hover: none;
    --shadow-input-focus: 0px 5px 10px -3px hsla(200, 90%, 40%, .3);
    --shadow-input-checked: none;

    --shadow-buttonPrimary-hover: 0px 10px 4px -8px hsla(0, 0%, 0%, .5);
    --shadow-buttonPrimary-active: none;
    --shadow-buttonPrimary-focus: 0px 0px 6px 2px hsl(200, 90%, 40%);

    --shadow-buttonSecondary-hover: 0px 10px 4px -8px hsla(0, 0%, 0%, .2);
    --shadow-buttonSecondary-active: none;
    --shadow-buttonSecondary-focus: 0px 0px 6px 2px hsla(200, 90%, 40%, .8);

    --shadow-buttonDanger-hover: 0px 10px 4px -8px hsla(0, 0%, 0%, .25);
    --shadow-buttonDanger-active: none;
    --shadow-buttonDanger-focus: 0px 0px 6px 2px hsla(6, 55%, 60%);
}
</style>
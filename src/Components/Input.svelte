<script>
  import { createEventDispatcher, onMount } from "svelte";
  // Declar variables.
  export let type = "text";
  export let id = "";
  export let name = "";
  export let value = "";
  export let classe = "";
  export let min = null;
  export let max = null;
  export let step = null;
  export let autocomplete = "off";
  export let placeholder = null;
  export let disabled = null;
  const dispatch = createEventDispatcher();
  // Change value field.
  function onChangerValue(event) {
    dispatch("changeValue", {
      name: name,
      value: event.target.value
    });
  }
  // Insert default values.
  onMount(() => {
    type = type === "datetimelocal" ? "datetime-local" : type;
    value = type === "range" ? (value = min) : value;
    dispatch("changeValue", {
      name,
      value
    });
  });
</script>

<input
  {type}
  {id}
  {name}
  {value}
  class={classe}
  {placeholder}
  {disabled}
  {min}
  {max}
  {step}
  {autocomplete}
  on:input={onChangerValue} />

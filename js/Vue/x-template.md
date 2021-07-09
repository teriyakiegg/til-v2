# x-template
```
Another way to define templates is inside of a script element with the type text/x-template, then referencing the template by an id. For example:

<script type="text/x-template" id="hello-world-template">
  <p>Hello hello hello</p>
</script>
Vue.component('hello-world', {
  template: '#hello-world-template'
})
Your x-template needs to be defined outside the DOM element to which Vue is attached.

These can be useful for demos with large templates or in extremely small applications, but should otherwise be avoided, because they separate templates from the rest of the component definition.
```
https://vuejs.org/v2/guide/components-edge-cases.html#X-Templates
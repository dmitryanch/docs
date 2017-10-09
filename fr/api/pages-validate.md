---
title: "API: The validate Method"
description: Nuxt.js lets you define a validator method inside your dynamic route component.
---

# The validate Method (En)

> Nuxt.js lets you define a validator method inside your dynamic route component.

- **Type:** `Function`

```js
validate({ params, query, store }) {
  return true // if the params are valid
  return false // will stop Nuxt.js to render the route and display the error page
}
```

<p style="width: 294px;position: fixed; top : 64px; right: 4px;" class="Alert Alert--orange"><strong>⚠Cette page est actuellement en cours de traduction française. Vous pouvez repasser plus tard ou <a href="https://github.com/vuejs-fr/nuxt" target="_blank">participer à la traduction</a> de celle-ci dès maintenant !</strong></p><p>Nuxt.js lets you define a validator method inside your dynamic route component (In this example: `pages/users/_id.vue`).</p>

If the validate method does not return `true`, Nuxt.js will automatically load the 404 error page.

```js
export default {
  validate ({ params }) {
    // Must be a number
    return /^\d+$/.test(params.id)
  }
}
```

You can also check some data in your [store](/guide/vuex-store) for example (filled by [nuxtServerInit action](/guide/vuex-store#the-nuxtserverinit-action) before):

```js
export default {
  validate ({ params, store }) {
    // Check if `params.id` is an existing category
    return store.state.categories.some((category) => category.id === params.id)
  }
}
```
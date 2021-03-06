---
path: /create-typography-components
title: Create Typography Components
tag: frontend
date: 2020-05-21T18:09:47.284Z
part: Setup frontend
chapter: Building reusable components
postnumber: 24
framework: vue
---

In this post we will create a couple of typography components that we will use throughout the App for all of our Typography.

First create a folder in the components directory called `typography`. Then create a file called `HeadingOne.vue`and add the following:

```javascript
<template>
  <p class="text-4xl text-black text-bold font-display">
    <slot> </slot>
  </p>
</template>
<script>
export default {
  name: "HeadingOne",
  props: {
    text: String
  }
};
</script>


```

🛩️ We are creating a paragraph component with a slot inside it that will allow us to add additional content inside it.

🛩️ Then we've given it some styles.

Next up we are going to create similar files but we are just changing the font size. So in the same directory create a `HeadingTwo.vue` file with the following:

```javascript
<template>
  <p class="text-2xl text-black text-bold font-display">
    <slot> </slot>
  </p>
</template>
<script>
export default {
  name: "HeadingTwo",
  props: {
    text: String,
  },
};
</script>

```

Then create a `HeadingThree.vue` file with the following:

```javascript
<template>
  <p class="text-xl text-black text-bold font-display">
    <slot> </slot>
  </p>
</template>
<script>
export default {
  name: "HeadingThree",
  props: {
    text: String,
  },
};
</script>


```

Next up create a `BodyOne.vue` file and add the following:

```javascript
<template>
  <p class="text-sm font-display text-bold text-black">
    <slot> </slot>
  </p>
</template>
<script>
export default {
  name: "BodyOne"
};
</script>

```

Now we need to create an `index.js` file that we can import all these from:

```javascript
import Vue from "vue"
import HeadingOne from "./HeadingOne"
import HeadingTwo from "./HeadingTwo"
import HeadingThree from "./HeadingThree"
import BodyOne from "./BodyOne"

const Typography = {
  HeadingOne,
  HeadingTwo,
  HeadingThree,
  BodyOne,
}

Object.keys(Typography).forEach(name => {
  Vue.component(name, Typography[name])
})

export default Typography
```

So all we've done here is imported all those typography files, put them into an object and looped over each to instantate them as Vue components.

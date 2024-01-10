# Welcome to Astro Snipcart for Astro V4+

*This project is based on another project with the same name... [lloyedjatkinson/astro-snipcart](https://github.com/lloydjatkinson/astro-snipcart) that hasnt been updated to properly support Astro v4.*  This project is super simple and just gives you support for Snipcart within astro using very simple components...

The Following are the available imports availble to you for building your page... i have layed them out in a typical layout of how to import them into your Astro project for use.

```
import * as SC from '@adammatthiesen/astro-snipcart';
// Available usage; <SC.Cart>, <SC.CartItemCount />, <SC.CartTotal />, <SC.Login />, <SC.HeaderAstro />, <SC.MakeProduct>

import * as SCVue from '@adammatthiesen/astro-snipcart/vue';
// Available usage; <SCVue.CartItemCount client:? />, <SCVue.CartTotal client:? />, <SCVue.HeaderVue client:? />
```

The Following are the Standard Astro Components Available to import:
- ```SC.Cart``` creates a button for opening the cart
- ```SC.CartItemCount``` Shows the ammount of items as ( 2 )
- ```SC.CartTotal``` Shows the current cart total ( $2.00 )
- ```SC.Login``` Shows the Sign-in/Customer Dashboard if you've enabled the feature within snipcart
- ```SC.MakeProduct``` is the script used for product creation
- ```SC.HeaderAstro``` Put this in your `<head>` tag to activate snipcart on your website (**DOSE NOT WORK WITH VIEW TRANSITIONS**)

The Following are the Vue Astro Components, They are inteded to fix the ViewTransition bug with Snipcart's Interactive components(**REQUIRES `@astrojs/vue`** Replaces `SC.*` with `SCVue.*` if you use `<ViewTransitions />`):
- ```SCVue.HeaderVue``` 
- ```SCVue.CartItemCount```
- ```SCVue.CartTotal``` 

## Install Astro Snipcart

```
npm i @adammatthiesen/astro-snipcart
```

Make sure to add ```PUBLIC_SNIPCART_API_KEY``` to your environment variables

Add one of the following inside your `<head>`:

Astro **Without ViewTransitions**
```html
---
import { HeaderAstro } from '@adammatthiesen/astro-snipcart';
---
<head>
  /** Other Head Data */
  <HeaderAstro />
</head>
```

Astro **WITH ViewTransitions** *(Requires `@astrojs/vue`)*
```html
import { HeaderVUE } from '@adammatthiesen/astro-snipcart/vue';
---
<head>
  /** Other Head Data */
  <HeaderVUE transition:persist client:idle />
</head>

```

For a Full tutorial of this addon, check out the [blog post here](https://matthiesen.xyz/blog/getting-started-with-my-astro-snipcart-addon)

# Welcome to Astro Snipcart for Astro V4+

*This project is based on another project with the same name... [lloyedjatkinson/astro-snipcart](https://github.com/lloydjatkinson/astro-snipcart) that hasnt been updated to properly support Astro v4.*  This project is super simple and just gives you support for Snipcart within astro using very simple components...

The Following are the available imports availble to you for building your page... i have layed them out in a typical layout of how to import them into your Astro project for use.

```
import { SCCheckout, SCCartItemCount, SCCartTotalValue, SCCustomerDashboard,
SCMakeProduct, SCSetupScript} from '@adammatthiesen/astro-snipcart';

import { SCSetupVUE } from '@adammatthiesen/astro-snipcart/vue';
```

- ```SCCheckout``` creates a button for opening the cart
- ```SCCartItemCount``` Shows the ammount of items as ( 2 )
- ```SCCartTotalValue``` Shows the current cart total ( $2.00 )
- ```SCCustomerDashboard``` Shows the Sign-in/Customer Dashboard if you've enabled the feature within snipcart
- ```SCMakeProduct``` is the script used for product creation
- ```SCSetupScript``` Put this in your `<head>` tag to activate snipcart on your website (**DOSE NOT WORK WITH VIEW TRANSITIONS**)
- ```SCSetupVUE``` Replaces `SCSetupScript` if you use `<ViewTransitions />` (**REQUIRES `@astrojs/vue`**)

## Install Astro Snipcart

```
npm i @adammatthiesen/astro-snipcart
```

Make sure to add ```PUBLIC_SNIPCART_API_KEY``` to your environment variables

Add one of the following inside your `<head>`:

Astro **Without ViewTransitions**
```html
---
import { SCSetupScript } from '@adammatthiesen/astro-snipcart';
---
<head>
  /** Other Head Data */
  <SCSetupScript />
</head>
```

Astro **WITH ViewTransitions** *(Requires `@astrojs/vue`)*
```html
import { SCSetupVUE } from '@adammatthiesen/astro-snipcart/vue';
---
<head>
  /** Other Head Data */
  <SCSetupVUE transition:persist client:idle/>
</head>

```

For a Full tutorial of this addon, check out the [blog post here](https://matthiesen.xyz/blog/getting-started-with-my-astro-snipcart-addon)

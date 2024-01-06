# Welcome to Astro Snipcart for Astro V4+

*This project is based on another project with the same name... [lloyedjatkinson/astro-snipcart](https://github.com/lloydjatkinson/astro-snipcart) that hasnt been updated to properly support Astro v4.*  This project is super simple and just gives you support for Snipcart within astro using very simple components...

The Following are the available imports availble to you for building your page... i have layed them out in a typical layout of how to import them into your Astro project for use.

```
import { SCCheckout, SCCartItemCount, SCCartTotalValue, SCCustomerDashboard,
SCMakeProduct, SCSetupScript} from '@adammatthiesen/astro-snipcart';
```

- ```SCCheckout``` creates a button for opening the cart
- ```SCCartItemCount``` Shows the ammount of items as ( 2 )
- ```SCCartTotalValue``` Shows the current cart total ( $2.00 )
- ```SCCustomerDashboard``` Shows the Sign-in/Customer Dashboard if you've enabled the feature within snipcart
- ```SCMakeProduct``` is the script used for product creation
- ```SCSetupScript``` Put this in your `<head>` tag to activate snipcart on your website

## Install Astro Snipcart

```
npm i @adammatthiesen/astro-snipcart
```

Make sure to add ```PUBLIC_SNIPCART_API_KEY``` to your environment variables

An example of making a product:

```
<SCMakeProduct
  id="SKU-0001" 
  name="Example Name"
  url="/store/example"
  price={ 12.99 }
  description="Some Default Example Product" 
  image="/Link/To/Image">
  <button>Add to cart</button>
</SCMakeProduct>
```

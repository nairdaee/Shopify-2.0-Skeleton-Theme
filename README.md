
# Shopify 2.0 Skeleton Theme

This is a starter theme structure for devs wanting to code Shopify 2.0 themes from scratch



## Requirements

[Shopify CLI](https://shopify.dev/themes/tools/cli/getting-started#install-shopify-cli)

## Installation

#### On your local Machine
* First clone this repository and then navigate to the theme's directory on your local machine.

```bash
  git clone https://github.com/nairdaee/Shopify-2.0-Skeleton-Theme.git
  cd Shopify-2.0-Skeleton-Theme
  code .
```
* Next, [login](https://shopify.dev/themes/tools/cli/getting-started#authenticate) to your shopify store

* Now any Shopify CLI theme command that you run uses the theme in our `Shopify-2.0-Skeleton-Theme` directory.


#### Directly to your Shopify store
* Download the .zip file for this repository

* Log into your store and navigate to `/admin/themes`

* Under theme library click on `Add theme` and select `Upload zip file`
* Select the zip file you downloaded and wait for it to be added to your themes.
* You can now go ahead and customize your theme

## Usage/editorials

####  Creating sections:
* First go to the `sections` folder and create the section you want inside i.e `editorial.liquid`
* Inside the .liquid file you have just created add the following code(ensure that the sections.`editorial`.name matches your file name):
```liquid
{% schema %}
{
  "name": "t:sections.editorial.name",
  "tag": "section",
  "class": "section"
}
{% endschema %}
```
* If the section you are creating is static(no dynamic content will be added later). Then the schema is not required. Instead you'll manually extend inside the `layout/theme.liquid` file like shown below:

```html
<body>
<!-- Ensure the section is inside the body tag -->
{% section 'editorial' %}
</body>
```
* If your sections are dynamic then we need to add them to the `templates/`. For example, if you want to add the editorial page. First create a new file called `editorial.json` under the `templates/` folder and add the following:
```html
{
  "sections": {},
  "order": []
}

```

* Inside the `editorial.json`, under sections, add the following code:
```html
"editorial": {
  <!-- no comma at the end if there's only one item -->
      "type": "editorial"
    }
```

* Lastly, under `"order"` add:
```html
<!-- no comma at the end if there's only one item -->
    "editorial"
```
* You can now see your page when you do a `shopify theme serve` and go to the url `/editorial`

####  Adding your styles:
* Now you'll need to add your css. This is achieved by adding a `.css` file inside the `assets/` folder. In our case, it will be called `editorial.css`
* To import it into our `.liquid` section file. We use the following code at the very top of our .liquid file:
```
{{ 'editorial.css' | asset_url | stylesheet_tag }}
```
* For inline styles, you can use the styles tag i.e:
```css
{% style %}
/* Add your styles here */
{% endstyle %}
```

## Authors

- [Adrian Etenyi](https://www.github.com/nairdaee)


## License

[MIT](https://github.com/nairdaee/Shopify-2.0-Skeleton-Theme/blob/main/LICENSE)


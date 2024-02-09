# Copenhagen Theme by Zendesk

The Copenhagen theme is the default Zendesk Guide theme. It is designed to be responsive and accessible.
Learn more about customizing Zendesk Guide [here](https://support.zendesk.com/hc/en-us/sections/206670747).

The Copenhagen theme for Help Center consists of a [set of templates](#templates), [styles](#styles), a Javascript file used mainly for interactions and an [assets folder](#assets).

## How to use
This is the latest version of the Copenhagen theme available for Guide. It is possible to use this repository as a starting point to build your own custom theme. You can fork this repository as you see fit.
You can use your favorite IDE to develop themes and preview your changes locally in a web browser using the Zendesk Apps Tools (ZAT). For details, see [Previewing theme changes locally](https://support.zendesk.com/hc/en-us/articles/115014810447).

## Customizing your theme
Once you have forked this repository you can feel free to edit templates, CSS in `style.css` (if you would like to use SASS go to the [Using SASS section](#using-sass)), javascript and manage assets.

### Manifest file
The manifest allows you to define a group of settings for your theme that can then be changed via the UI in Theming Center.
You can read more about the manifest file [here](https://support.zendesk.com/hc/en-us/articles/115012547687).

### Settings folder
If you have a variable of type file, you need to provide a default file for that variable in the `/settings` folder. This file will be used on the settings panel by default and users can upload a different file if they like.
Ex.
If you would like to have a variable for the background image of a section, the variable in your manifest file would look something like this:

```js
{
  ...
  "settings": [{
    "label": "Images",
    "variables": [{
      "identifier": "background_image",
      "type": "file",
      "description": "Background image for X section",
      "label": "Background image",
    }]
  }]
}

```

And this would look for a file inside the settings folder named: `background_image`

### Adding assets
You can add assets to the asset folder and use them in your CSS, Javascript and templates.
You can read more about assets [here](https://support.zendesk.com/hc/en-us/articles/115012399428)


## Publishing your theme
After you have customized your theme you can download the repository as a `zip` file and import it into Theming Center.

You can follow the documentation for importing [here](https://support.zendesk.com/hc/en-us/articles/115012794168).

You can also import directly from GitHub - learn more [here](https://support.zendesk.com/hc/en-us/articles/4408832476698).

## Templates
The theme includes all the templates that are used for a Help Center that has *all* the features available.
List of templates in the theme:
* Article page
* Category page
* Community post list page
* Community post page
* Community topic list page
* Community topic page
* Contributions page
* Document head
* Error page
* Footer
* Header
* Home page
* New community post page
* New request page
* Requests page
* Search results page
* Section page
* Subscriptions page
* User profile page

You can add up to 10 optional templates for:
 * Article page
 * Category page
 * Section page

You do this by creating files under the folders `templates/article_pages`, `templates/category_pages` or `templates/section_pages`.
Learn more [here](https://support.zendesk.com/hc/en-us/articles/360001948367).

## Styles
The styles that Theming Center needs to use in the theme are in the `style.css` file in the root folder.

The styles for the theme are split using Sass partials, all the partials are under [styles/](/styles/), they are all included in the "main" file [index.scss](/styles/index.scss) and then compiled to CSS.
If you wish to use SASS you can go to the [using SASS section](#using-sass)

## Assets
These are the images that are needed for the theme.
These include:
* Loader
* Dropdown arrow

# Using SASS
In order to use SASS for development, you just need to compile it into the CSS that Zendesk Guide understands.
Note: Zendesk App Tools [theme preview](#publishing-your-theme) currently does not support live SASS compilation.

## Requirements

- Install Ruby, we use `sassc` gem to compile our `.scss` files. You can see how to install Ruby [here](https://www.ruby-lang.org/en/documentation/installation/).
- Install `sassc` gem. You can run:
```
    gem install sassc
```

Now you can compile your SASS files running:
```
./bin/compile.rb
```
Which will take all the `scss` files inside the `styles/` folder and create the `style.css` file that is consumable by Zendesk Guide.


# Quick Setup Recall (Running and testing theme locally)

NOTE: This guide is to quickly setup and run the theme locally. To know more about how to customize the theme, See all the details above.

1. Create a trial account on https://www.zendesk.com/. This will let you create a subdomin Zendesk account that you can manage.
2. Make sure to opt-in for Guide integration once your trial account setup is done.
3. Create API keys for running the server locally and previewing them on your subdomain. `<YOUR_ZENDESK_DOMAIN>/admin/apps-integrations/apis/zendesk-api/settings`.
4. Enable Help Center for your account through `<YOUR_ZENDESK_DOMAIN>/hc/admin/general_settings`
5. Install [ZAT](https://developer.zendesk.com/documentation/apps/zendesk-app-tools-zat/installing-and-using-zat/) Or [ZAT CLI](https://support.zendesk.com/hc/en-us/articles/4408822095642-Previewing-theme-changes-locally)
6. Run `npm i` to install all the node packages
7. Create a `.zat` file in your main directory. You can use `zat new` or create one manually. This file content would look like:
```
{
  "subdomain": "<YOUR_SUB_DOMAIN>",
  "username": "<USERNAME>/token",
  "password": "<TOKEN_GENERATED_IN_STEP_3>",
  "zat_latest": "3.9.2",
  "zat_update_check": "2024-02-07"
}
```
8. Compile the assets `./bin/compile.rb`
9. Run the preview `zat theme preview`
10. (Optional) to build a zip of local theme and upload on your trial instance run `zip -vr <ZIP_FILE_NAME>.zip <YOUR_THEME_DIRECTORY> -x "*/node_modules/*"` and then upload the generated zip file on `<YOUR_ZENDESK_DOMAIN>/theming/workbench`


# Contributing
Bug reports and pull requests are welcome on GitHub at https://github.com/zendesk/copenhagen_theme
Please mention @zendesk/guide-growth when creating a bug report or a pull request.

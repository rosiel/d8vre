# UPEI VRE base theme for Drupal 8
## Dependencies
- ### Development
    - NodeJs/NPM
    - Gulp
    - Bower

- ### Production
    - 'Component Libraries', https://www.drupal.org/project/components
    - 'Roblib Vre Footer', https://github.com/roblib/roblib_vre_footer
    - (If this theme is installed via Composer, it will download these)
## Details 
- using core/stable as a base theme
- put site info in config.yml
- checkout `gulpfile.babel.js`
- need to run `npm install && bower install`
- add fonts to ****.libraries.yml

## Cool stuff
- Foundation 6 is built in. Any of the components, etc from https://foundation.zurb.com/sites/docs/ will work out of the box if their markup is emulated.
- Site setup script
  - If you want to fork this theme off as a new project, `./theme-setup` will rename all the relavent bits and create an empty git repo.
- Fancy Gulp setup
  - add site details in `config.yml` 
  - can proxy local or remote site with Browsersync
  
- SVG sprites: 
  - All svg's placed in 'src/assets/img/icons/' are bundled by Gulp into a master SVG sprite
  - ```{% include '@components/utilities/icon.twig' with { icon: 'home'  } %}``` puts the svg in the Twg template
- Extended Twig templates
  - "normal" twig templates can be used in combination with Drupal twig templates.
  - example usage:
```
    ----------------------
    # (themename.info.yml)
    ----------------------
    ...
    component-libraries:
        components:
            paths:
                - components
    ...

    --------------------------------
    # (somedrupaltemplate.html.twig)
    --------------------------------
    ...
    {% include '@components/utilities/icon.twig' with { icon: 'home'  } %}
    ...

    -------------------------------------
    # (./components/utilities/icon.twig)
    -------------------------------------
    ...
    <svg class="icon icon--{{ icon }}"><use xlink:href="#icon-{{ icon }}"></use></svg>
    ...


```


# Tide Theme for FOSSBilling

[![StandWithUkraine](https://raw.githubusercontent.com/vshymanskyy/StandWithUkraine/main/badges/StandWithUkraine.svg)](https://github.com/vshymanskyy/StandWithUkraine/blob/main/docs/README.md)

[![SWUbanner](https://raw.githubusercontent.com/vshymanskyy/StandWithUkraine/main/banner2-direct.svg)](https://github.com/vshymanskyy/StandWithUkraine/blob/main/docs/README.md)

## Overview

Tide is a client area theme for FOSSBilling. It's designed to enhance your user interface with a clean, modern aesthetic. This guide provides steps on how to install, upgrade, secure, and customize the Tide theme.

<p align="center">
  <img src="screen1.png" width="48%" />
  <img src="screen2.png" width="48%" />
</p>

## Compatibility

- Tide 1.2.4 → FOSSBilling 0.8.7

We strongly recommend upgrading to the latest version of FOSSBilling.

## Installation

1. Get the Tide theme using one of the following methods:

   **a. Download from GitHub**

   - Download the ZIP archive and extract it.
   - Open the extracted directory, for example `tide-1.2.4`.
   - Rename the theme directory inside it to `tide`.

   **b. Clone with Git**

   ```bash
   git clone --branch v1.2.4 --depth 1 https://github.com/getnamingo/tide.git
   ```

   This creates a directory named `tide`.

2. Move the `tide` directory into your FOSSBilling themes directory:

   ```bash
   mv tide /var/www/themes/
   ```

   Replace `/var/www` with your FOSSBilling installation path if different.

3. Set the correct owner and permissions:

   ```bash
   chown -Rf www-data:www-data /var/www/themes/tide
   chmod -Rf 750 /var/www/themes/tide
   ```

4. In the FOSSBilling admin panel, go to `Settings -> Themes` and select `tide` as the default theme.

## Upgrade

1. Get the Tide theme using one of the following methods:

   **a. Download from GitHub**

   - Download the ZIP archive and extract it.
   - Open the extracted directory, for example `tide-1.2.4`.
   - Rename the theme directory inside it to `tide`.

   **b. Clone with Git**

   ```bash
   git clone --branch v1.2.4 --depth 1 https://github.com/getnamingo/tide.git
   ```

   This creates a directory named `tide`.

2. Back up your existing Tide configuration and custom files:

   - `/var/www/themes/tide/config/settings_data.json`
   - `/var/www/themes/tide/assets/custom`
   - `/var/www/themes/tide/html/custom`

   Replace `/var/www` with your FOSSBilling installation path if different.

3. Replace the existing Tide theme with the new version:

   ```bash
   rm -rf /var/www/themes/tide
   mv tide /var/www/themes/
   ```

4. Restore `settings_data.json` and any files from `assets/custom` and `html/custom` from your backup.

5. Set the correct owner and permissions:

   ```bash
   chown -Rf www-data:www-data /var/www/themes/tide
   chmod -Rf 750 /var/www/themes/tide
   ```

### Upgrade from v1.1.3

If you customized your CSS in v1.1.3 or earlier, move `FOSSBilling directory/themes/tide/assets/css/extra.css` to `FOSSBilling directory/themes/tide/assets/custom/extra.css` before upgrading and follow Section 2 of the Theme Customization section below.

### Security Measures for Prior Installations (Before 0.9.5)

For versions of Tide installed prior to 0.9.5, implement these security measures:

1. Change the directory owner to the web server user. For example: `chown -Rf www-data:www-data tide/`.
2. Set permissions to `750` using chmod: `chmod -Rf 750 tide/`.

## Theme Customization

Tide is designed to be safely customizable without modifying core template files.  
To prevent your changes from being overwritten during updates, use the supported customization methods below.

### 1. Dashboard Layout

Tide provides optional hook points that allow you to extend specific dashboard areas without editing core files.

To use them, create the following files inside `FOSSBilling directory/themes/tide/html/custom/`:

`dashboard.top.twig` – customizes the top area of the dashboard  
`dashboard.widgets.twig` – customizes the widgets section  
`dashboard.bottom.twig` – customizes the bottom area of the dashboard  

Each file corresponds to its respective dashboard area.  
It is safe if one or more of these files are missing — Tide will continue to function normally.

For consistent layout and spacing, follow the default Tide dashboard structure:

- For `dashboard.top.twig` and `dashboard.bottom.twig`, wrap your content inside a Bootstrap `row row-cards` container and place elements inside `card` components.
- For `dashboard.widgets.twig`, use a standard `row`, as it is already rendered within the dashboard widgets grid context.

This ensures visual consistency with the default Tide dashboard styling.

### 2. Theme Colours

Tide allows you to replace the default colours with custom ones, so you can align the theme with your branding.

1. Create the following file to load your custom CSS automatically:

`FOSSBilling directory/themes/tide/html/custom/head.extra.twig`

Paste this content inside:

```twig
<link href="{{ 'custom/extra.css' | asset_url }}" rel="stylesheet"/>
```

2. Create `FOSSBilling directory/themes/tide/assets/custom/extra.css` and place your custom CSS overrides inside it, following the example below.

```css
.bg-primary {
     background-color: #your-color !important;
}
.text-primary {
     color: #your-color !important;
}
.btn-primary {
     background-color: #your-color !important;
     border-color: #your-color !important;
}
.btn-primary:hover {
     background-color: #your-hover-color !important;
     border-color: #your-hover-color !important;
}
.btn-primary:focus {
     background-color: #your-focus-color !important;
     border-color: #your-focus-color !important;
     box-shadow: 0 0 0 0.2rem rgba(#your-color, 0.5) !important;
}
.btn-primary:active {
     background-color: #your-active-color !important;
     border-color: #your-active-color !important;
}
.btn-primary:disabled {
     background-color: #your-disabled-color !important;
     border-color: #your-disabled-color !important;
}
```

Because this file is placed under `assets/custom/`, it is not part of the standard Tide files and will not be rewritten during a normal update.

Backups are still encouraged as a best practice. However, you should not need to restore this file after upgrading unless your update process deletes the entire theme folder.

## Support

Your feedback and inquiries are invaluable to Namingo's evolutionary journey. If you need support, have questions, or want to contribute your thoughts:

- **Email**: Feel free to reach out directly at [help@namingo.org](mailto:help@namingo.org).

- **Discord**: Or chat with us on our [Discord](https://discord.gg/97R9VCrWgc) channel.
  
- **GitHub Issues**: For bug reports or feature requests, please use the [Issues](https://github.com/getpinga/tide/issues) section of our GitHub repository.

We appreciate your involvement and patience as Namingo continues to grow and adapt.

## Support This Project

If you find Tide useful, consider donating:

- [Donate via Stripe](https://donate.stripe.com/7sI2aI4jV3Offn28ww)
- BTC: `bc1q9jhxjlnzv0x4wzxfp8xzc6w289ewggtds54uqa`
- ETH: `0x330c1b148368EE4B8756B176f1766d52132f0Ea8`

## Licensing

Tide is licensed under the Apache License, Version 2.0 starting from version 1.1.

Versions 1.0 and earlier are licensed under the MIT License.

This project includes and builds upon code from Huraga, the default template of the FOSSBilling platform.
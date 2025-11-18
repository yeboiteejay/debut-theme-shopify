# Shopify Collection Template with Color Variants

A Shopify collection template that displays each color variant as an individual product card, providing direct navigation to specific color variants.

## Overview

This custom template modifies the standard Shopify collection page to display color variants as separate products. Instead of showing one product card with multiple color options, each color receives its own card with direct variant linking.

## Features

- Display each color variant as a separate product card
- Direct linking to specific variants via `?variant=ID`
- Supports Color option in any position (Option1, Option2, or Option3)
- Fallback handling for products without color options
- Sold out and sale badges
- Lazy loading for optimized performance
- Fully responsive design
- Maintains standard collection features (sorting, pagination, filtering)

## File Structure

```
templates/collection.with-variants.liquid   # Main collection template
snippets/product-price.liquid               # Price display component
snippets/pagination.liquid                  # Pagination component
assets/collection-with-variants.css         # Template styles
products_export_ctrecruiting.csv            # Sample product data
```

## Installation

### 1. Import Sample Products (Optional)

Navigate to Products > Import and upload `products_export_ctrecruiting.csv`. Verify that Option1 is set to Size and Option2 is set to Color.

### 2. Add Collection Template

1. Navigate to Online Store > Themes > Edit code
2. Create a new template: Templates > Add a new template > collection
3. Name the template `with-variants`
4. Copy the contents from `templates/collection.with-variants.liquid` into the new template

### 3. Add Stylesheet

1. Navigate to Assets > Add a new asset > Create blank file
2. Name the file `collection-with-variants.css`
3. Copy the contents from `assets/collection-with-variants.css` into the new file

### 4. Add Snippets

**Note:** The Debut theme includes these snippets by default. Only add them if they are missing from the theme.

1. For `product-price.liquid`: Snippets > Add new snippet > `product-price`
2. For `pagination.liquid`: Snippets > Add new snippet > `pagination`
3. Copy the respective file contents into each snippet

### 5. Apply Template to Collection

1. Navigate to Products > Collections
2. Select or create a collection
3. In the Template dropdown, select `collection.with-variants`
4. Save changes

## How It Works

The template iterates through collection products and identifies the Color option (regardless of position). For each product with color variants:

- Groups variants by color value
- Creates individual product cards for each unique color
- Displays the variant-specific image (falls back to product image if unavailable)
- Links directly to the variant using query parameter (`?variant=ID`)
- Shows the first available variant for each color (or first variant if all sold out)

Products without color options display normally as single cards.

## Theme Settings

The template includes customizable settings accessible through the theme editor:

- **Show collection image**: Toggle hero banner display
- **Show product vendors**: Toggle vendor name display
- **Products per page**: Range from 8 to 50 (default: 24)

## Technical Details

- **Compatibility**: Designed for Shopify Debut theme
- **Browser Support**: Chrome, Firefox, Safari, Edge
- **Responsive**: Mobile-first design with breakpoints at 750px
- **Performance**: Implements lazy loading via lazyload class
- **Accessibility**: Includes ARIA labels and visually-hidden text for screen readers

## Template Logic

The template handles three scenarios:

1. **Color in Option1**: Accesses via `variant.option1`
2. **Color in Option2**: Accesses via `variant.option2`
3. **Color in Option3**: Accesses via `variant.option3`
4. **No Color option**: Displays product as standard card

## Customization

The template supports both "Color" and "Colour" option names. To add additional option name variations, modify the condition in `templates/collection.with-variants.liquid`:

```liquid
{% if option == 'Color' or option == 'Colour' %}
```

## License

MIT License - free to use and modify.

## Contributing

Contributions, issues, and feature requests are welcome. Feel free to check the issues page for open issues or create a new one.

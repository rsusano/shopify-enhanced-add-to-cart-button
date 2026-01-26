# 📦 Installation Guide

Complete step-by-step guide to installing the Enhanced Add-to-Cart Button.

---

## Prerequisites

- Shopify store access
- Theme Editor permissions
- Basic understanding of Shopify (helpful but not required)

---

## Method 1: Theme Customizer (Recommended)

### Step 1: Upload Files

1. **Go to:** Online Store > Themes > Edit code

2. **Upload Block File:**
   - Navigate to `blocks/` folder
   - Click "Add a new section"
   - Create `add-to-cart.liquid`
   - Copy code from `blocks/add-to-cart.liquid`
   - Save

3. **Upload Snippet File:**
   - Navigate to `snippets/` folder
   - Click "Add a new snippet"
   - Name it `add-to-cart-button-enhanced`
   - Copy code from `snippets/add-to-cart-button-enhanced.liquid`
   - Save

4. **Upload JavaScript:**
   - Navigate to `assets/` folder
   - Click "Add a new asset" → Create a blank file
   - Name it `enhanced-add-to-cart.js`
   - Copy code from `assets/enhanced-add-to-cart.js`
   - Save

### Step 2: Add to Product Page

1. **Open Theme Customizer:**
   - Go to Online Store > Themes > Customize
   
2. **Navigate to Product Page:**
   - Top dropdown → Products → Default product

3. **Remove Old Button:**
   - Find existing "Add to Cart" block
   - Click → Remove block

4. **Add Enhanced Button:**
   - Click "Add block"
   - Select "Add to Cart" (your new enhanced version)
   - Position where you want it

5. **Customize:**
   - Click the block to see settings
   - Adjust colors, text, sizing
   - Save

### Step 3: Test

- Select different variants
- Check price updates
- Test on mobile
- Verify add-to-cart works

---

## Method 2: Manual Code Integration

For developers who want more control.

### Step 1: Add Files (Same as Method 1)

### Step 2: Add to Product Template

Find your product template (`sections/product-template.liquid` or similar):

```liquid
{%- comment -%} Replace your existing add-to-cart button with: {%- endcomment -%}

<div
  class="enhanced-add-to-cart-wrapper"
  style="
    --atc-bg-color: #2F7A5E;
    --atc-text-color: #FFFFFF;
    --atc-hover-bg: #235A46;
    --atc-border-radius: 8px;
    --atc-font-size: 16px;
    --atc-padding-v: 16px;
    --atc-padding-h: 32px;
    --atc-price-color: #FFFFFF;
    --atc-compare-price-color: #CCCCCC;
    --atc-guarantee-color: #FFFFFF;
  "
>
  {% render 'add-to-cart-button-enhanced',
    id: 'product-submit-button',
    class: 'button enhanced-add-to-cart',
    can_add_to_cart: true,
    product: product,
    add_to_cart_text: 'Add to cart',
    show_price: true,
    show_compare_price: true,
    show_guarantee: true,
    guarantee_text: '30 Day Money-Back Guarantee',
    separator: '-',
    display_price: product.selected_or_first_available_variant.price,
    display_compare_price: product.selected_or_first_available_variant.compare_at_price
  %}
</div>
```

---

## Configuration

### Basic Setup

**Minimal configuration:**
```liquid
{% render 'add-to-cart-button-enhanced',
  product: product
%}
```

**Full configuration:**
```liquid
{% render 'add-to-cart-button-enhanced',
  id: 'custom-button-id',
  class: 'button enhanced-add-to-cart',
  can_add_to_cart: true,
  product: product,
  add_to_cart_text: 'Buy Now',
  show_price: true,
  show_compare_price: true,
  show_guarantee: true,
  guarantee_text: 'Free Shipping Over $50',
  separator: '|',
  display_price: variant.price,
  display_compare_price: variant.compare_at_price
%}
```

---

## Styling

### Using Theme Customizer

All styling options available in:
- Online Store > Themes > Customize
- Product page → Enhanced Button block
- Settings panel on right side

### Using CSS (Advanced)

Override in your theme CSS:

```css
/* Custom button styling */
.enhanced-add-to-cart {
  --atc-bg-color: #FF6B9D !important;
  --atc-font-size: 18px !important;
  box-shadow: 0 4px 12px rgba(0,0,0,0.15);
}

/* Custom hover effect */
.enhanced-add-to-cart:hover {
  transform: scale(1.05);
}
```

---

## Verification Checklist

After installation:

- [ ] Button appears on product page
- [ ] Price displays correctly
- [ ] Compare-at price shows (if product has one)
- [ ] Guarantee text visible
- [ ] Colors match your brand
- [ ] Clicking adds product to cart
- [ ] Success animation plays
- [ ] Mobile view looks good
- [ ] Works with variant selector

---

## Troubleshooting

### Button Doesn't Appear

**Check:**
1. Files uploaded to correct folders
2. File names match exactly (case-sensitive)
3. Block added in theme customizer
4. No JavaScript errors in console (F12)

### Price Not Showing

**Check:**
1. `show_price: true` in settings
2. Product has a price set
3. Variant is available

### Styling Not Applied

**Check:**
1. Theme CSS not overriding (increase specificity)
2. CSS variables supported by browser
3. Clear browser cache

---

## Next Steps

After successful installation:

1. ✅ Read [CUSTOMIZATION.md](./CUSTOMIZATION.md) for styling examples
2. ✅ Test on different products
3. ✅ Test on mobile devices
4. ✅ Add screenshots to your store (optional)

---

**Installation Complete!** 🎉

Your enhanced button is now ready to increase conversions.

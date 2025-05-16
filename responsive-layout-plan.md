# Responsive Layout Enhancement Plan for RSI Website

## Current Implementation
The website currently uses:
- Bootstrap framework for responsive grid
- Custom media queries at breakpoints: 575px, 767px, 991px, and 1024px
- Some responsive classes and flexbox layouts
- Responsive navigation with mobile menu

## Responsive Improvements by Section

### 1. Navigation Bar

**Issues:**
- Navigation breaks on mobile devices
- Button positioning inconsistent across breakpoints
- Menu toggle needs refinement

**Solutions:**
```css
/* Improve mobile navigation */
@media (max-width: 767px) {
  .nav-bar {
    padding: 0 10px;
    height: 56px;
  }
  
  .navbar-toggler {
    padding: 6px;
  }
  
  .ref-logo {
    width: 120px;
  }
}

/* Fix button display on mobile */
@media (max-width: 575px) {
  .btn-primary {
    display: block;
    width: 100%;
    margin: 10px 0;
  }
}
```

### 2. Hero Section

**Issues:**
- Content stacking issues on mobile
- Image and text alignment problems
- Decorative elements (squares) positioning inconsistent

**Solutions:**
```css
@media (max-width: 767px) {
  .hero-container {
    flex-direction: column;
    height: auto;
    padding: 40px 0;
  }
  
  .paddler-img {
    height: 300px;
    margin-top: 40px;
    width: 100%;
  }
  
  .hero-row {
    flex-direction: column;
    text-align: center;
  }
  
  /* Improve button layout */
  .hero-row .btn {
    margin: 0 5px 10px 5px;
    min-width: 140px;
  }
  
  /* Better square positioning */
  .squares-container {
    width: 100%;
    height: 200px;
    position: relative;
  }
}
```

### 3. Business Units Section

**Issues:**
- Cards don't stack properly on mobile
- Inconsistent spacing and margins
- Image sizing issues

**Solutions:**
```css
/* Improve card layout */
@media (max-width: 991px) {
  .feature-unit {
    flex-direction: column-reverse;
  }
  
  .feature-image {
    width: 100%;
    height: 300px;
    border-radius: 4px;
  }
  
  .content-colum {
    padding: 24px;
    text-align: center;
  }
  
  .card-flex {
    gap: 24px;
  }
}

@media (max-width: 575px) {
  .card-flex {
    flex-direction: column;
  }
  
  .card-body {
    width: 100%;
    margin-bottom: 24px;
  }
  
  .cma-card-img, .eres-card-img, .cow-card-img {
    height: 150px;
  }
}
```

### 4. Typography System

**Issues:**
- Inconsistent font scaling
- Line heights not optimized for smaller screens

**Solutions:**
```css
:root {
  /* Base typography variables */
  --h1-desktop: 64px;
  --h1-tablet: 48px;
  --h1-mobile: 36px;
  
  --h2-desktop: 56px;
  --h2-tablet: 42px;
  --h2-mobile: 32px;
  
  --body-large-desktop: 20px;
  --body-large-tablet: 18px;
  --body-large-mobile: 16px;
}

.h1-ref {
  font-size: var(--h1-desktop);
  line-height: 1.1;
}

.h2-ref {
  font-size: var(--h2-desktop);
  line-height: 1.15;
}

.body-large {
  font-size: var(--body-large-desktop);
  line-height: 1.5;
}

@media (max-width: 991px) {
  .h1-ref {
    font-size: var(--h1-tablet);
  }
  
  .h2-ref {
    font-size: var(--h2-tablet);
  }
  
  .body-large {
    font-size: var(--body-large-tablet);
  }
}

@media (max-width: 575px) {
  .h1-ref {
    font-size: var(--h1-mobile);
  }
  
  .h2-ref {
    font-size: var(--h2-mobile);
  }
  
  .body-large {
    font-size: var(--body-large-mobile);
  }
}
```

### 5. Footer Improvements

**Issues:**
- Layout breaks on mobile
- Inconsistent alignment
- Spacing issues

**Solutions:**
```css
@media (max-width: 767px) {
  .footer-flex {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }
  
  .footer-logo {
    margin-bottom: 24px;
    width: auto;
  }
  
  .footer-link {
    margin-bottom: 12px;
    display: block;
    text-align: center;
  }
}

@media (max-width: 575px) {
  .footer-style {
    margin: 0;
    padding: 20px;
  }
}
```

### 6. Consistent Spacing System

**Implementation:**
```css
:root {
  --space-xs: 8px;
  --space-sm: 16px;
  --space-md: 24px;
  --space-lg: 40px;
  --space-xl: 64px;
  --space-xxl: 100px;
}

/* Desktop spacing */
.section-padding {
  padding: var(--space-xxl) 0;
}

/* Tablet spacing */
@media (max-width: 991px) {
  .section-padding {
    padding: var(--space-xl) 0;
  }
  
  :root {
    --space-lg: 32px;
    --space-xl: 48px;
    --space-xxl: 64px;
  }
}

/* Mobile spacing */
@media (max-width: 575px) {
  .section-padding {
    padding: var(--space-lg) 0;
  }
  
  :root {
    --space-lg: 24px;
    --space-xl: 40px;
    --space-xxl: 48px;
  }
}
```

### 7. Mobile Touch Targets

**Implementation:**
```css
@media (max-width: 767px) {
  /* Better touch targets */
  .nav-link, .btn, .footer-link {
    padding: 12px;
    min-height: 44px;
  }
  
  /* Larger clickable area for buttons */
  .btn {
    min-width: 100px;
  }
}
```

### 8. Image Optimization

**Implementation Example:**
```html
<picture>
  <source 
    type="image/webp" 
    srcset="img/referentia-logo-blue.webp"
    sizes="(max-width: 575px) 120px, (max-width: 991px) 140px, 186px">
  <img 
    src="img/referentia-logo-blue.png" 
    class="img-fluid ref-logo" 
    alt="referentia logo blue"
    sizes="(max-width: 575px) 120px, (max-width: 991px) 140px, 186px"
    width="186" 
    height="44">
</picture>
```

## Implementation Plan

1. Start by creating a mobile-first approach for all new CSS
2. Update the existing media queries to be more consistent
3. Fix navigation and hero section first, as they have the most impact
4. Update the typography system
5. Apply spacing system to create consistency
6. Optimize images and touch targets
7. Test thoroughly on multiple devices

## Testing Guidelines

- Test on actual devices, not just browser emulation
- Verify usability on touch screens
- Ensure all elements are tappable on mobile (min 44x44px)
- Check for text readability at all sizes
- Validate proper image loading and sizing
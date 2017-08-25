# Animated hamburger icon mixin (Sass/Stylus/LESS)

Hamburger menu mixins utilizing the checkbox hack so you can use CSS only to show a mobile menu (or off-canvas menu, etc).

Unlike other mixins here you can specify a selector for the label tag if it's not directly below the checkbox, so the label (the icon) can be placed anywhere in the DOM.

It is also possible to add text, either on the left or right side.

There is also a "hamburger_tint" helper mixin included to easily colorize the icon/text on hover or in a checked state.


## Demo

[Sass](https://codepen.io/rolandtoth/pen/LypvrV?editors=1100) [Stylus](https://codepen.io/rolandtoth/pen/rzYPKK?editors=1100) [LESS](https://codepen.io/rolandtoth/pen/qXpoMd?editors=1100)


## Usage

### Markup

No text:

```html
<input type="checkbox" id="menu-toggle" />
<label for="menu-toggle"><i></i></label>
```

With text:

```html
<input type="checkbox" id="menu-toggle" />
<label for="menu-toggle"><i></i><span>Menu</span></label>
```

### Calling the mixin

#### Sass

```sass
// defaults
#menu-toggle {
  @include hamburger();
}

// some parameters + tint on hover
#menu-toggle {
  @include hamburger($width: 24px, $thickness: 2px, $gap: 5px, $color: lightgray, $padding: 24px);
  &:hover {
    @include hamburger_tint(orange);
  }
}
```

#### Stylus

```stylus
// defaults
#menu-toggle
  hamburger()

// some parameters + tint on hover
#menu-toggle
  hamburger(width: 24px, thickness: 2px, gap: 5px, color: lightgray, padding: 24px)
  &:hover
    hamburger_tint(orange)
```

#### LESS

```less
// defaults
#menu-toggle {
  .hamburger();
  }
}

// some parameters + tint on hover
  .hamburger(@width: 24px, @thickness: 2px, @gap: 5px, @color: lightgray, @padding: 24px);
  &:hover {
    .hamburger_tint(orange);
  }
}
```


 ## Parameters:

- **width**: the width of the icon. `default: 32px`
- **thickness**: the thickness of the bars. `default: 3px`
- **gap**: the vertical space between the bars. Overall height is: thickness x 3 + gap x 2. `default: 7px`
- **color**: the color of the icons. `default: #000 (black)`
- **radius**: border-radius value to round edges. `default: 0`
- **anim**: seconds of animation duration (transition-duration) or timing function + duration (eg. "ease-out 0.3s"). `default:0.25s`
- **labelselector**: in case the label is not directly after the checkbox, use this setting to tell the mixin where to find it. Eg. "~ div.content header nav label". `default: "+ label"`
- **padding**: extra spacing around the icon. `default: 0`
- **text**: show text next to the icon, by default on the right. Values: "left" or false to disable .Requires an extra "span" tag. `default: "right"`

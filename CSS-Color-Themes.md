## Light/dark theme color change (Alpha version)

Internet Explorer 11 browser is no longer supported. Features that are described in this section are not going to affect the interface when using this particular web browser.

Important: this functionality is currently being developed. Any variable and selector names can be changed or removed in future versions completely.

*Starting from version 1.16*.

You can change the colors of light/dark theme for certain UI elements by connecting your [CSS files](Widget-Constructor#custom_css_url). For your convenience, some elements have CSS Custom Properties that can be overridden.

The following CSS will make the widget look pink when selecting the light/dark theme.

```css
:root:not(.theme-dark) {
    --tv-color-platform-background: #d1c4e9;
    --tv-color-pane-background: rgb(251, 223, 244);
    --tv-color-pane-background-secondary: rgb(249, 185, 233);
    --tv-color-toolbar-button-background-hover: rgb(244, 143, 177);
    --tv-color-toolbar-button-background-secondary-hover: red;
    --tv-color-toolbar-button-background-expanded: rgb(244, 143, 177);
    --tv-color-toolbar-button-text: rgb(136, 24, 79);
    --tv-color-toolbar-button-text-hover: rgb(74, 20, 140);
    --tv-color-toolbar-button-text-active: red;
    --tv-color-toolbar-button-text-active-hover: red;
    --tv-color-item-active-text: rgb(6, 6, 255);
    --tv-color-toolbar-toggle-button-background-active: red;
    --tv-color-toolbar-toggle-button-background-active-hover: magenta;
}

.theme-dark:root {
    --tv-color-platform-background: #d1c4e9;
    --tv-color-pane-background: rgb(251, 223, 244);
    --tv-color-pane-background-secondary: rgb(249, 185, 233);
    --tv-color-toolbar-button-background-hover: rgb(244, 143, 177);
    --tv-color-toolbar-button-background-secondary-hover: red;
    --tv-color-toolbar-button-background-expanded: rgb(244, 143, 177);
    --tv-color-toolbar-button-text: rgb(136, 24, 79);
    --tv-color-toolbar-button-text-hover: rgb(74, 20, 140);
    --tv-color-toolbar-button-text-active: red;
    --tv-color-toolbar-button-text-active-hover: red;
    --tv-color-item-active-text: rgb(6, 255, 6);
    --tv-color-toolbar-toggle-button-background-active: red;
    --tv-color-toolbar-toggle-button-background-active-hover: magenta;
}
```

- the `: root: not (.theme-dark)` selector defines rules for the light theme
- the `.theme-dark: root` selector defines rules for the dark theme

Available variables:

- `--tv-color-platform-background` - the main color of the page where all elements are placed on
- `--tv-color-pane-background` - toolbar background color
- `--tv-color-pane-background-secondary` - additional background color for toolbars (e.g. when there is an open toolbar on the right)
- `--tv-color-toolbar-button-background-hover` - hover effect color for a toolbar button
- `--tv-color-toolbar-button-background-secondary-hover` - additional hover color for toolbar buttons (e.g. when there is an open toolbar on the right)
- `--tv-color-toolbar-button-background-expanded` - hover effect color for the active button on the right toolbar
- `--tv-color-toolbar-button-text` - text and icon color for toolbar buttons
- `--tv-color-toolbar-button-text-hover` - text and icon color for toolbar buttons when hovering over them
- `--tv-color-toolbar-button-text-active` - text and icon color for toolbar buttons that are active
- `--tv-color-toolbar-button-text-active-hover` - text and icon color for toolbar buttons that are active when hovering over them
- `--tv-color-item-active-text` - text color for toggle toolbar buttons (e.g. Magnet Mode, Lock All Drawings)
- `--tv-color-toolbar-toggle-button-background-active` - fill color for toggle toolbar buttons (e.g. Magnet Mode, Lock All Drawings)
- `--tv-color-toolbar-toggle-button-background-active-hover` - fill color for toggle toolbar buttons when hovering over them (e.g. Magnet Mode, Lock All Drawings)

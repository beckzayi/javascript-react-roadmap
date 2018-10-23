## Above the fold loading

See the example below. Simply put, css file loaded after the window is loaded.

```javascript
<script type="text/javascript">
    const loadStyleSheet = src => {
        if (document.createStylesheet) {
            document.createStylesheet(src);
        } else {
            const stylesheet = document.createElement('link');
            stylesheet.href = src;
            stylesheet.type = 'text/css';
            document.getElementByTagName('head')[0].appendChild(stylesheet);
        }
    };

    window.onload = function() {
        loadStyleSheet('./style-extra.css');
    };
</script>
```

#### Avoid long running JavaScript

```javascript
// After dom is loaded
addEventListener('DOMContentLoaded', function() { 
    . . .
})
```

```javascript
// After the whole page is loaded (inc images and other files)
addEventListener('load', function() { 
    . . .
})
```

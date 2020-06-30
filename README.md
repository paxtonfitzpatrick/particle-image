# particle-image
#### _particlized image animation in vanilla JavaScript_

## Demos:
CodePen: https://codepen.io/paxtonfitzpatrick/pen/GRoMQgb

My personal website: https://paxtonfitzpatrick.github.io/


## Usage
1. Create an HTML element where you want your particle animation to appear, and supply it with two attributes:
   * `id`: a unique ID the script will use to identify the div. The default is `particle-image`, but you can change
    this by editing the last line of `particle-image.js`.
   * `data-params-src`: the location of your `params.json` file. This can be either a local path or an external URL.
    ```
    <div id="particle-image" data-params-src="assets/js/params.json"></div>
    ```
2. Reference the script under your `<head>` tag _with the `defer` attribute_. **Notes**: 
    * Because `particle-image.js` queries the DOM, it should not be loaded with `async`, or your 
      `#particle-image` element may not exist at runtime.
    * Currently, the size difference the minified and non-minified scripts is de minimis (16KB vs 11KB).
    ```
    <script type="text/javascript" src="assets/js/particle-image.min.js" defer></script>
    ```

3. Add the following CSS. **Notes**:
    * _make sure to update the selector if you changed the reference element's `id`_
    * If the reference element is a child of another element, you may need to add `position: relative;` to the
     parent's CSS.
    ```
    #particle-image {
      background-color: #000;  // controls the background color of the display
      position: absolute;
      top: 0;
      bottom: 0;
      left: 0;
      right: 0;
      height: 100%;
      width: 100%;
    }
    ```

3. Adjust the parameters in `params.json` as you see fit. See the **`options`** table below for reference (and play
 with the parameters on [CodePen](https://codepen.io/paxtonfitzpatrick/pen/GRoMQgb)!)
# particle-image

***particlized image animation in vanilla JavaScript***

## Demos

CodePen: **<https://codepen.io/paxtonfitzpatrick/pen/GRoMQgb>**

My personal website: **[paxtonfitzpatrick.me](https://paxtonfitzpatrick.me)**

## Usage

1. Create an HTML element where you want your particle animation to appear, and supply it with two attributes:
   * `id`: a unique ID the script will use to identify the div. The default is `particle-image`, but you can change
    this by editing the last line of `particle-image.js`.
   * `data-params-src`: the location of your `params.json` file. This can be either a local path or an external URL.

    ```html
    <div id="particle-image" data-params-src="assets/js/params.json"></div>
    ```

2. Reference the script under your `<head>` tag *with the `defer` attribute*.

   **Notes**:
    * Because `particle-image.js` queries the DOM, it should not be loaded with `async`, or your
      `#particle-image` element may not exist at runtime.
    * Currently, the size difference the minified and non-minified scripts is de minimis (16KB vs 11KB).

    ```html
    <script type="text/javascript" src="assets/js/particle-image.min.js" defer></script>
    ```

3. Add the following CSS.
   **Notes**:
    * *make sure to update the selector if you changed the reference element's `id`*
    * If the reference element is a child of another element, you may need to add `position: relative;` to the
     parent's CSS.

    ```scss
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

4. Adjust the parameters in `params.json` as you see fit. See the **options** table below for reference (and play
 with the parameters on [CodePen](https://codepen.io/paxtonfitzpatrick/pen/GRoMQgb)!)

## Options

| Field                                      | Value type                                   | Description                                                                                                                         |
|--------------------------------------------|----------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| `particles.density`                        | `number`                                     | density of the particles comprising the image                                                                                       |
| `particles.color`                          | `HEX (string)`                               | color of the particles comprising the image                                                                                         |
| `particles.size.value`                     | `number`                                     | size of each particle (expressed as its radius)                                                                                     |
| `particles.size.random`                    | `boolean`                                    | if `true`, particles are randomly drawn with radii between 50% and 100% of `particles.size.value`                                   |
| `particles.movement.speed`                 | `number`                                     | movement speed of the particles. Particles are randomly assigned initial x- and y-velocities between -0.5 and 0.5 times this value. |
| `particles.movement.restless.enabled`      | `boolean`                                    | if `true`, particles will randomly "jitter" when undisturbed after reaching their destination                                       |
| `particles.movement.restless.value`        | `number`                                     | maximum distance (in pixels) restless particles will move from their assigned location                                              |
| `particles.interactivity.on_hover.enabled` | `boolean`                                    | if `true`, particles will respond to mouse hovering with the given `action`                                                         |
| `particles.interactivity.on_hover.action`  | `string: {"repulse", "big_repulse", "grab"}` | the particles' reaction in response to mouse hovering                                                                               |
| `particles.interactivity.on_click.enabled` | `boolean`                                    | if `true`, particles will respond to mouse presses with the given `action`                                                          |
| `particles.interactivity.on_click.action`  | `string: {"repulse", "big_repulse", "grab"}` | the particles' reaction in response to mouse presses                                                                                |
| `particles.interactivity.on_touch.enabled` | `boolean`                                    | if `true`, particles will respond to screen touches (on mobile) with the given `action`                                             |
| `particles.interactivity.on_touch.action`  | `string: {"repulse", "big_repulse", "grab"}` | the particles' reaction in response to screen touches                                                                               |
| `image.src.path`                           | `string`                                     | path or URL to the image to be "particlized" (may be local or external)                                                             |
| `image.src.is_external`                    | `boolean`                                    | set to `true` when loading an external image to set the image object's `crossorigin` attribute to "anonymous"                       |
| `image.size.canvas_pct`                    | `number`                                     | percentage of the smallest canvas dimension (height or width) that the image will fill                                              |
| `image.size.max_px`                        | `number`                                     | maximum size of the image (overrides `canvas_pct` for very large canvases), in pixels                                               |
| `image.size.min_px`                        | `number`                                     | minimum size of the image (overrides `canvas_pct` for very small canvases), in pixels                                               |
| `interactions.repulse.distance`            | `number`                                     | maximum distance for the repulsion interaction                                                                                      |
| `interactions.repulse.strength`            | `number`                                     | "force" of the repulsion interaction                                                                                                |
| `interactions.big_repulse.distance`        | `number`                                     | maximum distance for the "big repulsion"  interaction                                                                               |
| `interactions.big_repulse.strength`        | `number`                                     | "force" of the "big repulsion" interaction                                                                                          |
| `interactions.grab.distance`               | `number`                                     | maximum distance for the "grab" interaction                                                                                         |
| `interactions.grab.line_width`             | `number`                                     | with of lines formed by the "grab" interaction. Constrained to be at most the particle's diameter                                   |
| `disabled`                                 | `boolean`                                    | if `true`, don't create the particle animation. Useful when debugging locally                                                       |

## Credits

This work was heavily inspired by
[Vincent Garreau](https://github.com/VincentGarreau)'s [`particles.js`](https://github.com/VincentGarreau/particles.js) and
[Louis Hoebregt](https://github.com/Mamboleoo)'s [Text to particles](https://codepen.io/Mamboleoo/pen/obWGYr)

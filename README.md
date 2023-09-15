
This package is a forked version of https://github.com/altert/OpenseadragonFabricjsOverlay

Please visit the original repository for details.

## Differences in forked version

This forked version does a few things differently.

- Syncs Fabric JS object zoom levels to OpenSeadragon's image zoom level, instead of the viewport zoom level. Basically this better supports browser resizing, both horizontally and vertically.
- This package provides JS module exports for `initFabricJSOverlay` and `fabric`, so you can `@import` into your compiled JS app.

New features:

- Added LineArrow object (draw arrow marker)
- Added `containerClass` and `zIndex` options for fabricJsOverlay
 
## Usage

```
npm install github:skuracj/openseadragon-fabricjs-overlay#dev
```

For example if you're syncing OpenSeadragon and FabricJS in Angular app for example, you could do something like this:

```

import OpenSeadragon from 'openseadragon';
import { fabric, initFabricJSOverlay } from 'openseadragon-fabricjs-overlay';

...

export default function MyFabricViewer() {
      
    // Add Fabric support to OSD
    initFabricJSOverlay(OpenSeadragon, fabric);

    // Initialize our OpenSeadragon instance
    const viewer = OpenSeadragon(options);
    
      const options = {
      scale: 1000,
      containerClass: 'annotations',
      zIndex: '2',
    };
    
    const annotationsOverlay = viewer.fabricjsOverlay(options);
    const points = [{x: 3200, y: 1600}, ...]
    const polygon = new fabric.Polygon(points, {
        fill: 'transparent',
        strokeWidth: 2,
        stroke: 'rgb(255,255,255)',
        objectCaching: false,
      });
      annotationsOverlay.fabricCanvas().add(polygon);
      annotationsOverlay.fabricCanvas().renderAll();
}
```

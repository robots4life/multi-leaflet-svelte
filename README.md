Without setContext and getContext Leaflet shows an error and cannot set the label on each map.

```js
DivOverlay.js:285 Uncaught (in promise) TypeError: Failed to execute 'appendChild' on 'Node': parameter 1 is not of type 'Node'.
    at NewClass._updateContent (DivOverlay.js:285:9)
    at NewClass.update (DivOverlay.js:187:8)
    at NewClass.onAdd (DivOverlay.js:113:8)
    at NewClass.onAdd (Popup.js:135:30)
    at NewClass._layerAdd (Layer.js:114:8)
    at NewClass.whenReady (Map.js:1477:13)
    at NewClass.addLayer (Layer.js:172:8)
    at NewClass.openOn (DivOverlay.js:63:8)
    at NewClass.openOn (Popup.js:131:38)
    at NewClass.openPopup (Popup.js:430:17)
```

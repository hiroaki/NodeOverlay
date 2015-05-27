# NodeOverlay

A custom overlay of Google Maps JavaScript API v3 that enables DOM element to overlay on the map.

If it enables `draggable` option to true, it requires external JavaScript library `ExtDraggableObject.js` produced by Gabriel Schneider, to make DOM objects draggable.


## Reference


### NodeOverlay class

This inherites `google.maps.OverlayView`.


#### Constructor

Constructor | Description
------------|------------
NodeOverlay( element:Element, opts?:NodeOverlayOptions ) | Setup the element to overlay.


#### Methods

Method | Return Value | Description
-------|--------------|------------
getOffset( anchor:NodeOverlay.AnchorPosition ) | Size | Get offset pixel that is a point from the top left of the element.
getPane() | MapPane | Get a MapPane that the overlay is appended.
getPosition() | LatLng | The current LatLng position.
getCurrentPoint() | Point | The current Point position.
setPointByLatLng( latlng:LatLng ) | Point | Set current Point position by LatLng, and returns coordinate as an instance of Point.
moveTo( latlng:LatLng ) | this | Same as the method `setPointByLatLng`, but this retuns `this`.

#### Events

Event | Arguments | Description
------|-----------|------------
click | MouseEvent | Fired when the user clicks over the element.
dragstart | MouseEvent | Fired when the mouse is first down and no dragging has taken place yet.
drag | MouseEvent | Fired repeatedly as the mouse is moved by the user while dragstart has been triggered.
dragend | MouseEvent | Fired when the user releases the mouse after dragstart has been triggered.
mousedown | MouseEvent | Fired when the user clicks and holds the mouse button down over the element.
mouseup | MouseEvent | Fired when the user releases the mouse button after mousedown has been triggered.


### NodeOverlayOptions object specification


#### Properties

Property | Type | Description
---------|------|------------
position | LatLng | NodeOveraly position. Required.
draggable | boolean | If true, the marker can be dragged. Default value is false.
anchorPosition | NodeOverlay.AnchorPosition | To specify anchor position of the element by constant. The default is `NodeOverlay.AnchorPosition.BOTTOM_CENTER`. (Note that it is not 'anchorPoint' )
pane | NodeOverlay.MapPane | It should append elements as children of the pane. The default is `NodeOverlay.MapPane.OVERLAY_LAYER`.
draggableOptions | ExtDraggableObjectOptions | Argument for the constructor of the ExtDraggableObject when `draggable` is true.


### NodeOverlay.AnchorPosition class

Identifiers used to specify the placement of anchor on the element.

```
+----------------+ 
+ TL    TC    TR + 
+                + 
+ MC    MC    MR + 
+                + 
+ BL    BC    BR + 
+----------------+ 
```


#### Constants

Constant | Description
---------|------------
TOP_CENTER | Anchor positioned in the center of the top.
TOP_LEFT | Anchor positioned in the top left.
TOP_RIGHT | Anchor positioned in the top right.
MIDDLE_CENTER | Anchor positioned in the center of the middle.
MIDDLE_LEFT | Anchor positioned in the middle left.
MIDDLE_RIGHT | Anchor positioned in the middle right.
BOTTOM_CENTER | Anchor positioned in the center of the bottom.
BOTTOM_LEFT | Anchor positioned in the bottom left.
BOTTOM_RIGHT | Anchor positioned in the bottom right.


### NodeOverlay.MapPane class

To specify pane that an instance of NodeOverlay appending on.


#### Constants

Constant | Description
---------|------------
MAP_PANE | To specify pane is the lowest pane and is above the tiles. It may not receive DOM events. (Pane 0).
OVERLAY_LAYER | To specify pane contains polylines, polygons, ground overlays and tile layer overlays. It may not receive DOM events. (Pane 1).
MARKER_LAYER | To specify pane contains markers. It may not receive DOM events. (Pane 2).
OVERLAY_SHADOW | To specify pane contains the marker shadows. It may not receive DOM events. (Pane 2).
OVERLAY_IMAGE | To specify pane contains the marker foreground images. (Pane 3).
FLOAT_SHADOW | To specify pane contains the info window shadow. It is above the overlayImage, so that markers can be in the shadow of the info window. (Pane 4).
OVERLAY_MOUSE_TARGET | To specify pane contains elements that receive DOM mouse events, such as the transparent targets for markers. It is above the floatShadow, so that markers in the shadow of the info window can be clickable. (Pane 5).
FLOAT_PANE | To specify pane contains the info window. It is above all map overlays. (Pane 6).


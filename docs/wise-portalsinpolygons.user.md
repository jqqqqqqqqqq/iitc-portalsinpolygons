## Modules

<dl>
<dt><a href="#module_helpers">helpers</a> : <code>function</code></dt>
<dd><p>Establish varioius helpers and polyfills.</p>
</dd>
<dt><a href="#module_ToolboxControlSection">ToolboxControlSection</a> : <code>function</code></dt>
<dd><p>ToolboxControlSection Class.  Provides a standardized way of adding toolbox controls and grouping controls in
the same &quot;family&quot;.</p>
</dd>
<dt><a href="#module_portalsinpolygon">portalsinpolygon</a> : <code>function</code></dt>
<dd><p>Portals-in-Polygon IITC plugin.  The plugin and its members can be accessed via
<code>window.plugin.portalsinpolygons</code>.  The &quot;public&quot; members are documented as module members while the more
friend and private members are documented as part of the <code>wrapper</code> function.</p>
</dd>
</dl>

## Members

<dl>
<dt><a href="#bringPortalsToFront">bringPortalsToFront</a></dt>
<dd><p>Bring portals to the front of the draw layers so that you can click on
them after drawing a circle or polygon over the portals.
<br>
Thanks to Zaso&#39;s &quot;Bring Portals To Front&quot; at
<a href="http://www.giacintogarcea.com/ingress/iitc/bring-portals-to-front-by-zaso.meta.js"> Zaso Items</a>.</p>
</dd>
<dt><a href="#displayPortals">displayPortals</a></dt>
<dd><p>Displays portals.  The portals are filtered based on selections in the layer chooser.
<br>
This function is generalized version of the <code>window.plugin.portalslist.displayPL</code> function.</p>
</dd>
<dt><a href="#displayContainedPortals">displayContainedPortals</a></dt>
<dd><p>Displays the portals contain in, and on the perimeter, of drawn polygons
and on any lines.</p>
</dd>
<dt><a href="#getContainedPortals">getContainedPortals</a> ⇒ <code>Object</code></dt>
<dd><p>Returns an array of IITC portals contained in the polygons and circles
drawn on the map.<br>
Checks for layers of type L.Polygon, which includes L.GeodesicPolygon
and L.GeodesicCircle, and L.Polyline, which in L.GeodesicPolyline.</p>
</dd>
<dt><a href="#getPortalsInMapBounds">getPortalsInMapBounds</a> ⇒ <code>Object</code></dt>
<dd><p>Returns the portals within the displayed map boundaries.</p>
</dd>
</dl>

## External

<dl>
<dt><a href="#external_window.map">window.map</a></dt>
<dd><p>The IITC map object (a Leaflet map).</p>
</dd>
<dt><a href="#external_window.portals">window.portals</a></dt>
<dd><p>The IITC portals object (used as a map) that contains a list of the cached
portal information for the portals in the current and surrounding view.</p>
</dd>
<dt><a href="#external_window.Render">window.Render</a></dt>
<dd><p>The map data render class which handles rendering into Leaflet the JSON data from the servers.  Needed to access
<code>window.Render.prototype.bringPortalsToFront</code>.</p>
</dd>
<dt><a href="#external_window.plugin.portalslist">window.plugin.portalslist</a></dt>
<dd><p>The &quot;show list of portals&quot; plugin object, properties, and methods.</p>
</dd>
</dl>

<a name="module_helpers"></a>

## helpers : <code>function</code>
Establish varioius helpers and polyfills.

<a name="module_ToolboxControlSection"></a>

## ToolboxControlSection : <code>function</code>
ToolboxControlSection Class.  Provides a standardized way of adding toolbox controls and grouping controls in


* [ToolboxControlSection](#module_ToolboxControlSection) : <code>function</code>
    * [~wrapper(plugin_info)](#module_ToolboxControlSection..wrapper)
        * [~portalsinpolygons](#module_ToolboxControlSection..wrapper..portalsinpolygons) : <code>object</code>
            * [.requiredPlugins](#module_ToolboxControlSection..wrapper..portalsinpolygons.requiredPlugins)
            * [.layerChooserName](#module_ToolboxControlSection..wrapper..portalsinpolygons.layerChooserName)
            * [.formattedPortalList(portals)](#module_ToolboxControlSection..wrapper..portalsinpolygons.formattedPortalList) ⇒
            * [.getLayerClassName(layer)](#module_ToolboxControlSection..wrapper..portalsinpolygons.getLayerClassName) ⇒ <code>String</code>
            * [.getPortalGuidsFilteredByLayerGroup(portals)](#module_ToolboxControlSection..wrapper..portalsinpolygons.getPortalGuidsFilteredByLayerGroup) ⇒ <code>Array.&lt;string&gt;</code>
            * [.getToolboxControls()](#module_ToolboxControlSection..wrapper..portalsinpolygons.getToolboxControls) ⇒ <code>Object</code>
            * [.isPortalDisplayed(portal)](#module_ToolboxControlSection..wrapper..portalsinpolygons.isPortalDisplayed) ⇒ <code>Object</code> &#124; <code>null</code>
            * [.mapZoomHasPortals()](#module_ToolboxControlSection..wrapper..portalsinpolygons.mapZoomHasPortals) ⇒ <code>boolean</code>
            * [.setup()](#module_ToolboxControlSection..wrapper..portalsinpolygons.setup)
    * [~L.LatLng](#external_L.LatLng)
        * [.isLeft(p1, p2)](#external_L.LatLng+isLeft) ⇒
    * [~L.Polyline](#external_L.Polyline)
        * [.getWindingNumber(p)](#external_L.Polyline+getWindingNumber)
    * [~L.Polygon](#external_L.Polygon)

<a name="module_ToolboxControlSection..wrapper"></a>

### ToolboxControlSection~wrapper(plugin_info)
Closure function for Portals-in-Polygon.

**Kind**: inner method of <code>[ToolboxControlSection](#module_ToolboxControlSection)</code>  

| Param | Type | Description |
| --- | --- | --- |
| plugin_info | <code>Object</code> | Object containing Greasemonkey/Tampermonkey information about the plugin. |
| plugin_info.script | <code>string</code> | Greasemonkey/Tampermonkey information about the plugin. |
| plugin_info.script.version | <code>string</code> | GM_info.script.version. |
| plugin_info.script.name | <code>string</code> | GM_info.script.name. |
| plugin_info.script.description | <code>string</code> | GM_info.script.description. |


* [~wrapper(plugin_info)](#module_ToolboxControlSection..wrapper)
    * [~portalsinpolygons](#module_ToolboxControlSection..wrapper..portalsinpolygons) : <code>object</code>
        * [.requiredPlugins](#module_ToolboxControlSection..wrapper..portalsinpolygons.requiredPlugins)
        * [.layerChooserName](#module_ToolboxControlSection..wrapper..portalsinpolygons.layerChooserName)
        * [.formattedPortalList(portals)](#module_ToolboxControlSection..wrapper..portalsinpolygons.formattedPortalList) ⇒
        * [.getLayerClassName(layer)](#module_ToolboxControlSection..wrapper..portalsinpolygons.getLayerClassName) ⇒ <code>String</code>
        * [.getPortalGuidsFilteredByLayerGroup(portals)](#module_ToolboxControlSection..wrapper..portalsinpolygons.getPortalGuidsFilteredByLayerGroup) ⇒ <code>Array.&lt;string&gt;</code>
        * [.getToolboxControls()](#module_ToolboxControlSection..wrapper..portalsinpolygons.getToolboxControls) ⇒ <code>Object</code>
        * [.isPortalDisplayed(portal)](#module_ToolboxControlSection..wrapper..portalsinpolygons.isPortalDisplayed) ⇒ <code>Object</code> &#124; <code>null</code>
        * [.mapZoomHasPortals()](#module_ToolboxControlSection..wrapper..portalsinpolygons.mapZoomHasPortals) ⇒ <code>boolean</code>
        * [.setup()](#module_ToolboxControlSection..wrapper..portalsinpolygons.setup)

<a name="module_ToolboxControlSection..wrapper..portalsinpolygons"></a>

#### wrapper~portalsinpolygons : <code>object</code>
Portals-in-Polygon namespace.  `portalsinpolygon` is set to `window.plugin.portalsinpolygons`.

**Kind**: inner namespace of <code>[wrapper](#module_ToolboxControlSection..wrapper)</code>  

* [~portalsinpolygons](#module_ToolboxControlSection..wrapper..portalsinpolygons) : <code>object</code>
    * [.requiredPlugins](#module_ToolboxControlSection..wrapper..portalsinpolygons.requiredPlugins)
    * [.layerChooserName](#module_ToolboxControlSection..wrapper..portalsinpolygons.layerChooserName)
    * [.formattedPortalList(portals)](#module_ToolboxControlSection..wrapper..portalsinpolygons.formattedPortalList) ⇒
    * [.getLayerClassName(layer)](#module_ToolboxControlSection..wrapper..portalsinpolygons.getLayerClassName) ⇒ <code>String</code>
    * [.getPortalGuidsFilteredByLayerGroup(portals)](#module_ToolboxControlSection..wrapper..portalsinpolygons.getPortalGuidsFilteredByLayerGroup) ⇒ <code>Array.&lt;string&gt;</code>
    * [.getToolboxControls()](#module_ToolboxControlSection..wrapper..portalsinpolygons.getToolboxControls) ⇒ <code>Object</code>
    * [.isPortalDisplayed(portal)](#module_ToolboxControlSection..wrapper..portalsinpolygons.isPortalDisplayed) ⇒ <code>Object</code> &#124; <code>null</code>
    * [.mapZoomHasPortals()](#module_ToolboxControlSection..wrapper..portalsinpolygons.mapZoomHasPortals) ⇒ <code>boolean</code>
    * [.setup()](#module_ToolboxControlSection..wrapper..portalsinpolygons.setup)

<a name="module_ToolboxControlSection..wrapper..portalsinpolygons.requiredPlugins"></a>

##### portalsinpolygons.requiredPlugins
An array of objects describing the required plugins.  Each object has

**Kind**: static property of <code>[portalsinpolygons](#module_ToolboxControlSection..wrapper..portalsinpolygons)</code>  
<a name="module_ToolboxControlSection..wrapper..portalsinpolygons.layerChooserName"></a>

##### portalsinpolygons.layerChooserName
Used when calling `window.isLayerGroupDisplayed(<String> name)`. E.g.,

**Kind**: static property of <code>[portalsinpolygons](#module_ToolboxControlSection..wrapper..portalsinpolygons)</code>  
<a name="module_ToolboxControlSection..wrapper..portalsinpolygons.formattedPortalList"></a>

##### portalsinpolygons.formattedPortalList(portals) ⇒
Gets and formats the portal information that will be used in the portal list display.

**Kind**: static method of <code>[portalsinpolygons](#module_ToolboxControlSection..wrapper..portalsinpolygons)</code>  
**Returns**: {Array<{portal:{Object}, values:{Array}, sortValues:{Array}>} Returns an array of

| Param | Type | Description |
| --- | --- | --- |
| portals | <code>Object</code> | An associative array of IITC portals. |

<a name="module_ToolboxControlSection..wrapper..portalsinpolygons.getLayerClassName"></a>

##### portalsinpolygons.getLayerClassName(layer) ⇒ <code>String</code>
Returns a string representation of the layer class (e.g., "L.GeodesicPolygon" and "L.Marker").

**Kind**: static method of <code>[portalsinpolygons](#module_ToolboxControlSection..wrapper..portalsinpolygons)</code>  
**Returns**: <code>String</code> - A string representation of the layer class.  

| Param | Type | Description |
| --- | --- | --- |
| layer | <code>L.Layer</code> | An object whose class extends L.Layer. |

<a name="module_ToolboxControlSection..wrapper..portalsinpolygons.getPortalGuidsFilteredByLayerGroup"></a>

##### portalsinpolygons.getPortalGuidsFilteredByLayerGroup(portals) ⇒ <code>Array.&lt;string&gt;</code>
Returns a set of guids belonging to the portals filtered by the layer group selections of

**Kind**: static method of <code>[portalsinpolygons](#module_ToolboxControlSection..wrapper..portalsinpolygons)</code>  
**Returns**: <code>Array.&lt;string&gt;</code> - An array of portal guids.  

| Param | Type | Description |
| --- | --- | --- |
| portals | <code>Object</code> | An associative array of IITC portal objects. |

<a name="module_ToolboxControlSection..wrapper..portalsinpolygons.getToolboxControls"></a>

##### portalsinpolygons.getToolboxControls() ⇒ <code>Object</code>
Returns the DOM elements containing the plugin controls to be appended to the IITC toolbox.

**Kind**: static method of <code>[portalsinpolygons](#module_ToolboxControlSection..wrapper..portalsinpolygons)</code>  
**Returns**: <code>Object</code> - DOM elements.  
<a name="module_ToolboxControlSection..wrapper..portalsinpolygons.isPortalDisplayed"></a>

##### portalsinpolygons.isPortalDisplayed(portal) ⇒ <code>Object</code> &#124; <code>null</code>
Returns the portal if it is displayed based on the the layer group selections of "Unclaimed Portals",

**Kind**: static method of <code>[portalsinpolygons](#module_ToolboxControlSection..wrapper..portalsinpolygons)</code>  
**Returns**: <code>Object</code> &#124; <code>null</code> - The IITC portal object or null.  

| Param | Type | Description |
| --- | --- | --- |
| portal | <code>Object</code> | An IITC portal object. |

<a name="module_ToolboxControlSection..wrapper..portalsinpolygons.mapZoomHasPortals"></a>

##### portalsinpolygons.mapZoomHasPortals() ⇒ <code>boolean</code>
Checks if there is sufficient portal data for the current map zoom.  When the zoom is set very far,

**Kind**: static method of <code>[portalsinpolygons](#module_ToolboxControlSection..wrapper..portalsinpolygons)</code>  
**Returns**: <code>boolean</code> - True if there is sufficient portal data; otherwise, returns false.  
**Todo**

- [ ] it might be easier to check if one of the portals has the data your are looking for (e.g., check if portal.options.data.title exists).

<a name="module_ToolboxControlSection..wrapper..portalsinpolygons.setup"></a>

##### portalsinpolygons.setup()
Setup function called by IITC.

**Kind**: static method of <code>[portalsinpolygons](#module_ToolboxControlSection..wrapper..portalsinpolygons)</code>  
<a name="external_L.LatLng"></a>

### ToolboxControlSection~L.LatLng
The Leaflet LatLng class.

**Kind**: inner external of <code>[ToolboxControlSection](#module_ToolboxControlSection)</code>  
**See**: [Leaflet](http://leafletjs.com/) documentation for further information.  
<a name="external_L.LatLng+isLeft"></a>

#### l.LatLng.isLeft(p1, p2) ⇒
Tests if a point is left|on|right of an infinite line.

**Kind**: instance method of <code>[L.LatLng](#external_L.LatLng)</code>  
**Returns**: >0 for p2 left of the line through this point and p1,
**See**: [Inclusion of a Point in a Polygon](http://geomalgorithms.com/a03-_inclusion.html) by Dan Sunday.  

| Param | Type | Description |
| --- | --- | --- |
| p1 | <code>LatLng</code> | Point The reference line is defined by `this` LatLng to p1. |
| p2 | <code>LatLng</code> | The point in question. |

<a name="external_L.Polyline"></a>

### ToolboxControlSection~L.Polyline
The Leaflet Polyline class.

**Kind**: inner external of <code>[ToolboxControlSection](#module_ToolboxControlSection)</code>  
**See**: [Leaflet](http://leafletjs.com/) documentation for further information.  
<a name="external_L.Polyline+getWindingNumber"></a>

#### l.Polyline.getWindingNumber(p)
Test for a point in a polygon or on the bounding lines of the polygon.  The

**Kind**: instance method of <code>[L.Polyline](#external_L.Polyline)</code>  
**Retuns**: <code>Number</code> The winding number (=0 only when the point is outside)  
**See**

- [Inclusion of a Point in a Polygon](http://geomalgorithms.com/a03-_inclusion.html) by Dan Sunday.
- [Leaflet.Geodesc](https://github.com/Fragger/Leaflet.Geodesic) for information about Leaflet.Geodesc by Fragger.


| Param | Type | Description |
| --- | --- | --- |
| p | <code>L.LatLng</code> | A point. |

<a name="external_L.Polygon"></a>

### ToolboxControlSection~L.Polygon
The Leaflet Polygon class.

**Kind**: inner external of <code>[ToolboxControlSection](#module_ToolboxControlSection)</code>  
**See**: [Leaflet](http://leafletjs.com/) documentation for further information.  
<a name="module_portalsinpolygon"></a>

## portalsinpolygon : <code>function</code>
Portals-in-Polygon IITC plugin.  The plugin and its members can be accessed via

**See**: [wrapper](wrapper)  

* [portalsinpolygon](#module_portalsinpolygon) : <code>function</code>
    * [~getPortalsCallback](#module_portalsinpolygon..getPortalsCallback) ⇒ <code>Object</code>
    * [~keepPortalCallback](#module_portalsinpolygon..keepPortalCallback) ⇒ <code>boolean</code>

<a name="module_portalsinpolygon..getPortalsCallback"></a>

### portalsinpolygon~getPortalsCallback ⇒ <code>Object</code>
A getPortalsCallback function returns returns an associative array of IITC portals (typically a subset

**Kind**: inner typedef of <code>[portalsinpolygon](#module_portalsinpolygon)</code>  
**Returns**: <code>Object</code> - An associative array of IITC portals.  
**See**

- [displayPortals](#displayPortals)
- [displayContainedPortals](#displayContainedPortals)

<a name="module_portalsinpolygon..keepPortalCallback"></a>

### portalsinpolygon~keepPortalCallback ⇒ <code>boolean</code>
A keepPortalCallback function returns true if the the provided portal passes the test implemented by the

**Kind**: inner typedef of <code>[portalsinpolygon](#module_portalsinpolygon)</code>  
**Returns**: <code>boolean</code> - True if the portal should be kept.  False if the portal should be ignored.  
**See**: [getPortalsInMapBounds](#getPortalsInMapBounds)  

| Param | Type | Description |
| --- | --- | --- |
| portal | <code>Object</code> | An IITC portal object. |

<a name="bringPortalsToFront"></a>

## bringPortalsToFront
Bring portals to the front of the draw layers so that you can click on

**Kind**: global variable  
<a name="displayPortals"></a>

## displayPortals
Displays portals.  The portals are filtered based on selections in the layer chooser.

**Kind**: global variable  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [getPortalsFn] | <code>getPortalsCallback</code> |  | Optional. An callback function that returns an associative array of IITC 	portals. If the function is not provided or set to undefined, the portals in the current map bounds will be 	used. |
| [title] | <code>String</code> | <code>&quot;Portal List&quot;</code> | Optional. A title for the portal list dialog.  The default is "Portal list". |

<a name="displayContainedPortals"></a>

## displayContainedPortals
Displays the portals contain in, and on the perimeter, of drawn polygons

**Kind**: global variable  
<a name="getContainedPortals"></a>

## getContainedPortals ⇒ <code>Object</code>
Returns an array of IITC portals contained in the polygons and circles

**Kind**: global variable  
**Returns**: <code>Object</code> - A collection of IITC portals.  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [keepPortalFn] | <code>keepPortalCallback</code> &#124; <code>true</code> &#124; <code>false</code> | <code>window.plugin.portalsinpolygons.isPortalDisplayed</code> | If a callback function is  provided, it will be called and passed the IITC portal object. If keepPortalFn is not a function and is set to  something falsy, the portals will not be filtered.  If keepPortalCallback is not provided, explicitly 	undefined, or something truthy, then the default filtering will be  performed which is to filter portals based on the layer group selections of "Unclaimed Portals", 	"Level 1 Portals" to "Level 8 Portals", "Enlightened" and "Resistance". |

<a name="getPortalsInMapBounds"></a>

## getPortalsInMapBounds ⇒ <code>Object</code>
Returns the portals within the displayed map boundaries.

**Kind**: global variable  
**Returns**: <code>Object</code> - An associative array of IITC portal objects (a subset of `window.portals`).  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| [keepPortalFn] | <code>keepPortalCallback</code> &#124; <code>true</code> &#124; <code>false</code> | <code>portalsinpolygons.isPortalDisplayed</code> | If a callback function is  provided, it will be called and passed the IITC portal object. If keepPortalFn is not a function and is set to  something falsy, the portals will not be filtered.  If keepPortalCallback is not provided, explicitly 	undefined, or something truthy, then the default filtering will be  performed which is to filter portals based on the layer group selections of "Unclaimed Portals", 	"Level 1 Portals" to "Level 8 Portals", "Enlightened" and "Resistance". |

<a name="external_window.map"></a>

## window.map
The IITC map object (a Leaflet map).

**Kind**: global external  
**See**: [Ingress Intel Total Conversion](https://iitc.me/)  
<a name="external_window.portals"></a>

## window.portals
The IITC portals object (used as a map) that contains a list of the cached

**Kind**: global external  
**See**: [Ingress Intel Total Conversion](https://iitc.me/)  
<a name="external_window.Render"></a>

## window.Render
The map data render class which handles rendering into Leaflet the JSON data from the servers.  Needed to access

**Kind**: global external  
**See**: [Ingress Intel Total Conversion](https://iitc.me/)  
<a name="external_window.plugin.portalslist"></a>

## window.plugin.portalslist
The "show list of portals" plugin object, properties, and methods.

**Kind**: global external  
**See**: ["show list of portals"](http://leafletjs.com/) plugin source code for further information.  
# TOC Widget

## Features
The TableOfContents widget provides a table of contents that allows the toggling of layer visibility. The style can be completely changed and skinned to match your own map design.

### Purpose
- This widget is meant to be simple. It's general purpose is for the end user to toggle layer visibility.
- A legend isn't included along side each layer. Use the legend widget for displaying information about the layers.
- There are options to specify a "settingsId" or "customContentId" which will create nodes with these Ids within the widget. These nodes will allow you to do your app's configuration of the layer or put custom content, like a transperency slider, underneath the layer's title.

### Known Issues
- Toggling of Mapservice, KML and WMS sublayers outside of the widget is not supported.
- Out of scale range for sublayers not supported.

[View it live](http://esri.github.io/arcgis-dijit-table-of-contents/)

## Quickstart

Layers need to match the [ArcGIS Webmap JSON Spec](http://resources.arcgis.com/en/help/arcgis-web-map-json/index.html#/Web_map_data/02qt0000000q000000/) for [operational layers](http://resources.arcgis.com/en/help/arcgis-web-map-json/index.html#/ArcGIS_map_service_operational_layer/02qt00000018000000/).

```javascript
var map = response.map;
    var layers = response.itemInfo.itemData.operationalLayers;

    myWidget = new TableOfContents({
      map: map,
      layers: layers
    }, "TableOfContents");
    myWidget.startup();
```

 [New to Github? Get started here.](https://github.com/)


## Setup
Set your dojo config to load the module.

	var package_path = window.location.pathname.substring(0, window.location.pathname.lastIndexOf('/'));
	var dojoConfig = {
		// The locationPath logic below may look confusing but all its doing is
		// enabling us to load the api from a CDN and load local modules from the correct location.
		packages: [{
			name: "application",
			location: package_path + '/js'
		}]
	};

## Require module
Include the module for the TOC.

	require(["application/TableOfContents", ... ], function(TableOfContents, ... ){ ... });

## Constructor

TableOfContents(options, srcNode);

### Options (Object)
|property|required|type|value|description|
|---|---|---|---|---|
|theme||string|TableOfContents|CSS Class for uniquely styling the widget.|
|map|x|Map|null|ArcGIS JS Map|
|layers|x|Object[]|null|[Operational Layers](http://resources.arcgis.com/en/help/arcgis-web-map-json/index.html#/ArcGIS_map_service_operational_layer/02qt00000018000000/) ([Layer Example](http://resources.arcgis.com/en/help/arcgis-web-map-json/index.html#/operationalLayer/02qt00000006000000/))|
|visible||Boolean|true|Show the widget|
|removeUnderscores||Boolean|true|Removes underscores from the layer title|
|subLayers||Boolean|true|Show sublayers in the list of layers|

#### Layers Object
This is what the layers array should look like. It follows the response from a webmap's operational layers.

``` javascript
layers = [
    {
        layer: LayerObject
        defaultSymbol: Symbol
        title: String
    },
    {
    	...
    }
];
```

## Properties
|property|type|description|
|---|---|---|
|theme|string|CSS Class for uniquely styling the widget.|
|map|Map|ArcGIS JS Map|
|layers|Array|Array of layers|
|visible|Boolean|Show the widget|
|loaded|Boolean|If the widget has been loaded.|
|removeUnderscores||Boolean|Removes underscores from the layer title|


## Methods
### startup
startup(): Start the widget.
### destroy
destroy(): Destroy the widget.
### show
show(): Show the widget.
### hide
hide(): hide the widget.
### refresh
refresh(): reload all layers and properties that may have changed.

## Events
### load
#### Example
	on(widget, 'load', function(evt){…})
#### Event Object

``` javascript
{}
```

### refresh
#### Example
	on(widget, 'refresh', function(evt){…})
#### Event Object

``` javascript
{}
```

### toggle
#### Example
	on(widget, 'toggle', function(evt){…})
#### Event Object
``` javascript
{
	layerIndex: Integer,
	subLayerIndex: Integer,
	visible: Boolean
}
```


## Requirements

* Notepad or HTML editor
* A little background with Javascript
* Experience with the [ArcGIS Javascript API](http://www.esri.com/) would help.

## Resources

* [ArcGIS for JavaScript API Resource Center](http://help.arcgis.com/en/webapi/javascript/arcgis/index.html)
* [ArcGIS Blog](http://blogs.esri.com/esri/arcgis/)
* [twitter@esri](http://twitter.com/esri)

## Issues

Find a bug or want to request a new feature?  Please let us know by submitting an issue.

## Contributing

Anyone and everyone is welcome to contribute.

## Licensing
Copyright 2012 Esri

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

A copy of the license is available in the repository's [license.txt](https://raw.github.com/Esri/arcgis-dijit-table-of-contents/master/license.txt) file.

[](Esri Tags: ArcGIS JavaScript API Layer TOC Table of Contents Public)
[](Esri Language: JavaScript)

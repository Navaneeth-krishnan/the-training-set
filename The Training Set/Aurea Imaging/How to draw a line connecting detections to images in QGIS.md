
It is always good to have a visualization of which images contribute to which detection.

![[Pasted image 20250718114457.png]]

### Steps:
1. Rename the images layer to only say "images"
2. Open the detections attribute table and set it in editing mode
3.  Add 2 new attributes using the "Open Field Calculator"
	1. Uncheck update only 1 selected field
	2. Output field type should be set to decimal
	3. In the expression  add: for the distance field
```
distance(  
  $geometry,  
  geometry(get_feature('images', 'id', "image_id"))  
)
```

for the angle field :
```
degrees(azimuth($geometry, geometry(get_feature('images', 'id', "image_id")))) 
```
4. Save and get out of editing mode
5.  Symbology (detections layer)
6. Add Simple Marker (Line)
7. Size: 
    1. Field type: distance
    2. Map Units
8. Rotation:
    1. Field type: degrees
9. Anchor point: VCenter to Bottom
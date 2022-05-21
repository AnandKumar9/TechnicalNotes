frame
bounds
position
anchorPoint
transform

bounds.origin - Origin of layer’s internal coordinate system. It does not affect the layer’s place but is relevant while adding subviews to the layer.

When new bounds are set for the layer, if its size attributes do not match the attributes of the frame the new attributes are used with the necessary expansion or shrinking done about the center of the frame. self.frame.origin ultimately takes into account all this and shows the rect's final origin.

The layer’s bounds.origin is by default 0,0, i.e. the upper left corner of the frame.

Hence, while adding a view to the screen’s main view when a frame is specified in initWithFrame which has an origin such as (50,100) if its layer.bounds are printed in debug console, the origin will be 0,0. To change the origin of a layer, new bounds having the new origin must be set for it. New origin is applied with respect to the upper left edge of the layer’s final rect.

Hence, there is also a difference between self.frame.origin and self.layer.bounds.origin.

A layer’s internal coordinate system most likely goes left and up instead of right and down. Hence, a bounds.origin of 20,20 will be left and upwards from the final rect’s upper left corner.

anchorPoint - It defines the origin of the coordinate system in which the transform gets applied. Its value is normalized in the range of 0.0 - 1.0 and its equivalent points value can be obtained by multiplying it with bounds.size.

So it looks like bounds.origin is the origin of internal coordinate system with respect to which subviews are added to the layer and anchorPoint is the origin with respect to which the transform is applied.

transform - When a transform is applied, even the bounds.origin changes as the transform gets applied to it as well. Also, applying a transform can also changes the x and y axes. For example, if a rotation transform of 90 degrees is applied the axes also get rotated equally. This matters when a subview is being added to the layer.

position - Specifies the location of layer (rather its anchorPoint) relative to its parent view’s coordinate system. Also, by default its probably the center point of the parent view's frame.

Probably what happens is that anchorPoint should coincide with position. Hence if position is specified, the precise anchorPoint in parent view's coordinate system is known and then if the anchorPoint unit value has also been specified then that is used to determine the center of the layer. This way position and anchorPoint can also determine the layer’s final layout.

[link](http://macoscope.com/blog/understanding-frame/) - Macoscope blog


*****

How they all fit together - 

position tells the precise position of anchorPoint.
unit value of anchorPoint determines the layer’s center.
layer is then laid out as per its bounds.size about its center.
transform is then applied about the anchorPoint.
bounds.origin finally provides the coordinate system for any subviews then added to it.
The internal coordinate system goes up and left instead of down and right. 


*****

M_2_PI - 2 times the reciprocal of pi.
2*M_PI - 2 times pi.

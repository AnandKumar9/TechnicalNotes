Sample codebase - 

32. Layers/TestCALayer - commit no.  eb13f46 has most of the layers, uncomment as needed
32. Layers/WAActivityIndicatorView-master - nice effects using CAReplicatorLayer
Ray Wanderlich/LayerPlayer-master - Shows features of several layers

***********

Does CALayer’s mask property directly correspond to UIView mask property.
What exactly is the anchorPointZ property in CALayer.
What is CALayer style property.

***********

insetBy method expands (or collapses) a frame by the specified dimensions, about the frame's center. It changes the origin as well.

let insetReticleFrameInSelf = self.convert(reticleFrame, from: reticleView?.superview).insetBy(dx: -2.0, dy: -2.0)

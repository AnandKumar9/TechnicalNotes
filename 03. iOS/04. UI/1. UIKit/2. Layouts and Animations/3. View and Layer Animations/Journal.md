CATransactions are not affected by Toggle Slow Animations option of simulator.

Animating drawing of a path using CAShapeLayer ([link](http://oleb.net/blog/2010/12/animating-drawing-of-cgpath-with-cashapelayer/%09)). Can be done very easily as strokeEnd property of CAShapeLayer is animatable.

**********

Test codebase - 23. Animation/TestAnimationsInSwift (commit no. 3509582 - Has all basic CoreAnimation and view animation methods)

Core Animation programming guide
Other ObjC.io animations articles
CATransactions and actions
Pop animation engine by Facebook. What does it do, try it.

Haven’t yet tested UIViewController’s transition(from:to:duration:options:animations:completion:) in test codebase. But should work as expected.

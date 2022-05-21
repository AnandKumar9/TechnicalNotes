```
UIDynamicAnimator
UIDynamicAnimatorDelegate protocol
UIDynamicBehavior
UIDynamicItemGroup
UIDynamicItem protocol
UICollisionBehaviorDelegate protocol
UIDynamicItemCollisionBoundsType enum
```

Most of the behaviors (but not all) have these methods - 
```
init(items:)
items (read only)
addItem(_:)
removeItem
```

UIDynamicAnimator -
```
init(referenceView:)
init(collectionViewLayout:)
addBehavior(_:)
removeBehavior(_:)
removeAllBehaviors()
behaviors
_debugEnabled
_debugInterval
_debugAnimationSpeed
```

UIDynamicItem protocol -
```
center
bounds (read only)
transform
collisionBoundsType (optional)
```

UIGravityBehavior -
```
gravityDirection
angle
magnitude
setAngle(_:magnitude:)
```

UICollisionBehavior -

```
collisionMode
translatesReferenceBoundsIntoBoundary
setTranslatesReferenceBoundsIntoBoundaryWithInsets(_:)
addBoundaryWithIdentifier(_:forPath:)
addBoundaryWithIdentifier(_:fromPoint:toPoint:)
UICollisionBehaviorDelegate protocol -
collisionBehavior(_:beganContactForItem:withBoundaryIdentifier:atPoint:)
collisionBehavior(_:beganContactForItem:withItem:atPoint:)
collisionBehavior(_:endedContactForItem:withBoundaryIdentifier:)
collisionBehavior(_:endedContactForItem:withItem:)


UIDynamicItemBehavior -

allowsRotation
angularVelocity
density
elasticity
friction
resistance
charge
anchored
```

UIPushBehavior - 
```
mode - UIPushBehaviorModeContinuous, UIPushBehaviorModeInstantaneous
magnitude
angle
pushDirection
setAngle(_:magnitude:)
targetOffsetFromCenterForItem(_:)
setTargetOffsetFromCenter(_:forItem:)
active
```

UIAttachmentBehavior -
```
attachedBehaviorType - UIAttachmentBehaviorTypeItems, UIAttachmentBehaviorTypeAnchor
init(item:attachedToAnchor:)
init(item:offsetFromCenter:attachedToAnchor:)
init(item:attachedToItem:),
init(item:offsetFromCenter:attachedToItem:offsetFromCenter:)
limitAttachmentWithItem(_:offsetFromCenter:attachedToItem:offsetFromCenter:)
```

UISnapBehavior -
```
init(item:snapToPoint:)
snapPoint
damping
```

UIFieldBehavior - 
```
minimumRadius
falloff
position
region
strength
dragField()
springField()
electricField()
magneticField()
vortexField()
fieldWithEvaluationBlock(_:)
```

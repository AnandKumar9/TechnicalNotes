Extracting a polygon from a UIImage -

func applyMask_usingBezierPath(bezierPath: UIBezierPath) {
        
        let boundingBox = bezierPath.cgPath.boundingBox
        UIGraphicsBeginImageContextWithOptions(boundingBox.size, false, (self.imageView1.image?.scale)!)
        
        let context = UIGraphicsGetCurrentContext()
        context?.translateBy(x: -boundingBox.origin.x, y: -boundingBox.origin.y)
        context?.addPath(bezierPath.cgPath)
        context?.clip()
        
        self.imageView1.image?.draw(in: CGRect(origin: .zero, size: (self.imageView1.image?.size)!))
        let editedImage = UIGraphicsGetImageFromCurrentImageContext()
        UIGraphicsEndImageContext()
        
        self.imageView2.image = editedImage
        
    }

[Link](http://stackoverflow.com/a/35611207/1135417)


****************

Rotating a UIImage -

public func imageRotatedByDegrees(degrees: CGFloat, flip: Bool) -> UIImage {
    
    let degreesToRadians: (CGFloat) -> CGFloat = {
        return $0 / 180.0 * CGFloat(M_PI)
    }
    
    let placeholderView = UIView(frame: CGRect(origin: .zero, size: CGSize(width: size.width, height: size.height)))
    placeholderView.transform = CGAffineTransformMakeRotation(degreesToRadians(degrees))
    let placeholderViewSize = placeholderView.frame.size
    
    UIGraphicsBeginImageContext(placeholderViewSize)
    let context = UIGraphicsGetCurrentContext()
    
    // Move the origin to the middle of the image so we will rotate and scale around the center.
    CGContextTranslateCTM(context!, placeholderViewSize.width / 2.0, placeholderViewSize.height / 2.0)
    
    // Rotate the image context
    CGContextRotateCTM(context!, degreesToRadians(degrees))
    
    // Now, draw the rotated/scaled image into the context
    var yFlip: CGFloat
    
    if(flip){
        yFlip = CGFloat(-1.0)
    } else {
        yFlip = CGFloat(1.0)
    }
    
    CGContextScaleCTM(context!, yFlip, -1.0)
    CGContextDrawImage(context!, CGRect(x: -size.height / 2, y: -size.width / 2, width: size.height, height: size.width), self.CGImage!)
    
    let newImage = UIGraphicsGetImageFromCurrentImageContext()
    UIGraphicsEndImageContext()
    
    return newImage!
}


[Link](https://ruigomes.me/blog/how-to-rotate-an-uiimage-using-swift/)

****************

Altering a UIImage to just change few things (such as image orientation) -

let editedImageRotated = UIImage(CGImage: (editedImage?.CGImage)!, scale: (editedImage?.scale)!, orientation: .Right)

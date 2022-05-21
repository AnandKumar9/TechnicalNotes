(Creating custom layouts, [Link](http://skeuo.com/uicollectionview-custom-layout-tutorial)) The initial code steps - 

Add a collection view controller
Create a new subclass of UICollectionViewLayout
Select the collection view in document outline
Go to attributes inspector, change the layout from flow to custom and assign it to the new custom subclass
Change the background color of collection view in viewDidLoad to ensure code is working so far
Create a new subclass of UICollectionViewCell and use a new background color in its initWithFrame
Create an outlet for the collection view controller's layout

In the collection view cell, override initWithFrame: to set a new background color for every cell
Create data attributes as properties in custom layout, assign them values in a custom method and call that method in both init and initWithCoder

Override prepareLayout method of UICollectionViewLayout where the layout for all the items are calculated and stored in a dictionary
Override layoutAttributesForElementsInRect: to return the layout attributes for all the elements in the passed rect.
Override layoutAttributesForItemAtIndexPath: method.
Override collectionViewContentSize: method. This method should return the size of the entire collection view. The total height is calculated using inset, no. of items, item height, etc. But the width is just taken from collectionView.bounds.size.width. This might be because we are using a collection view controller which occupies the entire screen and its width will be fixed.

Register BHAlbumPhotoCell as the class to be used for the collection view cells and override basic datasource methods (numberOfSections, numberOfItemsInSection) with some hard code values for now.

Implement the willRotateToInterfaceOrientation method to have a different no. of columns and a different inset when device is in landscape.

Also override the setters of various properties of the collection view layout class to do an invalidateLayout every time their setter is called.
Add model classes for album and photo and create them in collection view controller's viewDidLoad. Get the images from a remote URL.
Set the layer properties of the cell in the initWithFrame method of BHAlbumPhotoCell. Also override prepareForReuse to set the image of the cell as nil.

Assign the album and image in collection view's cellForItemAtIndexPath and get the image view's image in a asynchronous block.

********************** (Up to above is enough to get a basic understanding of collection view cells)

In BHPhotoAlbumLayout, assign different transforms to each item and also do the rasterization in BHAlbumPhotoCell.
In collection view controller's viewDidLoad, have the photoCount of each album as a suitable random number.
In custom layout's prepareForLayout, have the zIndex appropriately set up so that the with item highest priority in operation queue is at the topmost.

********************** (Implementing supplementary views for each section)

Add a property in collection view layout class for the supplementary view's property, have a default value for it in setUp method and override its setter as done for other properties. There will be one supplementary view for every section here.

Set the attributes of the title supplementary view as another key in layoutInfo dictionary of collection vie layout class, calculate the attributes in prepareLayout method and then update the methods frameForAlbumTitleAtIndexPath:, frameForAlbumPhotoAtIndexPath: and collectionViewContentSize: accordingly.

Add the implementation for layoutAttributesForSupplementaryViewOfKind:atIndexPath: to return the layout attributes of the supplementary views.

Create custom subclass of UICollectionReusableView to represent the supplementary views and name it as BHAlbumTitleReusableView.

Override its init method to set the label properties such as textColor, etc.

Also, override its prepareForReuse method to set the text as nil.
Finally implement the collectionView:viewForSupplementaryElementOfKind:atIndexPath: method in collection view controller to set the supplementary views.

********************** (Implementing decoration view for the entire collection view)

Create a UICollectionReusableView subclass to represent decoration view and name it as BHEmblemView. Add a method to it to return a size and override initWithFrame to add an image to it.

Define a decoration view kind in collection view layout class and register it in its setUp method.

Add a method in collection view layout which returns the frame for the decoration view, have it as a frame above the top of collection view (i.e. all its sections).

Override the prepareForLayout method to create layoutAttributes for the decoration view and implement the layoutAttributesForDecorationViewOfKind:atIndexPath: method of collection view to return the attributes.

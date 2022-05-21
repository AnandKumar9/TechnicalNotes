UICollectionView
UICollectionViewDataSource 
UICollectionViewDelegate 
UICollectionViewLayout 
UICollectionViewLayoutAttributes 
UICollectionViewFlowLayout
UICollectionViewTransitionLayout
UICollectionReusableView 
UICollectionViewCell 

UICollectionViewController is similar to UITableViewController and should be used if the only view in a view controller is a collection view.

UICollectionViewLayout is the class which represents a collection view layout. It is the class that needs to be subclassed for creating a custom layout.

UICollectionViewLayoutAttributes is the class which represents the layout attributes of particular cell, supplementary view, etc.
UIScrollView -> UICollectionView
UIView -> UICollectionReusableView ->  UICollectionViewCell
UICollectionViewCell is the class which represents an item (i.e. a collection view cell).
UICollectionReusableView denotes all cells and supplementary views (as well as decoration view?) in a collection view. For cells in particular, a subclass of UICollectionReusableView (UICollectionViewCell) is there.

*********

UICollectionView -> indexPathsForVisibleItems
UICollectionView -> collectionViewLayout
UICollectionView -> dataSource
UICollectionView -> delegate
UICollectionView -> allowsSelection
UICollectionView -> -reloadData
UICollectionView -> -registerClass:forCellWithReuseIdentifier:
UICollectionView -> -registerNib:forCellWithReuseIdentifier:
UICollectionView -> -dequeueReusableCellWithReuseIdentifier:forIndexPath:
UICollectionView -> -dequeueReusableSupplementaryViewOfKind:withReuseIdentifier:forIndexPath: 
UICollectionView -> -registerClass:forSupplementaryViewOfKind:withReuseIdentifier:
UICollectionView -> -registerNib:forSupplementaryViewOfKind:withReuseIdentifier:
UICollectionView -> -performBatchUpdates:completion:
UICollectionView -> -deleteItemsAtIndexPaths

UICollectionViewDataSource -> -numberOfSectionsInCollectionView:
UICollectionViewDataSource -> -collectionView:numberOfItemsInSection:
UICollectionViewDataSource -> -collectionView:cellForItemAtIndexPath:
UICollectionViewDataSource -> -collectionView:viewForSupplementaryElementOfKind:atIndexPath:
UICollectionViewDelegate -> –collectionView:shouldSelectItemAtIndexPath:
UICollectionViewDelegate -> –collectionView:shouldHighlightItemAtIndexPath:
UICollectionViewDelegate -> –collectionView:didEndDisplayingCell:forItemAtIndexPath:
UICollectionViewDelegate -> –collectionView:transitionLayoutForOldLayout:newLayout:
UICollectionViewDelegate -> –collectionView:shouldShowMenuForItemAtIndexPath:
UICollectionViewDelegate -> -collectionView:canPerformAction:forItemAtIndexPath:withSender:
UICollectionViewDelegate -> -collectionView:performAction:forItemAtIndexPath:withSender:
UICollectionViewLayout -> -prepareLayout
UICollectionViewLayout -> -layoutAttributesForItemAtIndexPath:
UICollectionViewLayout -> -layoutAttributesForElementsInRect:
UICollectionViewLayout -> -collectionViewContentSize:
UICollectionViewLayout -> -registerClass:forDecorationViewOfKind: 
UICollectionViewLayout -> -registerNib:forDecorationViewOfKind: 
UICollectionViewLayout -> -shouldInvalidateLayoutForBoundsChange
UICollectionViewLayout -> -initialLayoutAttributesForAppearingItemAtIndexPath:
UICollectionViewLayout -> -finalLayoutAttributesForDisappearingItemAtIndexPath:
UICollectionViewLayout -> -prepareForCollectionViewUpdates
UICollectionViewLayout -> -targetContentOffsetForProposedContentOffset:withScrollingVelocity:
UICollectionViewLayout -> -invalidateLayout
UICollectionViewLayoutAttributes -> +layoutAttributesForCellWithIndexPath:
UICollectionViewLayoutAttributes -> +layoutAttributesForSupplementaryViewOfKind:withIndexPath:
UICollectionViewLayoutAttributes -> +layoutAttributesForDecorationViewOfKind:withIndexPath:
UICollectionViewLayoutAttributes -> representedElementCategory (indicates if the attributes are for items, supplementary views or decoration views)
UICollectionViewLayoutAttributes -> representedElementKind (returns the kind in case of supplementary view or decoration views)
UICollectionViewLayoutAttributes -> indexPath (applicable for items)
UICollectionViewLayoutAttributes -> frame
UICollectionViewLayoutAttributes -> zIndex
UICollectionViewLayoutAttributes -> transform3D
UICollectionViewLayoutAttributes -> size
UICollectionViewLayoutAttributes -> hidden
UICollectionViewFlowLayout -> itemSize
UICollectionViewFlowLayout -> minimumLineSpacing
UICollectionViewFlowLayout ->  sectionInset
UICollectionViewFlowLayout ->  scrollDirection
UICollectionViewDelegateFlowLayout -> –collectionView:layout:sizeForItemAtIndexPath:
UICollectionViewDelegateFlowLayout -> –collectionView:layout:minimumLineSpacingForSectionAtIndex:
UICollectionViewDelegateFlowLayout -> –collectionView:layout:referenceSizeForHeaderInSection:
UICollectionViewDelegateFlowLayout -> –collectionView:layout:referenceSizeForFooterInSection:

UICollectionReusableView -> prepareForReuse
UICollectionViewCell -> contentView
UICollectionViewCell -> selectedBackgroundView

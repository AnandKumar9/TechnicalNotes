What really is UICollectionViewUpdateItem? Page 11
Transitioning Between Layouts - Page 28
UICollectionViewDelegateFlowLayout
Custom layout example - Page 54

If needed, supplementary views and decoration views can be configured to have index paths with more than just two components (i.e. section and item). How?

Supplementary view - 

The thing to understand is that supplementary views are tied to index paths, hence theoretically speaking there can be a multiple supplementary views for every index path, each of them should have different 'kinds' however. They can be assigned any frame and the key is when they are accounted for in the method layoutAttributesForElementsInRect:. I think that is how a collection view gets to know that there are supplementary views to be shown.

Layout Attributes -

Two of the readonly properties of UICollectionViewLayoutAttributes are representedElementCategory and representedElementKind. representedElementCategory is the property that indicates the element's type, i.e. whether its an item, supplementary view or decoration view. representedElementKind indicates the element's kind, in case of a supplementary view or decoration view.
Every time a layoutAttributes is created, its created for a cell, supplementary view or decoration view.

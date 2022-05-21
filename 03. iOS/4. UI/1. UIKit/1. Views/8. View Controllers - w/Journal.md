Is it possible to have a completely transparent tab bar in a tab bar controller?

Adding a view controller using addChildViewController -

```
[self addChildViewController:_pageViewController];
[self.view addSubview:_pageViewController.view];
```

Showing a view controller modally -
-presentModalViewController:animated:


The master view controller in a split view controller, automatically shows a tab bar in the bottom in iOS7. To hide it the following property of the master view controller should be set as NO.
extendedLayoutIncludesOpaqueBars

UITableView - setSeparatorInset (Specifies if the table view cell separators should start right from the edge)
[self.tableView setSeparatorInset:UIEdgeInsetsZero];

A general background color can be specified for a table view from the storyboard. For individual cells, it can be specified as needed from the code which then overrides what is specified in storyboard.

When a table view cell is selected, the previously selected table view cell is already marked as unselected and hence does not show its selectedBackgroundView anymore.
selectedBackgroundView property indicates the background view used by a table view cell when it is selected.

webView:shouldStartLoadWithRequest:navigationType: method can be used to specify if a web view should load a URL.
UIWebViewNavigationTypeLinkClicked navigation type indicates the user had tapped on a link.

For setting the attributes of a bar item (such as bar button item), setTitleTextAttributes:forState: method can be used.
UIFont *font = [UIFont fontWithName:APP_FONT_NAME_REGULAR size:15.0f];
NSDictionary *attributes = [NSDictionary dictionaryWithObject:font forKey:NSFontAttributeName];
_leftButton = [[UIBarButtonItem alloc] initWithTitle:@"Templates" style:UIBarButtonItemStyleBordered target:self action:nil];
[_leftButton setTitleTextAttributes:attributes forState:UIControlStateNormal];

It can also be done for a segmented control.
[self.eLogSegmentedControl setTitleTextAttributes:attributes forState:UIControlStateNormal];

The width of master frame in a split view controller can be configured using its _masterColumnWidth variable.
[self setValue:@(200.0f) forKey:@"_masterColumnWidth”];   //self is a subclass of UISplitViewController

For turning off the auto bouncing in scroll views.
formDescriptionWebView.scrollView.bounces = NO;

For putting a subview one level beneath.
[self.pendingLogListViewController.view sendSubviewToBack:eLogSegmentedControl];

Instantiating a nib file.
```
FilterStatusPopoverView *filterStatusPopoverView = [[[NSBundle mainBundle] loadNibNamed:NSStringFromClass([FilterStatusPopoverView class]) owner:self options:nil] objectAtIndex:0];

CGRectIntersectsRect returns whether two rectangles intersect.
if (CGRectIntersectsRect(rect, attributes.frame)) {
     [allAttributes addObject:attributes];
}

CGRectContainsPoint returns whether a rectangle contains a particular point.
if (CGRectContainsPoint([self.bug.layer.presentationLayer frame], tapLocationCGPoint)) { .. }
```

UIEdgeInsets is a struct that has 4 float attributes - top, left, bottom, right. They normally indicate the clear spaces to be left across a rectangle and are usually applied to rectangles to shrink or expand their area. UIEdgeInsetsMake() is the function used to create an edge inset.

Handling insets for iPhone 4 or 5.
```
CGFloat sideInset = [UIScreen mainScreen].preferredMode.size.width == 1136.0f?45.0f:25.0f;
```
What is UIKIT_EXTERN?
UIKIT_EXTERN NSString * const BHPhotoAlbumLayoutAlbumTitleKind;

Detecting when the user taps back button for a view controller in navigation controller.

```
- (void)viewWillDisappear:(BOOL)animated {
    if ([self.navigationController.viewControllers indexOfObject:self]==NSNotFound) {
       // back button was pressed.  We know this is true because self is no longer in the navigation stack.  
    }
    [super viewWillDisappear:animated];
}
```

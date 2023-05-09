One way to hide the cursor on a text field is to set the tint color of text field as clearColor. The cursor is still there, but it will not be visible to the user. This is usually sufficient when the keyboard is not shown and another picker view is shown instead. ([link](http://stackoverflow.com/a/20101376/1135417))

self.startField.tintColor = [UIColor clearColor];

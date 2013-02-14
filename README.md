uialertview-blocks
==================

UIAlertView as it was meant to be.

Why?
====

UIAlertView is great, but it was designed back in the days when blocks weren't available. And now that we have them it is a lot cleaner to use them.

In addition, it gets cumbersome if you have more than one UIAlertView on a page that requires the use of a delegate. With blocks, the views are contained and there isn't the same functional code spread out in different parts of your controller file.

How?
====

It's pretty simple. There is one method added via the UIAlertView+Blocks category:

```
-(void)showWithBlock:^(NSInteger buttonIndex)clickedBlock cancelBlock:^(void)cancelBlock;
```

A trivial example:

```
UIAlertView *alert = [[UIAlertView alloc] initWithTitle:@"Title" message:@"A Message" delegate:nil cancelButtonTitle:@"Cancel Text" otherButtonTitles:@"Button 1", @"Button 2", nil];
                
[alert showWithBlock:^(NSInteger buttonIndex) {
    if (buttonIndex == 1) { //purchase all!
        NSLog(@"OMG! Button 1 was pressed!")
        
    } else if (buttonIndex == 2) { //purchase this tour
        NSLog(@"OMG! Button 2 was pressed!")
    }
} cancelBlock:^{
    NSLog(@"This was cancelled, yo!")
}];
```

Copyright
=========
All code in this library is published under the terms of the MIT License.
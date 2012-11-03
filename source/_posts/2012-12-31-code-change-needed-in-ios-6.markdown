---
layout: post
title: "Code Change Needed in iOS 6"
date: 2012-10-30 00:03
comments: true
categories: iOS
published: false
---

## presentModalViewController ##

Starting from iOS 6, `UIViewController` deprecated 

	- (void)presentModalViewController:(UIViewController *)modalViewController animated:(BOOL)animated

Starting from iOS 5, the replacement is

	- (void)presentViewController:(UIViewController *)viewControllerToPresent animated: (BOOL)flag completion:(void (^)(void))completion

If you *really* need to support the older iOS 4 and below, and mix in the new replacement, you would need to [check](http://stackoverflow.com/questions/12445190/dismissmodalviewcontrolleranimated-deprecated) using `respondsToSelector`.

    if ([self respondsToSelector:@selector(presentViewController:animated:completion:)])
        [self presentViewController:navController animated:YES completion:nil];
    else
        [self presentModalViewController:navController animated:YES];


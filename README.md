# ViewFullTransition

<table>
<tr>
<th>Zalo/Telegrame View Full</th>
<th>BottomSheet</th>
<th>Web View Facebook</th>
</tr>
<tr>
<td><img src="https://github.com/Truong98/ViewFullTransitonAnimation/blob/master/DemoGif/Viewfull.gif"/></td>
<td><img src="https://github.com/Truong98/ViewFullTransitonAnimation/blob/master/DemoGif/BottomSheet.gif"/></td>
<td><img src="https://github.com/Truong98/ViewFullTransitonAnimation/blob/master/DemoGif/Web%20view.gif"/></td>
</tr>
</table>

## Example

To run the example project, clone the repo, and start  in Xcode.

## Requirements

- iOS 10.0+

## Usage

### Get Started

Import the `ViewFullTransition` folder where you want to use it.

```swift
/// Create new UIViewController
 let viewFullVC = WebViewFullVC()
 
 let effectColor = UIColor.black
 
 // Create Params to pass in 'ViewFullTransitionController'
 var params = ParamsViewFullTransition(sourceViewController: self)
 
 /// Set destViewController in params is viewFullVC (line 32)
 params.destViewController = viewFullVC
 
 /// Set duration present animation
 params.presentParams.duration = 0.5
 
 params.dismissParams.duration = 0.5
 params.dismissParams.minFlickMagnitude = 1500
 params.dismissParams.applyFlickVelocity = false
 params.dismissParams.interactiveDirection = .Down
 params.dismissParams.yAxisInteractivecompletionThreshold = 0.4
 
 /// Create present animator to handle present transition event
 let presentAnimator = VFPresentAnimator(sourceTransition: self, viewFullTransition: viewFullVC)
 /// We need to set startState and endState
 presentAnimator.startState = VFAnimatedState(effectColor: effectColor, effectAlpha: 0)
 presentAnimator.endState = VFAnimatedState(effectColor: effectColor, effectAlpha: 1)
 
 /// Pass presentAnimator in params
 params.presentAnimator = presentAnimator

 let interactionAnimator = VFDismissalInteractionAnimator(sourceTransition: self, viewFullTransition: viewFullVC)
 interactionAnimator.interactiveHorizontalTracking = false
 interactionAnimator.clipsToRange = true
 interactionAnimator.startState = VFAnimatedState(effectColor: effectColor, effectAlpha: 1)
 interactionAnimator.endState = VFAnimatedState(effectColor: effectColor, effectAlpha: 0)
 params.dismissalInteractionAnimator = interactionAnimator

 let dismissAnimator = VFDismissAnimator(sourceTransition: self, viewFullTransition: viewFullVC)
 dismissAnimator.startState = VFAnimatedState(effectColor: effectColor, effectAlpha: 1)
 dismissAnimator.endState = VFAnimatedState(effectColor: effectColor, effectAlpha: 0)
 params.dismissAnimator = dismissAnimator

/// Create ViewFullTransitionController that conform 'UIViewControllerTransitioningDelegate'
 viewFullTransition = ViewFullTransitionController(params: params)

 viewFullVC.transitioningDelegate = viewFullTransition
 viewFullVC.modalPresentationStyle = .custom

 present(viewFullVC, animated: true, completion: nil)
```

### Customization



## Author

[Truong Nguyen](https://www.facebook.com/truongnguyen91723213?ref=bookmarks)

## License

ViewFullTransition is available under the MIT license. See the LICENSE file for more info.

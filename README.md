# ViewFullTransition

## Example

To run the example project, clone the repo, and start  in Xcode.

## Requirements

- iOS 10.0+

## Usage

### Get Started

Import the `ViewFullTransition` folder where you want to use it.

```swift
 let viewFullVC = WebViewFullVC()
 let effectColor = UIColor.black
 var params = ParamsViewFullTransition(sourceViewController: self)
 params.destViewController = viewFullVC
 
 params.presentParams.duration = 0.5
 
 params.dismissParams.duration = 0.5
 params.dismissParams.minFlickMagnitude = 1500
 params.dismissParams.applyFlickVelocity = false
 params.dismissParams.interactiveDirection = .Down
 params.dismissParams.yAxisInteractivecompletionThreshold = 0.4
 
 let presentAnimator = VFPresentAnimator(sourceTransition: self, viewFullTransition: viewFullVC)
 presentAnimator.startState = VFAnimatedState(effectColor: effectColor, effectAlpha: 0)
 presentAnimator.endState = VFAnimatedState(effectColor: effectColor, effectAlpha: 1)
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

 viewFullTransition = ViewFullTransitionController(params: params)

 viewFullVC.transitioningDelegate = viewFullTransition
 viewFullVC.modalPresentationStyle = .custom

 present(viewFullVC, animated: true, completion: nil)
```

### Customization

Most of the built-in animators work best in **Paging** mode and they have additional parameters that you can tweak for better transitions.
You can also write your own animators by implementing the protocol `LayoutAttributesAnimator`.

## Author

[Truong Nguyen](https://www.facebook.com/truongnguyen91723213?ref=bookmarks)

## License

ViewFullTransition is available under the MIT license. See the LICENSE file for more info.

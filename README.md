# Multibrowsers

An iOS app to demonstrate the adding and subtracting the arranged subviews of UIStackView as well as responding to the iOS interface environment changes through traitCollectionDidChange(_: )


Portrait mode in an iPad uses the Regular class size:

<img src="https://github.com/igibliss00/Multibrowsers/blob/master/README_assets/1.png" width="400">

When an iPad is in a landscape mode and the apps are split 50/50, the size class comes Compact:

<img src="https://github.com/igibliss00/Multibrowsers/blob/master/README_assets/2.png" height="400">

## Features

### UIStackView

UIStackView is a feature that was introduced back in iOS 9.  This is the backbone of your design to align multiple UI elements on your screen similar to Flexbox in CSS.  The keyword here is the “multiple UI elements” because you can individually set each UI element with Auto Layout yourself without stack view, but stack view makes applying Auto Layout to multiple elements easier for you especially when new element is inserted or deleted from the view.  

Each element within the stack view is referred to as a subview and it can be added, removed, or inserted in between any subviews. The method addArrangedSubview is used in this case, and not to be confused with addSubview.  UIStackView class uses the arrangedSubviews property for the array of subviews.

There are four main things to consider when you’re using UIStackView: the stack view’s axis, distribution, alignment, and spacing. 

#### Main Axis

Main axis is the direction in which your UI elements are either horizontally or vertically aligned.  The “distribution” property sets the value for how the subviews are placed alongside the main axis.  this is similar to justify-content of CSS.

There are a few options for the distribution property:

- equalSpacing
- equalCentering
- fill: doesn’t care about the intrinsic content size. Stretches the one with the lowest content hugging priority first, and then the lowest compression resistance priority. If these values are the same, the indices of the views will determine which one to be stretched.
- fillProportionally
- fillEqually: doesn’t use the intrinsic content size and stretches the element’s size to fill the stack view.

#### Cross Axis

Cross axis is the perpendicular axis to the main axis so in the case of a horizontal main axis, the Y-axis would be the cross axis.  The alignment property is what distribution is to the main axis. This is similar to the align-items in CSS.

The values for the alignment property are:

- fill (default): doesn’t use the intrinsic content size and resizes the elements to fill the stack view perpendicularly to its axis. 
- leading/trailing
- center
- top
- firstBaseline
- bottom
- lastBaseline

### Removing Views

The stack view ensures that the arrangedSubviews array is always a subset of its subviews array.   Therefore, whenever the addArrangedSubview(_: ) method is called, the stack view adds the view as a subview, if it is not already. Whenever an arranged view’s removeFromSuperview() method is called, the stack view removes the view from its arrangedSubview array. ([Source](https://developer.apple.com/documentation/uikit/uistackview/1616232-arrangedsubviews))

This means removeArrangedSubview() still keeps the view in memory, which is helpful for re-adding it later without the cost of recreating it, but removeFromSuperview() has to be called to completely remove the view.




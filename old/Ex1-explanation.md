## BLOCK-readText

### FLEXBOX

There is currently a new specification like `flex` to best layout our pages, other than floats. Flexbox gives us complete control over the alignment, direction, order, and size of our boxes.

In the last chapter, we learned how effectively position elements on a page using `floats` and `inline-block`. For the last decade or so `floats` were the only option to layout the complex layouts. But float was never actually intended for positioning purposes, thus it comes with few pitfalls. And we have discussed all these pitfalls and how to come over it.

To overcome all these limitations `flexbox` invented. Flexbox is one of the most interesting topics of CSS. I am sure while working `flexbox` you will enjoy it.

#### What is flexbox?

Flexbox provides a more efficient way to layout elements. It gives us the ability to align the items and distribute space among the items in a container - even though the size of the elements is unknown or dynamic. With the flexbox, we get the power of flexibility(as the word flex says) to fill the available space. So that elements can easily accommodate according to the size of screens. In a flexbox container, the item expands to fill the free space as well as shrinks to prevent overflow.

#### How does the flexbox model work?

The Flexbox model comes with some sets of properties. Few properties can be applied to parent containers and a few on children items. To make use of those properties and values we need to go into the flexbox zone.

To do so, apply `display: flex` style to an element. Once you do so the element automatically becomes "Flex Container" and children inside are "Flex Item" and we are in the zone of the flexbox model. Now we can use the flexbox properties. Without setting the element's style as `display: flex`, we cannot make use of any flexbox model property.

```
  <div class="container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
  </div>

  * {
    margin: 0;
    padding: 0;
  }
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    font-size: 34px;
    margin: 10px;
  }
```

![Flexbox Concept](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/intro.png)

> #### Terminology:(Flex Container and Flex Items)
>
> While working with flexbox model, there are few basic terminologies that you need to keep in mind.
> For example `flex container` and `flex-item`.
>
> ##### 1. Flex Container
>
> The Parent element where you need to apply `display: flex`.
>
> ##### 2. Flex Items
>
> The children elements inside the flex container.
>
> ![Flexbox Container and Item](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/container-item.png)

In the flexbox model, few properties can be applied to `Flex Container` and few to `Flex Items`. Let's check out what are the properties belong to "Flex Container" and "Flex Items" and discuss them in detail.

#### Understanding the Flex Container properties.

The properties that can be applied to flex containers are:

`display`, `flex-direction`, `flex-wrap`, `flex-flow`, `justify-content`, a`lign-items`, `align-content`.

##### A. Display:

The display property is to activate the flexbox zone. Remember, without setting the `display: flex`, you cannot make use of flexbox properties and values. This is the property from where the real magics get started.

The display property can take two values:

```
  .container {
    display: flex || inline-flex;
  }

```

The display: flex works normally as we have seen earlier.

![Flexbox Concept](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/intro.png)

The `display: inline-flex` is similar to inline-block elements. Applying this value, the element covers the space according to the content it wraps.

![Inline Flex](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/inline-flex.png)

##### B. Flex Direction

Flex direction property determines the direction of the item in which they will lay down. By default when we set the property as `display: flex`, all items line up one after another horizontally. Technically, saying "horizontally" will be wrong here in the flexbox model. Instead, I must say items line up on the main axis. Now here is the time to discuss the two other terminologies i.e. main-axis and cross-axis.

> #### Terminology(main-axis and cross-axis)
>
> Actually, in the flexbox model, there are two axes: `main-axis` and `cross-axis`.
>
> ##### 1. Main Axis
>
> The `main-axis` in the flexbox model is the primary axis along which the items are laid out in the flex container.
> By default, the `main-axis` feels like "horizontal direction", from left to right.
>
> ##### 2. Cross Axis
>
> The cross-axis goes perpendicular to the `main-axis`. It feels like "vertical direction", top to bottom.
>
> ![Flexbox: Main Axis and Cross Axis](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/axis.png)

The important point is that the `main-axis` is not necessary to remain always in the horizontal direction. We can anytime interchange the direction of axes with the `flex-direction` property.

The `flex-direction` property can accept four values:

```
  .container {
    flex-direction: row || column || row-reverse || column-reverse;
  }

```

###### Row(default)

```
  .container {
    flex-direction: row;
  }
```

This is the default value for `flex-direction` property. After applying this property you won't find any changes.

![Flexbox, flex-direction: row](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/row.png)

###### Column

```
  .container {
    flex-direction: column;
  }
```

This value makes all the items in the `flex-container` laid down top to bottom. The `column` value changes the direction of the axes in the flexbox model. The `main-axis` takes the place of `cross-axis` and the cross-axis takes the place of the main-axis.

![Flexbox, flex-direction: column](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/column.png)

###### Row Reverse

```
  .container {
    flex-direction: row-reverse;
  }
```

The `row-reverse` is similar to row but this time all the items will sit from right to left means in the opposite direction.

![Flexbox, flex-direction: row-reverse](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/row-reverse.png)

###### Column Reverse

```
  .container {
    flex-direction: column-reverse;
  }
```

The `column-reverse` is also opposite to the `column` value. The item will lay down from bottom to top.

![Flexbox, flex-direction: column-reverse](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/column-reverse.png)

##### B. Flex Wrap

The `flex-wrap` property determines how the flex-container will accommodate if there are extra flex-items inside it.

Let's take a few more items inside the flex container.

```
  <div class="container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">5</div>
    <div class="item">6</div>
    <div class="item">7</div>
    <div class="item">8</div>
    <div class="item">9</div>
  </div>

  * {
    margin: 0;
    padding: 0;
  }
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    font-size: 34px;
    margin: 10px;
  }
```

![Flexbox, flex-wrap: nowrap](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-nowrap.png)

Yes! exactly this is what happens with the flexbox model if we add extra items in the container. By default, the flex-container will always accommodate all the new items in a single line, even although the browser needs to be scrolled horizontally.

For wrapping the items inside the flex container we have the `flex-wrap` property. The flex-wrap property comes with three different values:

```
  .container {
    flex-wrap: nowrap || wrap || wrap-reverse;
  }
```

###### No wrap(default)

```
  .container {
    flex-wrap: nowrap;
  }
```

The nowrap value is the default value. By default, the container has the nowrap value for the flex-wrap property, whether we apply or not. The container will always accommodate all the items in a single line even although the browser needs to be scrolled horizontally.

###### Wrap

```
  .container {
    flex-wrap: wrap;
  }
```

![Flexbox, flex-wrap: flex-wrap](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-wrap.png)

If the container does not has enough space to accommodate enough items in a single line, then `wrap` value items will automatically break into new lines.

###### Wrap Reverse

```
  .container {
    flex-wrap: wrap-reverse;
  }
```

![Flexbox, flex-wrap: wrap-reverse](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/wrap-reverse.png)

The wrap-reverse is similar to wrap value, but this value wraps the items in the reverse direction.

##### C. Flex flow

The `flex-flow` property is the shorthand property for `flex-direction` and `flex-wrap`. I hope we all know what are shorthand and longhand properties.

```
  .container {
    flex-flow: row wrap;
  }
```

The `flex-flow` property accepts two values at a time, where the first value is for the `flex-direction` and the last value is for `flex-wrap`.

##### D. Justify Content

The `justify-content` property defines how the items will be laid out on the "main-axis". It controls the alignment of the items on the "main-axis". It also helps to make use of extra space leftover in a flex container.

The justify-content property can take 6 different values:

```
  .container {
    justify-content: flex-start || flex-end || center || space-between || space-around || space-evenly;
  }
```

###### Flex Start(default)

```
  .container {
    justify-content: flex-start;
  }
```

![Flexbox, justify-content: flex-start](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/intro.png)

This is the default value of `justify-content` property where all the flex-items will start from the starting point on the "main-axis". As we can see how the flex-items are being laid out from the starting point in a flex-container.

###### Flex End

```
  .container {
    justify-content: flex-end;
  }
```

![Flexbox, justify-content: flex-end](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-end.png)

All the flex-items are laid out towards the endpoint of the "main-axis".

###### Center

```
  .container {
    justify-content: center;
  }
```

The 'center' value for 'justify-content' will center the flex-items along the "main-axis" line.

![Flexbox, justify-content: center](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/center.png)

##### Space Between

```
  .container {
    justify-content: space-between;
  }
```

The extra space in the flex container will be evenly distributed between the flex-items, where the first item in the container will stick to the starting point of the "main-axis" and the last item will stick to the endpoint of the main-axis.

![Flexbox, justify-content: space-between](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/space-between.png)

###### Space Around

```
  .container {
    justify-content: space-around;
  }
```

The extra space in the flex container will be evenly distributed around the flex-items on the "main-axis". Means on the left as well as on the right side of the flex-items there will equal amount of space.

![Flexbox, justify-content: space-around](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/space-around.png)

###### Space Evenly

```
  .container {
    justify-content: space-evenly;
  }
```

The extra space in the flex container will be distributed in such a way that, the space between any two items as well the space of the item from the edge of the container will be equal.

![Flexbox, justify-content: space-evenly](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/space-evenly.png)

##### D. Align Items

The `align-items` property is similar to `justify-content` property. The only difference is that the `align-items` property works on "cross-axis". It defines how the "flex-items" will be laid out on the "cross-axis" inside a "flex container".

The align-items property comes with four values:

```
  .container {
    align-items: stretch || flex-start|| flex-end|| center || baseline;
  }
```

###### Stretch(default)

The stretch value for the align-items property is the default value. All the "flex-items" are stretched on the "cross-axis" to fill the extra space inside a container. By default, you won't see any effect on the items, because right now there is no extra space on the "cross-axis" inside the container. Let's apply some height(let's say 350px) to the container and thereafter see the changes.

```
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
    height: 350px;
  }
```

![Flexbox, align-items: stretch](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/stretch.png)

That's how all the flex-items behave in flexbox on "cross-axis". So without applying `align-items: stretch`, to the container the items are stretched out to fill the space on the "cross-axis".

###### Flex start

```
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
    height: 350px;
    align-items: flex-start;
  }
```

As expected the flex-items will be laid out from the starting point on the "cross-axis".

![Flexbox, align-items: flex-start](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/align-start.png)

###### Flex End

```
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
    height: 350px;
    align-items: flex-end;
  }
```

As expected the flex-items will be laid out towards the endpoint on the "cross-axis".

![Flexbox, align-items: flex-end](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/align-end.png)

###### Center

```
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
    height: 350px;
    align-items: center;
  }
```

The `center` value for `align-items` property will center the flex-items along the "cross-axis" line.

![Flexbox, align-items: center](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/align-center.png)

###### Baseline

```
  <!-- HTML -->
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
    <div class="item item3">3</div>
    <div class="item item4">4</div>
  </div>

  <!-- CSS -->
  .container {
    display: flex;
    background: #FAFFFC;
    border: 5px solid #182945;
    height: 350px;
    aign-items: baseline;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
  }
  .item1 {
    font-size: 34px;
  }
  .item2 {
    font-size: 20px;
  }
  .item3 {
    font-size: 48px;
  }
  .item4 {
    font-size: 72px;
  }
```

![Flexbox, align-items: baseline](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/baseline.png)

The `baseline` value aligns the items based on the baseline of the text. Check out the image above for understanding.

> ###### To be not confused, always remember, "justify" works along the `main-axis` and "align" works along the `cross-axis`.

##### D. Align Content

The align-content property is similar to both `justify-content` and align-items` property.

The difference is that the `justify-content` and `align-items` property works on the individual items but the `align-content` property works on the multi-line flex container. The `align-content` property aligns flex container's lines when there is extra space on the cross-axis.

If all the "flex-items" are on a single line in a container then this property does not affect.

The align-content property accepts 6 different values:

```
  .container {
    align-content: stretch || flex-start || flex-end || center || space-between || space-around;
  }
```

Let's add a few more flex items so that we have a multi-line flex-container. Remember this property does not affect single line flex-container.

```
  <div class="container">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
    <div class="item">5</div>
    <div class="item">6</div>
    <div class="item">7</div>
    <div class="item">8</div>
    <div class="item">9</div>
  </div>

  .container {
    display: flex;
    flex-wrap: wrap;
    background: #FAFFFC;
    border: 5px solid #182945;
    height: 350px;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
  }
```

###### Stretch(default)

```
  .container {
    display: flex;
    flex-wrap: wrap;
    align-content: stretch;
  }
```

The `stretch is the default value for the`align-content` property. All the items are stretched to take up the remaining space on the "cross-axis".

![Flexbox, align-content: stretch](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/content-stretch.png)

###### Flex Start

```
  .container {
    display: flex;
    flex-wrap: wrap;
    align-content: flex-start;
  }
```

All the items in a multi-line flex container will be aligned from the starting point on the "cross-axis".

![Flexbox, align-content: flex-start](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/content-start.png)

###### Flex End

```
  .container {
    display: flex;
    flex-wrap: wrap;
    align-content: flex-end;
  }
```

All the items in a multi-line flex-container will be aligned towards the endpoint on the "cross-axis".

![Flexbox, align-content: flex-end](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/content-end.png)

###### Center

```
  .container {
    display: flex;
    flex-wrap: wrap;
    align-content: center;
  }
```

Items are laid out to the `center` of the multi-line flex-container on the "cross-axis".

![Flexbox, align-content: center](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/content-center.png)

###### Space Between

```
  .container {
    display: flex;
    flex-wrap: wrap;
    align-content: space-between;
  }
```

The spaces are evenly distributed between the flex-items on the "cross-axis" as `justify-content: space-between` property works on the "main-axis".

![Flexbox, align-content: space-between](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/content-between.png)

###### Space Around

```
  .container {
    display: flex;
    flex-wrap: wrap;
    align-content: space-around;
  }
```

The spaces are evenly distributed around the flex-items on the "cross-axis" as `justify-content: space-around` property works on the "main-axis".

![Flexbox, align-content: space-around](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/content-around.png)

## BLOCK-writeTextAnswer

1. How does the flexbox model work?
2. Which is the important property to use all the flexbox properties and values?
3. What's the difference between a flexbox container and a flex item?
4. What are flex container properties?
5. What's the difference between flex and inline-flex values?
6. Which property is used to change the direction of the axis in the flexbox?
7. If the items are overflowing the container then which property should be used to so item automatically starts from the new line?
8. How can we center(horizontally as well as vertically) any item inside an element?

## BLOCK-writeCode
1. Create a simple page having a header, main content, and a footer.

2. Inside the header keep the brand name to the left and all the navigation to the right.

4. Inside the main content take an article section having two columns. In the first column put a heading and some introductory text of the article and in the second column take an image.

5. After the article section, take a gallery section, in which there will be two rows and in both the row there will be three columns. Each column must have a different image.

6. After the gallery section footer will come.

7. Use flexbox properties and values to create columns.

#### Understanding the Flex Item properties.

In the last section, we have seen all the properties and values for the flex-container. We saw how we can align the items on the "main-axis" or "cross-axis" and how to utilize the extra space inside a flex-container. Like flex-container, there are few properties that we can apply on flex-items.

The properties that can be applied to flex-items are:

`order`, `flex-grow`, `flex-shrink`, `flex-basis`, `flex`, `align-self`.

##### A. Order

The `order` property is used to reorder the flex-item within a flex-container without changing the source code in an HTML document. By default, we know that the elements are laid out according to the order in which it is written in the HTML document.

However, we can reorder the place of items on a page with `order` property in the flexbox. For example, let's say we want our first item at the end.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
    <div class="item item3">3</div>
    <div class="item item4">4</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
  }
  .item1 {
    order: 1;
  }
```

![Flexbox Order Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/order1.png)

The item-1 will at the end because of its order `1`. By default, every item has `0` value for the `order` property. The property accepts unitless value in number, it can be negative or positive. The items are reordered according to the values applied to the order property, from lowest to highest. If the order value for the items is the same then the items are laid out according to the order appeared in HTML source code.

Let's see another example where we will reorder the 4th item at the first position and 1st item at the last.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
    <div class="item item3">3</div>
    <div class="item item4">4</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
  }
  .item1 {
    order: 1;
  }
  .item4 {
    order: -1;
  }
```

![Flexbox Order Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/order2.png)

##### B. Flex Grow

The flex-grow property allows the items to grow if there is extra space inside the flex container. The property accepts unitless value in number which provides the ability to grow to the items.

By default, the value for the flex-grow property is `0`, which means the size of the item will be auto. It may accept any value but not negative. If we want the item to grow and fill the extra space inside the container, we will have to apply `flex-grow` property and set the value greater than `0`. Let's check out the property visually.

Suppose we have two items inside a flex-container and we want the items to grow in the same proportionality. Then we can set the value 1 for `flex-grow` property for the items.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;padding: 40px 50px;
    margin: 10px;
    flex-grow: 1;
  }
```

![Flex Grow Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-grow1.png)

If all the items have `flex-grow` set to `1` the extra space will be distributed equally to all the items.

If one of the items has a value of 2, the remaining space would take up twice as much space as the others.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
  }
  .item1 {
    flex-grow: 2;
  }
  .item2 {
    flex-grow: 1;
  }
```

![Flex Grow Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-grow2.png)

##### C. Flex Shrink

The `flex-shrink` property is opposite to the `flex-grow` property. It allows the items to shrink if there is no extra space in the container. For the practical view, just reduce the size of your screens. You will find the width of the items is also reducing as the size of screens is reducing.

By default, the value for `flex-shrink` property is 1. Similar to `flex-grow` property the `flex-shrink` property also accepts a unitless value but greater than `0`. Negative values are invalid.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
    flex-basis: 300px;
    flex-shrink: 1;
  }
```

Here, 1 is the default value for the `flex-shrink` property that we have applied, so the item's size will reduce as per the size of the screens. For a better understanding of `flex-shrink` property, I have also applied `flex-basis` property. The `flex-basis` property is to set the initial size of the item before the item will grow or shrink in a flex-container according to the extra space, that we will see in the next section.

![Flex Shrink Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-shrink1.png)

This is what we will see after applying `flex-shrink: 1` and `flex-basis: 300px`. Now if you will reduce the size of your screen, the item size will also reduce.

![Flex Shrink Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-shrink2.png)

However, if we set `0` value for the `flex-shrink` property the item size won't reduce as per the size of the screens. The item will overflow in the flex container.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
    flex-basis: 300px;
    flex-shrink: 0;
  }
```

![Flex Shrink Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-shrink3.png)

##### D. Flex Basis

We got a bit introduction of `flex-basis` property in the last section. The `flex-basis` property is somewhat similar to the width property, as it accepts the values(in px, %, em, rem, etc.) similar to the width property. The `flex-basis` property is applied to set a base width or size of the flex-item from where the item will grow or shrink if necessary.

By default, the value for flex-basis property is auto, which means the base size of the item will be computed based on the content inside it plus whatever the padding we will apply to the item.

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
  </div>

  .container {
    display: flex;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
    flex-basis: 200px;
  }
```

![Flex Basis Property](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/flex-basis.png)

##### Flex

The `flex` property is the shorthand property for the `flex-grow`, `flex-shrink`, and `flex-basis`.

```
  .item {
    flex: 0 1 auto;
  }
```

This is the default value for the `flex` property where the first value is for `flex-grow`, second is for `flex-shrink` and the last value is for `flex-basis`. The last two value for flex property is optional.

```
  .item {
    flex:  1;
  }
```

Here, 1 is the value for the flex-grow property, and the values for `flex-shrink` and `flex-basis` will be automatically set to the default.

It's better to go with the `flex` shorthand property, instead of applying `flex-grow`, `flex-shrink`, and `flex-basis` individually.

##### F. Align Self

The `align-self` property is exactly similar to align-items property. It accepts all the same values as the `align-items` accepts. The only difference is that the `align-self` property is applied to the flex-items but the `align-items` property is applied to the flex container.

```
  .container {
    align-self: auto || stretch || flex-start || flex-end || center || baseline;
  }
```

Also, we all know from the above discussion that "align" always works on the "cross-axis", therefore we must have some extra space on the "cross-axis".

```
  <div class="container">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
    <div class="item item3">2</div>
  </div>

  .container {
    display: flex;
    height: 350px;
    align-items: flex-start;
  }
  .item {
    background: #9EDDEB;
    padding: 40px 50px;
    margin: 10px;
  }
```

###### Auto

The `auto` value for `align-self` property inherits, whatever the value is set for `align-items` in the flex-container. If it is `flex-star`, the `align-self` value will be also `flex-start`.

```
  .item3 {
    align-self: auto;
  }
```

![Flexbox, align-self: auto](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/item-start.png)

###### Stretch

The `stretch` property is to stretch out the size of individual items on the "cross-axis" to fill the extra space.

```
  .item3 {
    align-self: stretch;
  }
```

![Flexbox, align-self: stretch](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/item-stretch.png)

###### Flex Start

The item will be aligned from the starting point on the "cross-axis".

```
  .item3 {
    align-self: flex-start;
  }
```

![Flexbox, align-self: flex-start](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/item-start.png)

###### Flex End

The item will be aligned towards the endpoint on the "cross-axis".

```
  .item3 {
    align-self: flex-end;
  }
```

![Flexbox, align-self: flex-start](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/item-end.png)

###### Center

The item will be aligned at the center on the "cross-axis".

```
  .item3 {
    align-self: center;
  }
```

![Flexbox, align-self: center](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/item-center.png)

###### Baseline

We have already seen baseline value for align-items property for the "flex-container". The baseline value for `align-self` property also works in the same way.

```
  .item3 {
    align-self: baseline;
  }
```

![Flexbox, align-self: baseline](https://raw.githubusercontent.com/suraj122/AC-STYLE-images/master/flexbox/item-baseline.png)

> Note: float, clear, and vertical-align do not affect a flex item.

## BLOCK-writeTextAnswer

1. What is a different property that can be applied to flex items?

2. Flex is the shorthand property of?

3. What's the difference between `flex-grow` and `flex-shrink`?

4. What is the default value for `flex-grow` and `flex-shrink`?

5. What's the purpose of `flex-basis` property? And how it is different from width property?
---
layout: post
title: "React Native's SectionList and getItemLayout"
tags: compsci
---
<img style="max-width: 75%; float: left; box-shadow: none; border: none;" src="{{ '/images/section-list.png' | relative_url}}">

React Native's old ListView was superseded by the new FlatList and SectionList in version 0.43 last year. These lists take a `getItemLayout` prop that it uses to calculate dimensions for the things on your list. As you quickly find out as you start using these new list classes, this prop is vitally important if you want a half-way decent user experience. This is because (a) React Native won't know the total length of your list otherwise which means as it loads additional content, the scroll bar jumps around and more importantly (b) if your rows render too slowly to keep up with the user scrolling, the scroll gets blocked. If you provide this prop, the user sees blank rows that appear as they finish rendering. While still not ideal, this makes for a much better haptic experience as user interaction doesn't get abruptly interrupted.
<!--break-->

For both FlatList and SectionList, `getItemLayout` expects to be given two parameters: a `data` array which is the same data array you pass to the list element itself and `index`, the index of the row you should calculate dimensions for. Its return value is an object with three properties: `offset`, the distance from the top of the first element, `length`, the height of your row and `index` which is simple the `index` parameter passed into the function.

For FlatList, this function is fairly easy to write. For lists that contain rows of uniform height, you simply return `{offset: ROW_HEIGHT * index, length: ROW_HEIGHT, index}`. Separators or rows of differing height can make this slightly more complicated, but it's still pretty clear what you are supposed to calculate.

For SectionList, however, it's far less clear what `getItemLayout` should return. According to my experiments and [the react-native source code](https://github.com/facebook/react-native/blob/master/Libraries/Lists/VirtualizedSectionList.js#L132), all section headers, section footers and proper rows get flattened into one list. The `index` parameter refers to an element in that list.

Figuring out how to calculate this took me an afternoon and since this will be useful to pretty much everyone who uses SectionList, I extracted it into its own package available on [npm](https://www.npmjs.com/package/react-native-section-list-get-item-layout) and [github](https://github.com/jsoendermann/rn-section-list-get-item-layout). You use it like this:

<script src="https://gist.github.com/jsoendermann/fd1155366069250bcb5a12531647757f.js"></script>
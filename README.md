# react-swipe

[Brad Birdsall](https://github.com/thebird)'s [Swipe.js](http://swipejs.com), as a [React](http://facebook.github.io/react) component.

Check out the [demo](https://jed.github.io/react-swipe/demo) from a mobile device (real or emulated).

## Installation

```bash
npm install react-swipe
```

## Module and React Versions

- `2.0.x` - depends on React `0.12.x`
- `2.1.x` - depends on React `0.13.x`
- `3.0.x` - depends on React and ReactDOM `0.14.x`

## Usage

```javascript
var React = require('react')
var ReactSwipe = require('react-swipe')

var Carousel = React.createClass({
    render: function () {
        return (
            <ReactSwipe
                continuous={false}
            >
                <div>'PANE 1'</div>
                <div>'PANE 2'</div>
                <div>'PANE 3'</div>
            </ReactSwipe>
        );
    }
});

React.render(<Carousel />, document.body)
```

## Props

Properties are duplicates of options from [Swipe.js config](https://github.com/thebird/Swipe#config-options) but there are additional ones:

- **slideToIndex** Integer - set index position by Swipe's `.slide()` method on `componentDidUpdate` lifecycle method. It's useful when you need to control `ReactSwipe` by custom next/prev buttons - just update component with new index (it wont be updated if index number is the same as previous one).

- **shouldUpdate** Function, _arguments: nextProps {Object}_ - by default `<ReactSwipe />` component will rerender itself and children **only** if `slideToIndex` [property has changed](https://github.com/jed/react-swipe/blob/gh-pages/react-swipe.js#L65). But `shouldUpdate` prop allows to define a function and control rerendering of children on your own. 

## Re-rendering

See [related issue](https://github.com/jed/react-swipe/issues/23).

In order for `react-swipe` to know that it needs to be re-rendered, you should supply the `key` property to the component. By setting the `key` to the `length` of the images that you pass into `react-swipe`, re-rendering will take place when the `images.length` differs from the previous `render` pass:

```javascript
<ReactSwipe key={images.length}>
{images}
</ReactSwipe>
```

---

**MIT Licensed**

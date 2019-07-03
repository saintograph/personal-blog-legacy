---
layout: post
title:  "Consistent layouts for React Native views."
date:   2019-05-17 08:00:00 +0800
categories: [javascript, react]
---

Reference: [https://facebook.github.io/react-native/docs/view#onlayout](https://facebook.github.io/react-native/docs/view#onlayout)

**Warning** : Use `onLayout` to manage the display of UI elements _within_ a view, not the view itself.

`onLayout` immediately fires after the layout has been calculated, which will result in odd behaviour which the user might notice.

Example:

**Do this**

```jsx
class Example extends Component {
  state = {
    renderLayout: false,
  }

  render() {
    const { renderLayout } = this.state;
    return (
      <View
        onLayout={() => this.setState({ renderLayout: true })}
      >
        {renderLayout ? 
          <Text>Lorem Ipsum.</Text>
          :
          <ActivityIndicator color="#000000" size="large">
        }
      </View>
    )
  }
}
```


**Not this**


```jsx
class Example extends Component {
  state = {
    containerWidth: '80%',
  }
  
  render() {
    const { containerWidth } = this.state;
    return (
      <View
        onLayout={() => this.setState({ containerWidth: '80%' })}
      >
        <View
          style={ { width: containerWidth} }
        >
          <Text>Odd janky behavior.</Text>
        </View>
      </View>
    )
  }
}
```
# vue-from-react-transition-guide
A transition guide to vue for react developers

## Passing Props

### React
```js
// static
<ComponentName prop="ok" />

// dynamic
<ComponentName prop={post.title} />

// number
<ComponentName prop={42} />

// boolean true
<ComponentName prop />

// boolean false
<ComponentName prop={false} />

// array
<ComponentName prop={[1, 2, 3]} />

// object
<ComponentName prop={{ 1: 1, 2: 2, 3: 3 }} />

// rest
<ComponentName {...rest} />
```

### Vue
```js
// static
<component-name prop="ok"></component-name>

// dynamic
<component-name :prop="post.title"></component-name>

// number
<component-name :prop="42"></component-name>

// boolean true
<component-name prop></component-name>

// boolean false
<component-name :prop="false"></component-name>

// array
<component-name :prop="[1, 2, 3]"></component-name>

// object
<component-name :prop="{ 1: 1, 2: 2, 3: 3 }"></component-name>

// rest
<component-name v-bind="rest"></component-name>
```

## Prop-Types

### React
```js
import React from 'react'
import PropTypes from 'prop-types'

class ComponentName extends React.Component {
  static propTypes = {
    propA: PropTypes.number,
    propB: PropTypes.oneOfType([PropTypes.string, PropTypes.number])
    propC: PropTypes.string.isRequired,
    propD: PropTypes.number,
    propE: PropTypes.object,
    propF: PropTypes.oneOf(['success', 'warning', 'danger']).isRequired,
  }

  static defaultProps = {
    propA: undefined,
    propB: undefined,
    propD: 100,
    propE: { message: 'hello' },
  }
}
```

### Vue
```js
Vue.component('my-component', {
  props: {
    // Basic type check (`null` matches any type)
    propA: Number,
    // Multiple possible types
    propB: [String, Number],
    // Required string
    propC: {
      type: String,
      required: true
    },
    // Number with a default value
    propD: {
      type: Number,
      default: 100
    },
    // Object with a default value
    propE: {
      type: Object,
      // Object or array defaults must be returned from
      // a factory function
      default: function () {
        return { message: 'hello' }
      }
    },
    // Custom validator function
    propF: {
      validator: function (value) {
        // The value must match one of these strings
        return ['success', 'warning', 'danger'].indexOf(value) !== -1
      }
    }
  }
})
```

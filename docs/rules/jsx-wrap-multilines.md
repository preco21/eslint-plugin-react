# Prevent missing parentheses around multiline JSX (react/jsx-wrap-multilines)

Wrapping multiline JSX in parentheses can improve readability and/or convenience. It optionally takes a second parameter in the form of an object, containing places to apply the rule. By default, `"declaration"`, `"assignment"`, `"return"`, and `"arrow"` syntax is checked, but these can be explicitly disabled. Any syntax type missing in the object will follow the default behavior (become enabled).

**Fixable:** This rule is automatically fixable using the `--fix` flag on the command line.

## Rule Details

The following patterns are considered warnings:

```jsx
var Hello = createReactClass({
  render: function() {
    return <div>
      <p>Hello {this.props.name}</p>
    </div>;
  }
});
```

The following patterns are not considered warnings:

```jsx
var singleLineJSX = <p>Hello</p>

var Hello = createReactClass({
  render: function() {
    return (
      <div>
        <p>Hello {this.props.name}</p>
      </div>
    );
  }
});

// When [1, {declaration: false}]
var hello;
hello = <div>
  <p>Hello</p>
</div>

// When [1, {declaration: true, assignment: false, return: true}]
var world = <div>
  <p>World</p>
</div>

// When [1, {arrow: false}]
var hello = () => <div>
  <p>World</p>
</div>
```

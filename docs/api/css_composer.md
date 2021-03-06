<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

## CssComposer

This module contains and manage CSS rules for the template inside the canvas.
You can customize the initial state of the module from the editor initialization, by passing the following [Configuration Object][1]

```js
const editor = grapesjs.init({
 cssComposer: {
   // options
 }
})
```

Once the editor is instantiated you can use its API. Before using these methods you should get the module from the instance

```js
const cssComposer = editor.CssComposer;
```

-   [load][2]
-   [store][3]
-   [add][4]
-   [get][5]
-   [getAll][6]
-   [clear][7]
-   [setRule][8]
-   [getRule][9]

## load

Load data from the passed object, if the object is empty will try to fetch them
autonomously from the storage manager.
The fetched data will be added to the collection

### Parameters

-   `data` **[Object][10]** Object of data to load

Returns **[Object][10]** Loaded rules

## store

Store data to the selected storage

### Parameters

-   `noStore` **[Boolean][11]** If true, won't store

Returns **[Object][10]** Data to store

## add

Add new rule to the collection, if not yet exists with the same selectors

### Parameters

-   `selectors` **[Array][12]&lt;Selector>** Array of selectors
-   `state` **[String][13]** Css rule state
-   `width` **[String][13]** For which device this style is oriented
-   `opts` **[Object][10]** Options for the add of new rule (optional, default `{}`)
-   `addOpts`   (optional, default `{}`)
-   `props` **[Object][10]** Other props for the rule

### Examples

```javascript
var sm = editor.SelectorManager;
var sel1 = sm.add('myClass1');
var sel2 = sm.add('myClass2');
var rule = cssComposer.add([sel1, sel2], 'hover');
rule.set('style', {
  width: '100px',
  color: '#fff',
});
```

Returns **Model** 

## get

Get the rule

### Parameters

-   `selectors` **[Array][12]&lt;Selector>** Array of selectors
-   `state` **[String][13]** Css rule state
-   `width` **[String][13]** For which device this style is oriented
-   `ruleProps` **[Object][10]** Other rule props

### Examples

```javascript
var sm = editor.SelectorManager;
var sel1 = sm.add('myClass1');
var sel2 = sm.add('myClass2');
var rule = cssComposer.get([sel1, sel2], 'hover');
// Update the style
rule.set('style', {
  width: '300px',
  color: '#000',
});
```

Returns **(Model | null)** 

## getAll

Get the collection of rules

Returns **Collection** 

## clear

Remove all rules

Returns **this** 

## setRule

Add/update the CSS rule with a generic selector

### Parameters

-   `selectors` **[string][13]** Selector, eg. '.myclass'
-   `style` **[Object][10]** Style properties and values
-   `opts` **[Object][10]** Additional properties (optional, default `{}`)
    -   `opts.atRuleType` **[String][13]** At-rule type, eg. 'media' (optional, default `''`)
    -   `opts.atRuleParams` **[String][13]** At-rule parameters, eg. '(min-width: 500px)' (optional, default `''`)

### Examples

```javascript
// Simple class-based rule
const rule = cc.setRule('.class1.class2', { color: 'red' });
console.log(rule.toCSS()) // output: .class1.class2 { color: red }
// With state and other mixed selector
const rule = cc.setRule('.class1.class2:hover, div#myid', { color: 'red' });
// output: .class1.class2:hover, div#myid { color: red }
// With media
const rule = cc.setRule('.class1:hover', { color: 'red' }, {
 atRuleType: 'media',
 atRuleParams: '(min-width: 500px)',
});
// output: @media (min-width: 500px) { .class1:hover { color: red } }
```

Returns **CssRule** The new/updated rule

## getRule

Get the CSS rule by a generic selector

### Parameters

-   `selectors` **[string][13]** Selector, eg. '.myclass:hover'
-   `opts`   (optional, default `{}`)

### Examples

```javascript
const rule = cc.getRule('.myclass1:hover');
const rule2 = cc.getRule('.myclass1:hover, div#myid');
const rule3 = cc.getRule('.myclass1', {
 atRuleType: 'media',
 atRuleParams: '(min-width: 500px)',
});
```

Returns **CssRule** 

## getRules

Find rules, in different states (eg. like `:hover`) and media queries, matching the selector.

### Parameters

-   `selector` **[string][13]** Selector, eg. '.myclass'

### Examples

```javascript
// Common scenario, take all the component specific rules
const id = someComponent.getId();
const rules = cc.getRules(`#${id}`);
console.log(rules.map(rule => rule.toCSS()))
```

Returns **[Array][12]&lt;CssRule>** 

[1]: https://github.com/artf/grapesjs/blob/master/src/css_composer/config/config.js

[2]: #load

[3]: #store

[4]: #add

[5]: #get

[6]: #getall

[7]: #clear

[8]: #setrule

[9]: #getrule

[10]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object

[11]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Boolean

[12]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array

[13]: https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String

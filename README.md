# browser-app
React-based template for a single page app with search/content/actions

## Dependencies
* React
* Jquery (not in package.json)

## Props
`searchPath` should be a url which returns JSON. The search term will be passed as the `f` query parameter. The JSON object should have these keys:
  * `results`: an array of matching items. Each item should have these keys:
     * `id` -- must be unique among all items
     * `html` -- the html which will render this item in the search results
     
  Optionally, the item can have a `url` key. If so, when the search result is clicked, the viewport will load content from this url.

`searchPlaceholder` is optional, and can be a string to use as placeholder text in the search box

## CSS
You should include `browser-app.css` on your page at a minimum. This styles the app in a 2-column format with search results on the left and content on the right.

If the viewport region (children of the `BrowserApp` element, or html loaded from search results) contains a div with the class `browser-app-actions`, children of this div with the class `browser-app-action` will be fixed to the top right of the page in a menu. See the example below for how this works.

## Example
```javascript
<BrowserApp searchPath="/search.json" searchPlaceholder="Search for stuff">
  <h2>This area is the "viewport"</h2>
  <p>Initial content goes here.</p>

  <div className="browser-app-actions">
    <div className="browser-app-action">
      <a href="#"><i className="fa fa-save" /></a>
    </div>

    <div className="browser-app-action">
      <a href="#"><i className="fa fa-remove" /></a>
    </div>

    <hr />

    <div className="browser-app-action">
      <a href="#"><i className="fa fa-home" /></a>
    </div>
  </div>
</BrowserApp>
```

This will create an app which looks something like this (sidebar results have also been added):

<img width="1276" alt="screen shot 2016-08-26 at 12 16 53 pm" src="https://cloud.githubusercontent.com/assets/6469642/18017611/2a0838ce-6b87-11e6-8cb4-c7a1c32e6ab7.png">

## Copyright

Copyright (c) 2016 Peter Woo, released under the MIT license

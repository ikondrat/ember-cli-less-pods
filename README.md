# ember-cli-less-pods

Styling your pods with the less style file in the pod directory.
Based on [ember-cli-sass-pods](https://github.com/justtal/ember-cli-sass-pods) implementation
 
## Installation

```
ember install ember-cli-less-pods 
```


## Example of usage ember-cli-less-pods
Say you have a contacts route and contact-box component.

##### Generate regular route and component:
```
ember g route contacts -p
ember g component contact-box -p
```
##### Then, use ember-cli-less-pods power and generate styles:
```
ember g less contacts -p
ember g less components/contact-box -p
```

##### Your file structure would be:
```
app/

app/contacts
app/contacts/route.js
app/contacts/template.hbs
app/contacts/style.less

app/components/
app/components/contact-box
app/components/contact-box/component.js
app/components/contact-box/template.hbs
app/components/contact-box/style.less

app/styles/
app/styles/app.less
app/styles/[importFileName].less
```
##### app/styles/[importFileName].less
```
@import "contacts/style";
@import "components/contact-box/style";
```

## Installation

##### Install ember-cli-less-pods

* `ember install ember-cli-less-pods`

It will automatically install [ember-cli-less](https://github.com/aexmachina/ember-cli-less#ember-cli-less) less preprocess package.

##### The import file
You need to add the import file into your main app less file.

If you use podModulePrefix your imports file would be:
```
pods/[podModulePrefix].less
```
otherwise it would be:
```
pods/pods.less
```
Add import line into your main app less file:

```
@import "pods/[podModulePrefix] or pods/index";
```

## Usage

To generate styles into your pod - just run:

```
ember g style [path] -p
```

## Live reload
You may setup live reload with `onchange` npm package 
```
npm install --save onchange
```
Here is example of setup for live reload with `onchange` 

package.json
```
"scripts": {
  ...
  "prestart": "npm run watch",
  "watch": "pkill -f myapp/node_modules/.bin/onchange; mkdir -p app/styles/pods/; touch app/styles/pods/pods.less; onchange app/pods/**/*.less -- touch app/styles/pods/pods.less &> watch.log &"
  ...
```
.watchmanconfig
```
{
  "ignore_dirs": ["tmp", "dist", "app/styles/pods"]
}
```

Enjoy styling

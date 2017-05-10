# ember-cli-less-pods

Styling your pods with the less style file in the pod directory.
Based on [ember-cli-sass-pods](https://github.com/justtal/ember-cli-sass-pods) implementation
 
## Installation

```
ember install ember-cli-sass-pods 
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
[podModulePrefix].less
```
otherwise it would be:
```
pods.less
```
Add import line into your main app less file:

```
@import "[podModulePrefix] or pods";
```

##### Watched folder
Add paths for watching in the 'ember.cli-build.js' (for Ember 2+ ember-cli-build.js):
```
var app = new EmberApp(defaults, {
  lessOptions: {
    includePaths: ['app']
  }
});
```

## Usage

To generate styles into your pod - just run:

```
ember g style [path] -p
```

Enjoy styling

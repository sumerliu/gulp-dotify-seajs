# gulp-dotify-seajs

[Gulp](https://github.com/gulpjs/gulp) plugin for precompilation of [doT](https://github.com/olado/doT) templates for seajs.

## Example

If we have following folder structure:

```
app/views/users/list.html
app/views/users/detail.html
app/views/products/list.html
app/views/products/detail.html
app/views/layout.html
```

Then, running this code:

```js
gulp.task('templates', function() {
	gulp.src('app/views/**/*.html')
	.pipe(dotify())
	.pipe(concat('templates.js'))
	.pipe(header('window.JST = {};'))
	.pipe(gulp.dest('public/js'));
});
```

Will produce `public/js/templates.js`:

```js
window.JST = {};
JST['users-list'] = function ...
JST['users-detail'] = function ...
...
JST['layout'] = function ...
```

## Options

* root -- root folder, where templates are located (affects template name generation), `views` by default
* extension -- file extension of template files, `.html` by default
* separator -- template namespace-name separator, `-` by default
* dictionary -- template dictionary name, `JST` by default

## License

MIT

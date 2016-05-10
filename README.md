# gulp-language-tool

## Usage

```javascript
var gulp = require('gulp');
var lt = require('gulp-language-tool');

gulp.task('default', function() {
	gulp.src('/posts/*{.md}')
		.pipe(lt());
});
```

### Configuration

`gulp-language-tool` accepts an optional object of configuration, it has the following configuration:

- **interface** - The URL of Language Tool

### Language Tool

It is highly recommended that you run your own local Language Tool instance, as the public API is rate limited. For instructions see [https://languagetool.org/](https://languagetool.org/) or:

```
$ wget https://languagetool.org/download/LanguageTool-3.3.zip
$ unzip LanguageTool-3.3.zip
$ cd LanguageTool-3.3/
$ java -cp languagetool-server.jar org.languagetool.server.HTTPServer --port 8081
```

You can then specify you local instance as an interface:

```javascript
gulp.task('default', function() {
	gulp.src('/posts/*{.md}')
		.pipe(lt({ interface: 'http://localhost:8081' }));
});
```
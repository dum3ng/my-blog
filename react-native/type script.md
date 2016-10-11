##Install
Need to install latest typescript globally and react-native-tools extension in vscode

---

##workflow
After the installation and configuration eslint and typescipt, we will add the build task
    
    npm install gulp gulp-typescript concurrently
Create gulpfile.js:
    
    var gulp = require('gulp');
    var ts = require('gulp-typescript');
    
    // Grab settings from tsconfig.json
    var tsProject = ts.createProject('tsconfig.json');
    
    gulp.task('build', function() {
        var tsResult = tsProject.src().pipe(ts(tsProject));
        return tsResult.js.pipe(gulp.dest('built'));
    });
    
    gulp.task('watch', ['build'], function() {
        gulp.watch('*.tsx', ['build']);
    });
    
    gulp.task('default', ['build']);
    
This will create some task to execute.
Then in the package.json, add some scripts:
    
    "build": "gulp build",
    "watch": "gulp watch",
    "start": "concurrently \"npm run watch\" \"node node_modules/react-native/local-cli/cli.js start\" "
Then run 
    
    $ npm start
When you changed some file and saved, the typescript transpile and watchman will work concurrently. If you enabled the hot loading, just edit you .tsx file and save. See the change.

>workflow note:
>Since the typescript compiler will compile the jsx extension to .jsx if you specify the 'jsx' option to 'preserve', and react native will not recognize the .jsx file, you may need another task in gulp to rename the .jsx file to .js:
    
    var rename = require('gulp-rename')
  
     gulp.task('build', function() {
        var tsResult = tsProject.src().pipe(ts(tsProject));
        return tsResult.js.pipe(rename({extname:'.js'})).pipe(gulp.dest('built')) 
    });

---
##Tips
 - To use jsx you need add jsx configuration in tsconfig.json
    
        "compilerOptions":{
            //...other options
            "jsx":"preserve"
        }
 - To import the *React* module from 'react', you need write like:
        
        import * as React from 'react'
    since the typedefination file does 
    
        export = React
    There is no defalut export

 - To clear the 'import is a reserver keyword' error, you need add:
    
        "allowSyntheticDefaultImports": true
    in tsconfig file.
 - To create a react-native component, you need write like this:
    
        interface Props {}
        interface State {}
        class MyComponent extends Component<Props,State>{

        }
    Then add all props and state in the interface.
    See more in the *react.d.ts* file.
    
 - typings 
        
        $ typings install -G dt~react-native
the dt is source name. And you need install it globally by using -G. That will create a global folder under typings folder.

    












    
    
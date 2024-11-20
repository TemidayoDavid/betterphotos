poppins for playful projects

USING SASS

```
npm i sass
change the script in package.json to 

```
"compile": "sass --watch --no-source-map main.scss style.css"

```

where: sass is the package
--watch tells sass to watch for changes in the scss file and compile 
automatically to css
--no-source-map tells the system not to add the styles.css.map file (the file isn't harmful and can be used to track bugs)
main.scss, states the file we want sass to compile from
style.css, states the file we want sass to compile to

```

npm run compile 

Don't forget to add a "src" folder
with a
build folder

you need to update the scripts in package.json
src/main.scss               src/style.css

Packages that would help optimize app

--- csso is a minifier and would remove redundant code that was added during development. 
--- postcss helps to our css to be manipulated. 
--- the plugin autoprefixer would ride on the manipulation of postcss to add vendor prefixes like moz and webkit necessary for some styling to work on older devices.

ENSURE YOU INSTALL THE CLI VERSION OF CSSO

```
npm install csso-cli

```
for POSTCSS

```
npm install postcss postcss-cli

```
for AUTOPREFIXER

```
npm install autoprefixer

```
or

```
npm install csso-cli postcss postcss-cli autoprefixer

```

build:compile (script in package.json)

this will take the sass file and output a css file

ADDITIONAL SCRIPTS TO COMPILE, PREFIX AND OPTIMIZE CODE (write inside package.json)

```
 "build:compile": "sass --no-source-map src/main.scss build/compiled.css",
 "build:prefixes": "postcss build/compiled.css --use autoprefixer --output build/prefixed.css",
 "build:optimize": "csso build/prefixed.css --output build/style.css"

```

THEN NPM RUN

```
npm run build:compile
npm-run build:prefixes
npm run build:optimize

```

//100% is about 16px if the default option is not changed to something else
//normally 1rem = 16px font size

YOU CAN USE THE REM UNIT EVERYWHERE IN YOUR PROJECT


SINCE THE DECIMALS CAN BE TOO MUCH, INSTEAD OF USING 100% IN THE ROOT
```
html{
    font-size: 100%;   
}
```

WE USE

62.5% OF 16px = 10px, so 1rem = 10px

```
html{
    font-size: 62.5%
}

```

This means i would simply divide px value by 10. if i have 1240px somewhere, the rem equivalent would be 1240/10 = 124.0rem


THE ONLY PLACE WHERE YOU DON'T USE REM UNIT IS IN THE MEDIA QUERY BREAK POINT, INSTEAD USE 'em'
(rem has a bug in safari)

@media (max-width: 1300px){ // 1rem = 1rem = browser font size (usually 16px)

}
----------------------------------------
INSTEAD OF THE PX ABOVE YOU CAN WRITE :----->

@media (max-width: 81.25em){  // 1300px / 16px = 81.25em

}
----------------------------------------
# npmdoc-hls.js

#### api documentation for  [hls.js (v0.7.5)](https://github.com/video-dev/hls.js)  [![npm package](https://img.shields.io/npm/v/npmdoc-hls.js.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-hls.js) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-hls.js.svg)](https://travis-ci.org/npmdoc/node-npmdoc-hls.js)

#### JavaScript HLS client using MediaSourceExtension

[![NPM](https://nodei.co/npm/hls.js.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/hls.js)

- [https://npmdoc.github.io/node-npmdoc-hls.js/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-hls.js/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-hls.js/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-hls.js/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-hls.js/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-hls.js/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "name": "hls.js",
    "version": "0.7.5",
    "license": "Apache-2.0",
    "description": "JavaScript HLS client using MediaSourceExtension",
    "homepage": "https://github.com/video-dev/hls.js",
    "authors": "Guillaume du Pontavice <guillaume.dupontavice@dailymotion.com>",
    "repository": {
        "type": "git",
        "url": "https://github.com/video-dev/hls.js"
    },
    "bugs": {
        "url": "https://github.com/video-dev/hls.js/issues"
    },
    "main": "./dist/hls.js",
    "scripts": {
        "build": "npm run buildlib && rimraf dist/* && npm run builddist && npm run builddistlight",
        "buildlib": "rimraf lib/* && babel src --out-dir lib",
        "builddistlight": "browserify -t [browserify-conditionalify --definitions [--subtitle 0 --altaudio 0 ] ] -t browserify-versionify -t [babelify] -p browserify-derequire -p bundle-collapser/plugin -s Hls src/index.js --debug | exorcist dist/hls.light.js.map -b . > dist/hls.light.js && npm run minifylight",
        "builddist": "browserify -t browserify-versionify -t [babelify] -p browserify-derequire -p bundle-collapser/plugin -s Hls src/index.js --debug | exorcist dist/hls.js.map -b . > dist/hls.js && npm run minify",
        "preparerelease": "npm run build && npm run test && git add dist/* && git commit -m 'update dist'",
        "prerelease": "mversion prerelease && npm run preparerelease",
        "patch": "mversion p && npm run preparerelease",
        "minor": "mversion mi && npm run preparerelease",
        "major": "mversion ma && npm run preparerelease",
        "minify": "uglifyjs dist/hls.js -c sequences=true,dead_code=true,conditionals=true,booleans=true,unused=true,if_return=true,join_vars=true,drop_console=true -m --screw-ie8  > dist/hls.min.js",
        "minifylight": "uglifyjs dist/hls.light.js -c sequences=true,dead_code=true,conditionals=true,booleans=true,unused=true,if_return=true,join_vars=true,drop_console=true -m --screw-ie8  > dist/hls.light.min.js",
        "watch": "watchify --debug -s Hls src/index.js -t [babelify] -o dist/hls.js",
        "pretest": "npm run lint",
        "test": "mocha --compilers js:babel-register --recursive tests/unit",
        "testfunc": "mocha --compilers js:babel-register tests/functional/auto/hlsjs.js --timeout 40000",
        "lint": "jshint src/",
        "serve": "http-server -p 8000 .",
        "open": "opener http://localhost:8000/demo/",
        "live-reload": "live-reload --port 8001 dist/",
        "dev": "npm run builddist && (npm run open -s & parallelshell 'npm run live-reload -s' 'npm run serve -s' 'npm run watch -s')"
    },
    "devDependencies": {
        "arraybuffer-equal": "^1.0.4",
        "babel-cli": "^6.23.0",
        "babel-preset-es2015": "^6.18.0",
        "babel-register": "^6.24.0",
        "babelify": "^7.2.0",
        "browserify": "^14.1.0",
        "browserify-conditionalify": "^1.0.0",
        "browserify-derequire": "^0.9.4",
        "browserify-versionify": "^1.0.6",
        "bundle-collapser": "^1.2.1",
        "chromedriver": "^2.28.0",
        "deep-strict-equal": "^0.2.0",
        "exorcist": "^0.4.0",
        "http-server": "^0.9.0",
        "jshint": "^2.9.4",
        "live-reload": "^1.1.0",
        "mocha": "^3.0.2",
        "mversion": "^1.10.1",
        "opener": "^1.4.0",
        "parallelshell": "^2.0.0",
        "rimraf": "^2.6.1",
        "uglify-js": "^2.8.11",
        "url-toolkit": "^2.0.1",
        "selenium-webdriver": "^3.1.0",
        "watchify": "^3.7.0",
        "webworkify": "^1.4.0"
    }
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

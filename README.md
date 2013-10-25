LWF Loader
==========
Loads LWF in a simple and easy way.
This is the assistant tool for [LWF Library](https://github.com/gree/lwf).


How to run?
------------
1. Download the latest version of `lwf.js` from [LWF Repository](https://github.com/gree/lwf).
2. Download [underscore.js](http://underscorejs.org/) or compatible library. 
3. Include above files with `lwf-loader.js` and `lwf-util.js` to your project. 
4. Call loader function in your project.

Please refer to [LWF demo page](http://gree.github.io/lwf-demo/) for samples and more information.


Structure
----------
```
|-- lwf-loader
|   |-- doc 
|       |-- Resource_Guideline.md
|   |-- js
|       |-- lwf-loader-all.min.js
|       |-- lwf-loader.js
|       |-- lwf-util.js
|   |-- README.md
```

* **/lwf-loader/doc/Resource_Guideline.md**

  Resource Guideline for assets that could be used with lwf-loader and LWF.


* **/lwf-loader/js/lwf-loader-all.min.js**

  Minified version of `lwf-loader.js` with `lwf-util.js`. Closure compiler(SIMPLE_OPTIMIZATIONS) is applied for minification.


* **/lwf-loader/js/lwf-loader.js**

  Main implementation of lwf-loader. 


* **/lwf-loader/js/lwf-util.js**

  Utility helper for lwf-loader. 


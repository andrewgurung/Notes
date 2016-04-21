## Setup ESLint in Atom Editor

### Install the packages
1.  Install `linter` package
	- Settings --> Install --> Search 'linter cow'
	- Install 'linter' package.

	Note: There are many linter packages.  
	Find the package with description 'A Base Linter with Cow Powers' and download count of over 1 million.

2.  Install `linter-eslint` package
	- Settings --> Install --> Search 'linter-eslint'
	- Install 'linter-eslint' package

### Use with Lint plugins
1.	Navigate to your VSAC ES6 project folder  
	Eg: `C:\Users\gurunga\git\vsac-develop\vsac-ui-es6`

2. 	Install locally to your project eslint and Airbnb's ESLint rules, including EcmaScript 6+ and React
	```
	npm install --save-dev eslint-config-airbnb eslint-plugin-import eslint-plugin-react eslint-plugin-jsx-a11y eslint
	```

	- Link to Airbnb ESLint Configuration Github Page: https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb

	- Link to Airbnb's JavaScript Style Guide: https://github.com/airbnb/javascript

3. 	Create `.eslintrc` file under your VSAC ES6 project folder

	Eg: `C:\Users\gurunga\git\vsac-develop\vsac-ui-es6\.eslintrc`  
	Add the following configuration to the empty `.eslintrc` file
	```js
	{
		  "extends": "airbnb",
		  "plugins": [
			"jsx-a11y"
		  ],
		  "rules": {
			"jsx-a11y/img-uses-alt":0,
			"jsx-a11y/redundant-alt":0,
			"jsx-a11y/valid-aria-role":0
		  }
	}
	```

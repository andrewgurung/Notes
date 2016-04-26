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

Common ESLint errors
#indent (Enforce consistent indentation and tab spacing)

	Solution: Use beautify to fix the indentation
	1) On the Atom Editor --> Project Explorer --> Right click on a file --> Beautify file
			Or
	2) Open a file in Atom Editor --> Right click anywhere inside the open file --> Beautify Editor Contents

#quotes
	"jqgrid"

	Solution: doublequote to singlequote
	'jqgrid'

#func-names (Require Function Expressions to have a Name)
$.each(recordsToDelete, function() {
  expGrid.jqGrid('delRowData', recordsToDelete[i]);
  i++;
});

Solution: Use Arrow functions
$.each(recordsToDelete, () => {
  expGrid.jqGrid('delRowData', recordsToDelete[i]);
  i++;
});
	
#max-len
	import { post, postJson, showFetchError, fetchJson, fetchText, validSession } from "./../../util/vsacFetch";

	Solution:
	Either break down to multiple lines
	Or Add ignore case in .eslintrc config file

#no-var
	var collabDetailsValueSets;

	Solution:
	Convert to let or const

#object-shorthand
	loadComplete: function() { $('#cb_myCollabSiteTable').hide(); },

	Solution: Use ES6 method shorthand
	loadComplete() { $('#cb_myCollabSiteTable').hide(); },

#property-shorthand
	url: url

	Solution
	url

#key-spacing
	multiselect : true,

	Solution: Remove extra space after multiselect
	multiselect: true;

#prefer-const
	let cm = $(this).jqGrid('getGridParam','colModel');

	Solution: cm is never reassigned so convert to const
	const cm = $(this).jqGrid('getGridParam','colModel');


#no-use-before-define
	viewCollabDetails(siteID);

	Solution:
	Move function declaration to top

#space-before-blocks
	if(siteSeq === null)

	Solution:
	if (siteSeq === null)

#func-names
	$('#collabContainer').bind('loadMyCollabSites', function(e, arg) {

	Solution: Require Function Expressions to have a Name
	$('#collabContainer').bind('loadMyCollabSites', function loadMyCollabSites(e, arg) {

#no-shadow
	The variable a inside of b() is shadowing the variable a in the global scope:
	var a = 3;
	function b() {
		var a = 10;
	}

	Solution:
	Define different name to avoid shadowing

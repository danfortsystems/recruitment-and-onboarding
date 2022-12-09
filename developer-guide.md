# Danfort Systems Developer Guide


**Workflow**

The GitFlow workflow is used to manage the source code using git. With this approach, there are two main branches: _master_ (or _main_), containing the code deployed to production, and optionally, _dev_,containing code that is being staged for eventual deployment. If there is no _dev_ branch, the _master_ branch fulfills both functions. The workflow proceeds as follows: 

1. When starting work on an issue, create a new local feature branch (from the _dev_ or _master_ branch), naming it according to the following template: 
`feature/{Github issue #, without hash symbol}_{shortened title of GitHub issue, in dash case, with the first character of each word in uppercase}`.


2. Keep adding commits to this feature branch as necessary until your work is done, then squash the commit into one with a properly descriptive message. Squashing commits helps to keep the git history clean when the branch is merged with dev. Please do not push to the default remote until you have squashed your commits into one and are ready to submit your work for review. Therefore, make sure your repository is backed up by DropBox so that you do not lose work locally. You can also create temporary branches based on the main feature branch you are working on and push them to the default remote (name them with the prefix temp, e.g., temp/{name of branch}. Delete these temporary branches when they are no longer needed 

3. When you are ready to submit your work, create a pull request for the issue against the dev branch. Name the pull request as follows: _PR: {title of GitHub issue, without the hash number}_. Add a comment that refers to the issue number (e.g., Resolves issue #123). Add other team members as reviewers, who will test, review the code and comment if the PR is ok. Apply the tag “Review” to the PR to indicate that it’s ready to be reviewed (as opposed to PRs currently being worked on) 
 
4. If there are problems with the work, the pull request will be updated to indicate what you need to make change. The “Review” tag should then be removed. Make the changes, squash any additional commit since the last review, and push to the default remote when done. 
 
5. When the work is acceptable, we will merge the pull request feature branch with the dev branch and then delete the feature branch from the default remote. The pull request and related issue will then be closed.  

4. You can rename the merged feature branch to archived/… on your local, and keep for some time in case something happens on the default remote 

 

 

**Naming** 

- Use _camelCase_ for: Variables, Functions, Class, Interface, and Type members and methods 

- Use _PascalCase_ for: Classes, Interfaces, Namespaces, Enums and their members

- Avoid prefixing interface names with “I” 

- -Do not use "_" as a prefix for private properties unless necessary. 

- Use whole words in names when possible. 

- Name files with dash-case. e.g., accordion.tsx, my-control.tsx, utils.ts, map.ts etc. 

- Method returning something should be prefaced by get (i.e. getResult() ) 

- Methods returning something & not requiring arguments can be members of a component (get Results() ) 

- Asynchronous method should be suffixed by Async (i.e getTablesAsync) 

- Variables containing JSX/HTML elements should mention it (i.e. analysisTitleJSX) 

- For Enums it is preferable to use names in singular. 

- When naming components, use the suffix _Box_ When it’s wrapping one children element, _Panel_ when it’s laying out multiple  child elements, _Input_ for input control elements, and _View_ when it's a panel that generates its children based on some data passed to it. 

 

 

**Style**

- Prefer to use arrow functions over anonymous function expressions. 

- Avoid declaring undefined variables that will be assigned a value later, when possible 

- Use anonymous functions when possible 

- For asynchronous functions, use the Async/Await style instead of the .then() if possible 

- Almost never use/allow the any type, explicitly or implicitly. 

- Only surround arrow function parameters when necessary.  

- Always surround loop and conditional bodies with curly braces. Statements on the same line are allowed to omit braces. 

- Open curly braces always go on the same line as whatever necessitates them. 

- Parenthesized constructs should have no surrounding whitespace.  

- A single space follows commas, colons, and semicolons in those constructs.  

- Use a single declaration per variable  

_ _else_ goes on a separate line from the closing curly brace. 

- Prefer backticks (\`) to delimit strings. When you can't use them, you can using single quotes (') or double quotes ("). 

- Use template strings instead of concatenating with + 

- Avoid terminating statements with semicolons unless necessary 

- The code must be properly formatted before being submitted in the PR (e.g., right-click in VS Code editor, choose format code) 

- Conditionals should always have a comparison statement (e.g, ‘if (x === 0)’ instead of ‘if (x)’ 

- The closing bracket “>” of JSX elements should be on the same line as the last line of its properties, not on its own line below 

- When working with the UI elements: There should never be any element within another element if they are not needed. For example, Stack-Panels within Stac-Panels where they are only serving to wrap some inner items without any specific layout 

- Don’t close tag with ‘/>’, use full closing tags (‘</input>’) -

**Null and Undefined**

- Use undefined instead of null in general 

- Use null where its a part of the API or convention 

- Use explicit check for objects being null or undefined 

 

**Type Definitions**

- Do not export types/functions unless you need to share it across multiple components. 

- Do not introduce new types/values to the global namespace. 

- Shared types should be defined in 'types.d.ts'. 

- Within a file, type definitions should come first. 

- Avoid using the _any_ as type as much as possible. Implicit any must also be avoided as much as possible. 

- Do not use a type to define a structure unless you cannot use an interface 


**Debugging/Troubleshooting tips**

If you start seeing strange errors involving the TypeScript intellisense, try the following: 

Check the folders included in the rootDirs parameter in tsconfig.json 

Try putting a semicolon before or after the offending statement(s) 

Restart the IDE program (e.g., VS Code) 

 

Testing 

The testing suite for each file should follow the following pattern:  file -> class -> method -> cases, and In case there are not clases: file -> functions -> cases,  

 

**Checklist before submitting your PR:**

- Indicate if the PR includes important architectural changes and/or changes in the types.d.ts. 

- Make sure the branch is named properly. Use a name that is reasonably short and also describes the issue correctly. 

- Check your capitalization in issue titles and descriptions. 

- Format your code using the VS Code feature (or the one that your IDE has) 

- Make sure your code is up-to-date with the current dev branch. 

- Use cuid() instead of shortid.generate(), if you need a css/html "safe" id 

- RequestX and ReportX prefixes convention should be used when passing function references between parent and children components. Use the RequestX naming convention for methods defined in a parent component that will be used by children components, when the child component needs to be changed from the parent. Use the ReportX naming convention when the child component changes its own state and merely informs the parent. 

- Make sure to remove unused code or imports



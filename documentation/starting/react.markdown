# Getting started with React Web App


## Create new page

- Create the page file on the <code>views/pages</code> directory. *You can do a logical grouping of pages creating new folders on <code>views/pages</code> or using existing ones.*
- Add the new page's route on <code>views/routes.js</code>.
- Create access to new page:
	- To access from left menu, add the item on <code>_nav.js</code>. 
	- To access from header's dropdown menu, add item on <code>components/header/AppHeaderDropdown.js</code>.

#### Important:
The pages are not accessible  unless the user has the permissions for the page's url. This are set on the backend and sent on the endpoint <code>security/authenticate</code>.
 
 
## Use translations

To use the language translations on your pages you need to:

1. On top of the page's file add <code>import \{ useTranslation } from 'react-i18next' </code>
2. Then inside the page definition function add <code>const { t, i18n } = useTranslation()</code>
3. Now when you add text to you code instead of writing <code>"Some text"</code>, write <code>{i18n.t("Some text")}</code>
4. If text to display doesn't have a translation yet, add the translation on the <code>translation.json</code> files on <code>location/</code>

## Add new language
 
1. Create a new folder on <code>locales/</code> named as the abbreviation you want to use for the new language.
2. Copy into that folder the file <code>locales/EN/translation.json</code>
3. Change the values on the json for the new translations.
4. Add the new language on the <code>i18n</code> initialization on <code>helpers/i18n.js</code>
 
 ## Calls to API
 
All calls to the SolaREC API are handled by the function <code>DataAPI</code> defined on <code>helpers/DataAPI.js</code>.
<br>Use the function as follows:
<pre><code>DataAPI({
	endpoint: 'some_endpoint',
	method: 'GET or POST',
	body: body,
}).then((response) => {
	// Do stuff
}))
</code></pre>

## Using Cookies

If you need to use Cookies for your new page, you can import the functions <code>getCookie</code> and/or <code>setCookie</code> defined on <code>helpers/sessionCookie.js</code>.


 ## Other useful information
 
 ### Helpers
 
 If you need helper functions which might be used across the app, you can implement them on the <code>file helpers/utils.js</code>
 
 ### Components
 
 To build new components to use across your pages, add them to <code>components/</code>
 
 But first, see if you can find what you need on CoreUI's components list. Take a look at the documentation on https://coreui.io/react/docs/
 
 ### Style
 
 On the file <code>scss/_variables.scss</code> you can modify global variables that can help you change the main style of the app. Take a look at https://coreui.io/react/docs/customize/options/.
 
 If you need further customizations add your code on <code>scss/_custom.scss</code>
 
 
 ## Unit test
 
 For unit testing the app uses **Jest**. 
 
 If you want to create unit tests for your code just create a file on the same directory as the one you are testing with the same name, and type <code>.test.js</code>. So, if I'm testing <code>example.js</code>, I need to create <code>example.test.js</code>.
 
 To understand how to build your testing files start here: https://jestjs.io/docs/tutorial-react

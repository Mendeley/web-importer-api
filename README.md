*__Please Notes:__ This is currently an experimental API. If you can interested in using it, please get in touch with [See Wah Cheng][].

# Mendeley Web Importer API

The Web Importer API provides callbacks to third-party websites to improve integration with the [Mendeley Web Importer bookmarklet][].

As a website developer, you can leverage the Mendeley Web Importer to allow users to easily save academic references and full text PDFs from your website into their Mendeley libraries. The users do not have to have [Mendeley Web Importer bookmarklet][] installed in their browsers for this API to work.

## Usage

 1. include `importer-api.js` at the bottom of your html before the closing body tag
 2. on page load, call `MendeleyImporterApi.registerHostId()`, `MendeleyImporterApi.registerDataCallback()` and, optionally, `MendeleyImporterApi.registerUserIdentityCallback()` to register the callbacks
 3. if implementing a button to trigger the import, rather than relying on the users using their installed [Mendeley Importer bookmarklet][], call `MendeleyImporterApi.open()` to programmatically invoke the Mendeley Web Importer

## Available Methods

### MendeleyImporterApi.registerHostId(hostId) ###

`hostId` is expected to be a string, which identifies the host site

Use the fully qualified domain name of your site, e.g. www.your-site.com. Note that this is purely for the purpose of identification.

### MendeleyImporterApi.registerUserIdentityCallback(callback) ###

`callback` is expected to be a function, which returns json data representing the identity of the current user on your site

Upon initialisation, the Mendeley Web Importer javascript will invoke the callback with a boolean argument to indicate the current context: true if the importer is invoked as a bookmarklet action, and false if the importer is explicitly invoked via the `.open()` call.

### MendeleyImporterApi.registerDataCallback(callback) ###

`callback` is expected to be a function, which returns json data representing the articles (metadata) on the current page on your site

Upon initialisation, the Mendeley Web Importer javascript will invoke the callback with a boolean argument to indicate the current context: true if the importer is invoked as a bookmarklet action, and false if the importer is explicitly invoked via the `.open()` call.

### MendeleyImporterApi.open() ###

This will load the Mendeley Web Importer javascript via script tag injection, and calls its initialisation function to display the importer UI.

If Mendeley Web Importer javascript is already loaded, it will simply call its initialisation function without loading it again.

### MendeleyImporterApi.close() ###

This will simply remove the importer UI element from the current page. This will not error even if it is called when the UI is not currently displayed.


[Mendeley Web Importer bookmarklet]:http://www.mendeley.com/import/
[See Wah Cheng]:http://www.mendeley.com/profiles/see-wah-cheng/

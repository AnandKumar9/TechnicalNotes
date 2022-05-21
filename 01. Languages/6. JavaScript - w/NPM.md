Installing gulp - Run both of these. This will require write permissions in usr/local/lib/node_modules. So manually add write permissions to them through Finder.
npm install --global gulp
npm install --global gulp - cli

-------

Atom editor -

Installing a plugin - Its best to install plugins from command line using apm (Atom package manager). apm is automatically installed with Atpom, so there is nothing more that needs to be done to install Atom in particular.


apm config set strict-ssl false         // First run this to disable ssl, else there was an issue happening for me while installing any plugin
apm install atom-beautify --verbose     // Install the plugin in question


Using atom-beautify, a plugin for indenting html, javascript, etc. files. Select the text in Atom, tap Option-Control-B

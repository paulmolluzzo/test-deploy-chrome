# Test Deploy to Chrome

A fake extension to test auto deploying to Chrome Web Store with grunt via Travis CI.

# Replicating the Process in Another Project
1. Go to the [Google Developers Console](https://console.developers.google.com/) to create the CLIENT_ID and CLIENT_SECRET you'll need to deploy. Start with the "Before You Begin" section here https://developer.chrome.com/webstore/using_webstore_api and make sure you have a `CLIENT_ID`, `CLIENT_SECRET`, and `REFRESH_TOKEN` following those instructions.
2. Create a new Google Extension via the [Dashboard](https://chrome.google.com/webstore/developer/dashboard) as usual. You need to start the app this way.
3. Copy the Gruntfile in this repo into your repo and copy the App ID for the extension from the Chrome Web Store (it's the last part of the URL for the published extension).
4. Update/create the repo package.json file to include the dependencies for `grunt` and `grunt-webstore-upload`.
5. Setup Travis CI with the `before_install` and `after_success` commands in this repo.
6. In the ./chrome-deploy.sh file, make sure that the command to zip the extension has the correct directory name for your extension in the second argument.
7. Install the [Travis CI ruby gem](https://github.com/travis-ci/travis.rb) and encrypt the `CLIENT_ID`, `CLIENT_SECRET`, and `REFRESH_TOKEN`, or just add them as env vars in the Travis CI website.
8. Push your repo.

# Specifying when to deploy

This repo will deploy on a push on the `master` branch or if there is a tag in the release, but not on pull requests. To change these rules, change the tests in the `if` block in chrome-deploy.sh.

--------

MIT (c) 2016 [Paul Molluzzo](http://paul.molluzzo.com)

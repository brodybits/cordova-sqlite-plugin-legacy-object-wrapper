# cordova-sqlite-plugin-legacy-object-wrapper

LICENSE: GPL v3 (based on MIT-licensed software from [`github:xpbrew/cordova-sqlite-storage`](https://github.com/xpbrew/cordova-sqlite-storage)

provides cordova-sqlite-storage JavaScript API for [`github:brodybits/cordova-plugin-sqlite-batch-connection-manager-core`](https://github.com/brodybits/cordova-plugin-sqlite-batch-connection-manager-core), which in turn uses [`github:brodybits/sqlite-batch-connection-core-2020-01`](https://github.com/brodybits/sqlite-batch-connection-core-2020-01)

How to this library with the new plugin in an app:

- ensure that any other SQLite plugin is completely removed
- to build `cordova-plugin-sqlite-batch-connection-manager-core` from [`github:brodybits/cordova-plugin-sqlite-batch-connection-manager-core`](https://github.com/brodybits/cordova-plugin-sqlite-batch-connection-manager-core):
  - `git clone https://github.com/brodybits/cordova-plugin-sqlite-batch-connection-manager-core`
  - `(cd cordova-plugin-sqlite-batch-connection-manager-core && make build)`
- do `cordova plugin add ./cordova-plugin-sqlite-batch-connection-manager-core`
- copy `cordova-sqlite-plugin-legacy-object-wrapper.js` from this project into the `www` directory
- add the following to `www/index.html`: `<script src="cordova-sqlite-plugin-legacy-object-wrapper.js"></script>`
- do `cordova plugin add cordova-sqlite-storage-file`

IMPORTANT LIMTATIONS AND OTHER NOTES:

- uses DEPRECATED `location: 2` setting, which saves the database in the `Library` directory on iOS & macOS ("osx")
- close & delete operations not supported
- numeric values are always handled as double-precision floating-point values, which is consistent with the JavaScript language itself
- some exceptional values such as Infinity, -Infinity, -0, and NaN are not tested and not supported at this point
- error `code` always reported as 0
- no error code in the error message
- multi-byte UTF-8 characters not well tested, with known issue on iOS & macOS
- issues with some other sequences such as 0xFFFE

# cordova-sqlite-storage-connection-core-js

LICENSE: GPL v3 (based on MIT-licensed software from [`github:xpbrew/cordova-sqlite-storage`](https://github.com/xpbrew/cordova-sqlite-storage)

provides cordova-sqlite-storage API for [`github:brodybits/sqlite-batch-connection-core-preview-2020-01`](https://github.com/brodybits/sqlite-batch-connection-core-preview-2020-01)

How to this library with the new plugin in an app:

- ensure that any other SQLite plugin is completely removed
- to build `cordova-sqlite-demo-plugin` from [`github:brodybits/sqlite-batch-connection-core-preview-2020-01`](https://github.com/brodybits/sqlite-batch-connection-core-preview-2020-01):
  - `git clone https://github.com/brodybits/sqlite-batch-connection-core-preview-2020-01`
  - `cd sqlite-batch-connection-core-preview-2020-01`
  - `(cd sccglue && make ndkbuild)`
  - `(cd cordova-demo && make prepare-plugin)`
- add `cordova-demo/cordova-sqlite-demo-plugin` built in `sqlite-batch-connection-core-preview-2020-01`
- copy `SQLitePlugin.js` from this project into the `www` directory
- add the following to `www/index.html`: `<script src="SQLitePlugin.js"></script>`
- `cordova plugin add cordova-sqlite-storage-file`

IMPORTANT LIMTATIONS AND OTHER NOTES:

- uses DEPRECATED `location: 2` setting, which saves the database in the `Library` directory on iOS & macOS ("osx")
- close & delete operations not supported
- error `code` always reported as 0
- no error code in the error message
- multi-byte UTF-8 characters not well tested, with known issue on iOS & macOS
- issues with some other sequences such as 0xFFFE

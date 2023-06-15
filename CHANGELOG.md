# VSCODE-TASKEXPLORER CHANGE LOG

## Version 2.13.2 (December 23rd, 2022)

### Bug Fixes

- last two releases are inoperable due to missing json5 package

## Version 2.13.1 (December 23rd, 2022)

### Bug Fixes

- transfer old settings to new settings in some cases did not work in the previous release

## Version 2.13.0 (December 23rd, 2022)

### Bug Fixes

- super bug kill - 'a node named .... has already been added', after which most of the tree breaks until refreshed.
- changing the 'show last tasks' or 'show favorites' settings have no effect until restart [Fixes #173]

### Documentation

- readme displays broken badge link due to space char.

### Features

- complete new layout, 10x easier to navigate and configure
- add new setting 'show hidden vscode tasks', which will not include workspace tasks in the task tree that have with the 'hide' property set in the task definition.  Defaults to 'true' to resume past behavior. [Closes #182]

### Refactoring

- improve logging legibility, format any logged json objects.
- add additional logging when constructing a tree file node

## Version 2.12.0 (December 21st, 2022)

### Bug Fixes

- ant tasks no longer show relative path in grouped tree nodes if file is named build.xml. [Fixes #179]

### Features

- add new setting 'expanded', an object that can specify either special or project folders to either be expanded or collapsed in the explorer tree on startup. [Closes #176]

## Version 2.11.0 (December 21st, 2022)

### Bug Fixes

- last release is inoperable.

### Features

- add new setting 'excludeTask', an array of regex pattern strings that can be used to ignore / exclude specific task names globally.   Available in the context menus as well as editing the VSCode settings manually. [Closes #178]
- fix(commands) clicking on a task to open the src file does not scroll to the task name in package.json files that are not located in the root project workspace folder.

## Version 2.10.0 (December 21st, 2022)

### Bug Fixes

- **Reporting:** parsing report fails if there are User type workspace tasks.
- **Logging:** correct log blank line functionality

### Documentation

- **Readme:** update title
- **Readme:** update vs marketplace svg badges as all of a sudden microsoft decides to fail releases because of a GD img path.

### Features

- add parsing report available from the command pallette (for all projects) or the Explorer context menu (per project).

### Refactoring

- add 'obj' and 'Assets' to list of default exclude paths
- some commands should not be avail in cmd pallette

### Build System

- update ap publishrc file to latest ap format.
- move build system to webpack v5.68.0 and update all webpack dependencies to support NodeJS 17 environment.  Also eliminates 3 dev dependency security vulnerabilities in webpack v4 unfixable by npm audit.

## Version 2.9.1 (February 4th, 2022)

### Bug Fixes

- **Providers:** app-publisher 'prompt version' task fails.

### Documentation

- **Readme:** update api section with task definition info

## Version 2.9.0 (February 1st, 2022)

### Bug Fixes

- **Api:** external tasks fail to run as background tasks
- **Logging:** value log writes are spaced differently in random blocks

### Features

- **Api:** add invalidate call through for task providers that want TE to do the file system watching and invalidation notifying (works with getGlobPattern)

### Refactoring

- **Logging:** add additional logging for task tree and tree files
- **Api:** peform checks on icon paths specified by external task providers

### Build System

- update .vscodeignore

## Version 2.8.0 (January 31st, 2022)

### Bug Fixes

- **Api:** tree nodes show when external providers registers but expanding them throws error
- **Tree:** typescript config files not names 'tsconfig.json' do not update in the tree if moved/renamed.

### Documentation

- **Readme:** update api section

### Features

- **Api:** add icon support for API

## Version 2.7.1 (January 28th, 2022)

### Bug Fixes

- **Tree:** becomes unresponsive after editing a tsconfig.json file

## Version 2.7.0 (January 27th, 2022)

### Bug Fixes

- **Explorer:** tsc tasks are not refreshed if a tsconfig.json is removed or moved.
- **Api:** if multiple enable/disable settings are changed quickly programatically, several progress messages for parsing are opened in the toolbar.
- **Providers:** makefile task does not use custom $gccte parser if ms-vscode.cpptools extension is not installed
- **Providers:** composer parser throws unhandled exception parsing invalid JSON
- **Providers:** composer tasks are scanned out of alpha order

### Documentation

- **Readme:** add section on external task provider api. [References #22]
- **Readme:** add section on animated running task icons

### Features

- **Api:** working initial implementation of external task provider api [References #22]

## Version 2.6.3 (January 24th, 2022)

### Bug Fixes

- **Providers:** custom parser throws exception on invalid file
- **Providers:** ant-program parser does not work
- **Api:** using the 'stop' command on a detached task throws unhandled exception
- **Tree:** deleting a folder from outside VSCode while  open causes tree to break

### Refactoring

- **General:** use internal storage as opposed to vscode setting for storing custom task labels
- **Providers:** add check for ignore in ReadTask

## Version 2.6.2 (January 23rd, 2022)

### Bug Fixes

- composer tasks use an incorrect command when executed. [Fixes #166]

## Version 2.6.1 (January 23rd, 2022)

### Bug Fixes

- new bash glob patterns do not work
- the new setting to disable animated icons broke context for running tasks

## Version 2.6.0 (January 22nd, 2022)

### Bug Fixes

- when settings for click action is 'Execute', can't use the other 'Open' actions. [Fixes #160]
- pause button does not work in Explorer view

### Features

- add support for php composer tasks found in composer.json [Closes #150]
- add new setting 'Glob Patterns Bash' for specifying glob patterns for identifying bash scripts with no extension. [Closes #153]
- add new setting 'Disable animated icons' to disable spinning icons when running tasks, known to cause high CPU usage on some systems. [Closes #157]
- add label rename command for special folder items [Closes #164]

### Refactoring

- the 'Include Ant' setting has been deprecated, use 'Glob Patterns Ant'.

## Version 2.5.7 (August 28th, 2021)

### Bug Fixes

- multiple scans occur if a task is running, the explorer view is not visible, and a package.json script name that is referenced in tasks.json is modified.

## Version 2.5.6 (August 21st, 2021)

### Bug Fixes

- events are processing for bothe sidebar and explorer view even if only one is activated and in use.

## Version 2.5.5 (August 20th, 2021)

### Bug Fixes

- regression - leaving view while task is running then coming back after it has finished causes re-parse of all tasksif both main and sidebar view are enabled.

### Documentation

- **Readme:** update open source project list

### Build System

- **Ap:** update renamed 3.7  publishrc properties
- codecov upload fails when using git bash

## Version 2.5.4 (August 17th, 2021)

### Bug Fixes

- **General:** if a task completes while the explorer view is not visible, the tree is not refreshed

### Build System

- fix -vscode release only contains webpacked files but vsce complains of 850+files in package.

## Version 2.5.3 (August 17th, 2021)

### Refactoring

- handle VSCode v1.56+ randomly emitting 10+ task start/stop events when a task starts and finishes

### Build System

- fix - vsix fails to upload with guthub release

## Version 2.5.2 (August 15th, 2021)

### Bug Fixes

- **Tasks:** start/stop events processing for non-visible view
- **Tasks:** stopping a task with 'keep terminal on stop'  option set still x3 fails for some tasks.

## Version 2.5.1 (August 9th, 2021)

### Bug Fixes

- **Tree:** display name for a task is not properly trimmed when grouping is enabled and the group separator character is something other than the default '-'.
- **Tasks:** stopping a task with 'keep terminal on stop'  option set still fails for some tasks.

## Version 2.5.0 (August 9th, 2021)

### Bug Fixes

- **Tasks:** stopping a task with 'keep terminal on stop' works for some tasks but not for all.

### Performance Enhancements

- **Build:** webpack build runs 10-15% faster, package size halved

## Version 2.4.2 (August 7th, 2021)

### Bug Fixes

- **General:** v2.4.0/1 does not load - invalid package-lock.json reference to 'chevrotain'

## Version 2.4.1 (August 7th, 2021)

### Bug Fixes

- **General:** v2.4.0 does not load - invalid package-lock.json reference to 'chevrotain'

### Refactoring

- **General:** touch for vscode api changes

## Version 2.4.0 (August 7th, 2021)

### Bug Fixes

- **Tree:** tree does not populate if not visible when task scan completes.

### Features

- **Providers:** add support for python pipenv pipfile scripts [closes #155]

### Refactoring

- **Settings:** default 'keepTermOnStop' to true
- **Logging:** further improve readability

### Build System

- the vsix installer is not being published as a github release asset

## Version 2.3.2 (July 2nd, 2021)

### Bug Fixes

- **App-Publisher:** tree labels are showing an empty set of parenthesis

## Version 2.3.1 (June 30th, 2021)

### Documentation

- **Readme:** add app-publisher section
- **Readme:** update contributors section

### Bug Fixes

- **Providers:** app-publisher custom config files are found but tasks always run with default config.

### Build System

- **Publishrc:** run local test task

### Other Notes

- build(package.json): update description [skip ci]

# [2.3.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v2.2.0...v2.3.0) (2021-06-06)


### Bug Fixes

* explorer occassionally hangs / stops responding [fixes [#143](https://github.com/spmeesseman/vscode-taskexplorer/issues/143)] ([a68166e](https://github.com/spmeesseman/vscode-taskexplorer/commit/a68166e))
* if a task label exists that itself is equal to a 1st level task group name of another task (as per the separator char), the tree breaks. [fixes [#149](https://github.com/spmeesseman/vscode-taskexplorer/issues/149)] ([3716ca7](https://github.com/spmeesseman/vscode-taskexplorer/commit/3716ca7))
* Makefile variables assigned with := are interpreted as rules. [fixes [#146](https://github.com/spmeesseman/vscode-taskexplorer/issues/146)] ([7b878d8](https://github.com/spmeesseman/vscode-taskexplorer/commit/7b878d8))
* maven settings string is blank ([7e87b01](https://github.com/spmeesseman/vscode-taskexplorer/commit/7e87b01))
* vscode tasks group separtors fixed by last check-in. [fixes [#147](https://github.com/spmeesseman/vscode-taskexplorer/issues/147)] ([f5d5b32](https://github.com/spmeesseman/vscode-taskexplorer/commit/f5d5b32))


### Documentation

* **readme:** update featires by version section ([07d9f5e](https://github.com/spmeesseman/vscode-taskexplorer/commit/07d9f5e))


### Features

* add 10+ new app-publisher commands, set up w/ group separator task names ([ce9c8f0](https://github.com/spmeesseman/vscode-taskexplorer/commit/ce9c8f0))

# [2.2.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v2.1.0...v2.2.0) (2021-05-31)


### Features

* add support for maven - closes [#107](https://github.com/spmeesseman/vscode-taskexplorer/issues/107) ([1f90d1b](https://github.com/spmeesseman/vscode-taskexplorer/commit/1f90d1b))

# [2.1.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v2.0.7...v2.1.0) (2021-05-28)


### Bug Fixes

* adding a new script type task file causes explorer to stop responding ([9551467](https://github.com/spmeesseman/vscode-taskexplorer/commit/9551467))
* script type task files that are located in same folder always 'open' same file ([4716e66](https://github.com/spmeesseman/vscode-taskexplorer/commit/4716e66))


### Features

* add app-publisher task 'View Pending Changelog' ([4653c0d](https://github.com/spmeesseman/vscode-taskexplorer/commit/4653c0d))

## [2.0.7](https://github.com/spmeesseman/vscode-taskexplorer/compare/v2.0.6...v2.0.7) (2021-02-28)


### Bug Fixes

* npm file nodes are appearing even if npm tasks are disabled in settings. [fixes [#144](https://github.com/spmeesseman/vscode-taskexplorer/issues/144)] ([d76756b](https://github.com/spmeesseman/vscode-taskexplorer/commit/d76756b))

## [2.0.6](https://github.com/spmeesseman/vscode-taskexplorer/compare/v2.0.5...v2.0.6) (2021-02-27)


### Bug Fixes

* v2.0.5 does not include required node_modules in package, extension does not load ([d9a9a02](https://github.com/spmeesseman/vscode-taskexplorer/commit/d9a9a02))

## [2.0.5](https://github.com/spmeesseman/vscode-taskexplorer/compare/v2.0.4...v2.0.5) (2021-02-27)


### Bug Fixes

* add to favorites fails if there is only one workspace folder and no tasks exist in the last tasks folder ([6456148](https://github.com/spmeesseman/vscode-taskexplorer/commit/6456148))
* adding a grouped node to excludes via context menu isnt working, it has be done at the root node ([ce4ad76](https://github.com/spmeesseman/vscode-taskexplorer/commit/ce4ad76))
* broken async on add/remove favorite ([c4cf8ab](https://github.com/spmeesseman/vscode-taskexplorer/commit/c4cf8ab))
* manually stopping a task at the instant it finishes can cause extension to stop responding ([4e84592](https://github.com/spmeesseman/vscode-taskexplorer/commit/4e84592))
* npm install tasks are showing up for subfolders containg a package.json, npm management tasks should only showin file node context menu ([1712966](https://github.com/spmeesseman/vscode-taskexplorer/commit/1712966))
* regression - removing a workspace folder causes extension to stop responding ([4703ebb](https://github.com/spmeesseman/vscode-taskexplorer/commit/4703ebb))


### Build System

* initial preparation for webpack build ([e7cedef](https://github.com/spmeesseman/vscode-taskexplorer/commit/e7cedef))


### Code Refactoring

* additional logging [references [#138](https://github.com/spmeesseman/vscode-taskexplorer/issues/138)] ([359bf37](https://github.com/spmeesseman/vscode-taskexplorer/commit/359bf37))
* improve logging indentation for better readability ([e35a80e](https://github.com/spmeesseman/vscode-taskexplorer/commit/e35a80e))


### Documentation

* jsdoc commenting ([3783548](https://github.com/spmeesseman/vscode-taskexplorer/commit/3783548))

## [2.0.4](https://github.com/spmeesseman/vscode-taskexplorer/compare/v2.0.3...v2.0.4) (2021-02-20)


### Bug Fixes

* open command does not work for vscode/workspace tasks if a path property is defined. ([8535d69](https://github.com/spmeesseman/vscode-taskexplorer/commit/8535d69))
* tree build loops indefinitely when vscode/worskspace tasks with path properties exist. [fixes [#133](https://github.com/spmeesseman/vscode-taskexplorer/issues/133)] ([d8fb390](https://github.com/spmeesseman/vscode-taskexplorer/commit/d8fb390))

## [2.0.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v2.0.2...v2.0.3) (2021-02-19)


### Bug Fixes

* makefile targets are not parsed correctly in v2. [fixes [#136](https://github.com/spmeesseman/vscode-taskexplorer/issues/136)] ([2ac9c6c](https://github.com/spmeesseman/vscode-taskexplorer/commit/2ac9c6c))
* modifying a task file other than an npm package.json causes workspace tasks to disappear nd requires manual refresh to get back ([44385f9](https://github.com/spmeesseman/vscode-taskexplorer/commit/44385f9))

## [2.0.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v2.0.1...v2.0.2) (2021-02-15)


### Bug Fixes

* if no ant includes are specified in sttings.json, the xtension does not start if all task types are enabled ([0a4ede6](https://github.com/spmeesseman/vscode-taskexplorer/commit/0a4ede6))
* insiders 1.53.1 build hangs randomly ([70e34c8](https://github.com/spmeesseman/vscode-taskexplorer/commit/70e34c8))


### Code Refactoring

* extract more funcitonality into base task interface for easier debugging ([a2ff41a](https://github.com/spmeesseman/vscode-taskexplorer/commit/a2ff41a))

## [2.0.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v2.0.0...v2.0.1) (2021-02-15)


### Bug Fixes

* after modifying and saving an ant file, changes are no longer noticed. ([de7dfdd](https://github.com/spmeesseman/vscode-taskexplorer/commit/de7dfdd))
* modifying a package.json that has defined tasks in a tasks.json file causes the vscode tasks tree node to break ([7b0c4f7](https://github.com/spmeesseman/vscode-taskexplorer/commit/7b0c4f7))


### Code Refactoring

* task definitions are not properly exposed to vscode api ([bc1f0b4](https://github.com/spmeesseman/vscode-taskexplorer/commit/bc1f0b4))


### Documentation

* **readme:** touch info ([a5e8bad](https://github.com/spmeesseman/vscode-taskexplorer/commit/a5e8bad))

# [2.0.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.30.2...v2.0.0) (2021-02-14)


### Bug Fixes

* altering the 'includeAnt' globs has no effect when removing globs until after a restart ([71c97f9](https://github.com/spmeesseman/vscode-taskexplorer/commit/71c97f9))
* ant files with an uppercase letter other than the first letter do not display with the path prepandature ([3b0d639](https://github.com/spmeesseman/vscode-taskexplorer/commit/3b0d639))
* ant task discovery is breaking async /await process ([658da17](https://github.com/spmeesseman/vscode-taskexplorer/commit/658da17))
* bild node groupings breaks async/await processing ([d784c75](https://github.com/spmeesseman/vscode-taskexplorer/commit/d784c75))
* gulfile.babel.js and gulpfile.mjs are no longer found ([a5aa7fd](https://github.com/spmeesseman/vscode-taskexplorer/commit/a5aa7fd))
* if npm.packageManager setting is 'auto', the npm icon is missing in all npm tree nodes ([a3504a0](https://github.com/spmeesseman/vscode-taskexplorer/commit/a3504a0))
* logValue does not log a false boolean value ([bf99324](https://github.com/spmeesseman/vscode-taskexplorer/commit/bf99324))
* run with no terminal still opens the terminal ([ea2fd8f](https://github.com/spmeesseman/vscode-taskexplorer/commit/ea2fd8f))
* switching between explorer and sidebar views can cause a crash in certain cases. ([f2e85cf](https://github.com/spmeesseman/vscode-taskexplorer/commit/f2e85cf))
* the 'open' button icon is missing in the sidebar view ([2a63421](https://github.com/spmeesseman/vscode-taskexplorer/commit/2a63421))
* the context menu npm commands fail if the package manager setting in Code is set to 'auto' ([0e42fd4](https://github.com/spmeesseman/vscode-taskexplorer/commit/0e42fd4))
* when modifying an ant file, the tree randomly breaks and must be refreshed manually ([9e5d0e0](https://github.com/spmeesseman/vscode-taskexplorer/commit/9e5d0e0))


### Build System

* finalize update to eslint from tslint ([52a2d93](https://github.com/spmeesseman/vscode-taskexplorer/commit/52a2d93))
* set visual tag as patch ([e169b0f](https://github.com/spmeesseman/vscode-taskexplorer/commit/e169b0f))


### Code Refactoring

* add temp handler for v2 to clean up tasks caches ([e3f030d](https://github.com/spmeesseman/vscode-taskexplorer/commit/e3f030d))
* add timestamps to logging ([8d9cf9d](https://github.com/spmeesseman/vscode-taskexplorer/commit/8d9cf9d))
* improve log readability ([291280f](https://github.com/spmeesseman/vscode-taskexplorer/commit/291280f))
* sort project folders ([e424b5b](https://github.com/spmeesseman/vscode-taskexplorer/commit/e424b5b))


### Documentation

* **readme:** add new section for v2 ([f68591c](https://github.com/spmeesseman/vscode-taskexplorer/commit/f68591c))
* **readme:** add ref to new vscode-extjs language server extension ([b0f45eb](https://github.com/spmeesseman/vscode-taskexplorer/commit/b0f45eb))
* **readme:** update 2.0 info ([5877652](https://github.com/spmeesseman/vscode-taskexplorer/commit/5877652))


### Features

* add 'clear list' action  to last tasks tree node ([06afff0](https://github.com/spmeesseman/vscode-taskexplorer/commit/06afff0))
* add favorites list ([decf2cd](https://github.com/spmeesseman/vscode-taskexplorer/commit/decf2cd))
* do all processing with async/await ([48098b4](https://github.com/spmeesseman/vscode-taskexplorer/commit/48098b4))


### Performance Improvements

* config changes for some settings refresh performance increased by 2-5x ([b146814](https://github.com/spmeesseman/vscode-taskexplorer/commit/b146814))
* major performance improvement in tree refresh when tasks start and when they complete. ([a2b271e](https://github.com/spmeesseman/vscode-taskexplorer/commit/a2b271e))
* when a watched file is modified, created, or deleted, re-ask the VSCode task engine for tasks of only the task type that the file is associated with. ([a74bfac](https://github.com/spmeesseman/vscode-taskexplorer/commit/a74bfac))


### Visual Enhancements

* new task icon ([fec8e9f](https://github.com/spmeesseman/vscode-taskexplorer/commit/fec8e9f))

## [1.30.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.30.1...v1.30.2) (2021-02-08)


### Bug Fixes

* editing a gulp files are causies its respective tree node to break. ([f4c6479](https://github.com/spmeesseman/vscode-taskexplorer/commit/f4c6479))
* grouped task labels in tree still contain the grouping parts, only the last part should display ([6117ac8](https://github.com/spmeesseman/vscode-taskexplorer/commit/6117ac8))


### Code Refactoring

* add setting to turn task label renaming on/off ([7be7488](https://github.com/spmeesseman/vscode-taskexplorer/commit/7be7488))

## [1.30.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.30.0...v1.30.1) (2021-02-08)


### Bug Fixes

* editing a package.json or tasks.json file no longer refresh the treeview with changes ([2a168a4](https://github.com/spmeesseman/vscode-taskexplorer/commit/2a168a4))


### Code Refactoring

* test semantic-release ([bd8c1f2](https://github.com/spmeesseman/vscode-taskexplorer/commit/bd8c1f2))

# [1.30.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.29.0...v1.30.0) (2021-02-08)


### Bug Fixes

* adding/modifying/deleting task files in excluded paths causes tree to refresh. [fixes [#92](https://github.com/spmeesseman/vscode-taskexplorer/issues/92)] ([1a980ce](https://github.com/spmeesseman/vscode-taskexplorer/commit/1a980ce))
* after disabling a task type in settings, modification or additions to files of that type still refresh the tree view. ([0fb783d](https://github.com/spmeesseman/vscode-taskexplorer/commit/0fb783d))
* editing a package.json or tasks.json file no longer refresh the treeview with changes ([de6ffe2](https://github.com/spmeesseman/vscode-taskexplorer/commit/de6ffe2))
* not recognizing gulpfile.mjs. [fixes [#120](https://github.com/spmeesseman/vscode-taskexplorer/issues/120)] ([8bc2cbb](https://github.com/spmeesseman/vscode-taskexplorer/commit/8bc2cbb))
* opening ant task does not find correct position if it is the default task ([62fe08c](https://github.com/spmeesseman/vscode-taskexplorer/commit/62fe08c))
* opening gulp tasks does not find correct position if not defined as gulp.task. ([fa351e1](https://github.com/spmeesseman/vscode-taskexplorer/commit/fa351e1))
* when opening a vscode/workspace task, task position is not located properly if no label property exists. ([4870016](https://github.com/spmeesseman/vscode-taskexplorer/commit/4870016))


### Build System

* **semantic-release:** fix vsce upgrade breaks vs marketplace release ([9d31d55](https://github.com/spmeesseman/vscode-taskexplorer/commit/9d31d55))
* resolve 10 dependency security vulnerabilities ([10e0283](https://github.com/spmeesseman/vscode-taskexplorer/commit/10e0283))
* update all dependecies, vsce 1.85 ([e019b30](https://github.com/spmeesseman/vscode-taskexplorer/commit/e019b30))


### Code Refactoring

* allow gradle tasks to use 'run with arguments' command. [closes [#88](https://github.com/spmeesseman/vscode-taskexplorer/issues/88)] ([8784e00](https://github.com/spmeesseman/vscode-taskexplorer/commit/8784e00))
* if 'detail' is defined on a task definition, then display it in it's representative tree item tooltip ([e0f45f6](https://github.com/spmeesseman/vscode-taskexplorer/commit/e0f45f6))


### Documentation

* **redame:** add feature images for 1.29 and 1.30 ([e773624](https://github.com/spmeesseman/vscode-taskexplorer/commit/e773624))
* **readme:** add yarn image ([54dec21](https://github.com/spmeesseman/vscode-taskexplorer/commit/54dec21))


### Features

* add 'run with arguments' and 'run with no terminal' commands to script file tasks ([c75d9aa](https://github.com/spmeesseman/vscode-taskexplorer/commit/c75d9aa))
* Add inline open task button ([1bad6d9](https://github.com/spmeesseman/vscode-taskexplorer/commit/1bad6d9))
* add new setting for default item click action. [closes [#97](https://github.com/spmeesseman/vscode-taskexplorer/issues/97)] ([c4e2ad0](https://github.com/spmeesseman/vscode-taskexplorer/commit/c4e2ad0))

# [1.30.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.29.0...v1.30.0) (2021-02-08)


### Bug Fixes

* adding/modifying/deleting task files in excluded paths causes tree to refresh. [fixes [#92](https://github.com/spmeesseman/vscode-taskexplorer/issues/92)] ([1a980ce](https://github.com/spmeesseman/vscode-taskexplorer/commit/1a980ce))
* after disabling a task type in settings, modification or additions to files of that type still refresh the tree view. ([0fb783d](https://github.com/spmeesseman/vscode-taskexplorer/commit/0fb783d))
* not recognizing gulpfile.mjs. [fixes [#120](https://github.com/spmeesseman/vscode-taskexplorer/issues/120)] ([8bc2cbb](https://github.com/spmeesseman/vscode-taskexplorer/commit/8bc2cbb))
* opening ant task does not find correct position if it is the default task ([62fe08c](https://github.com/spmeesseman/vscode-taskexplorer/commit/62fe08c))
* opening gulp tasks does not find correct position if not defined as gulp.task. ([fa351e1](https://github.com/spmeesseman/vscode-taskexplorer/commit/fa351e1))
* when opening a vscode/workspace task, task position is not located properly if no label property exists. ([4870016](https://github.com/spmeesseman/vscode-taskexplorer/commit/4870016))


### Build System

* resolve 10 dependency security vulnerabilities ([10e0283](https://github.com/spmeesseman/vscode-taskexplorer/commit/10e0283))
* update all dependecies, vsce 1.85 ([e019b30](https://github.com/spmeesseman/vscode-taskexplorer/commit/e019b30))


### Code Refactoring

* allow gradle tasks to use 'run with arguments' command. [closes [#88](https://github.com/spmeesseman/vscode-taskexplorer/issues/88)] ([8784e00](https://github.com/spmeesseman/vscode-taskexplorer/commit/8784e00))
* if 'detail' is defined on a task definition, then display it in it's representative tree item tooltip ([e0f45f6](https://github.com/spmeesseman/vscode-taskexplorer/commit/e0f45f6))


### Documentation

* **redame:** add feature images for 1.29 and 1.30 ([e773624](https://github.com/spmeesseman/vscode-taskexplorer/commit/e773624))
* **readme:** add yarn image ([54dec21](https://github.com/spmeesseman/vscode-taskexplorer/commit/54dec21))


### Features

* add 'run with arguments' and 'run with no terminal' commands to script file tasks ([c75d9aa](https://github.com/spmeesseman/vscode-taskexplorer/commit/c75d9aa))
* Add inline open task button ([1bad6d9](https://github.com/spmeesseman/vscode-taskexplorer/commit/1bad6d9))
* add new setting for default item click action. [closes [#97](https://github.com/spmeesseman/vscode-taskexplorer/issues/97)] ([c4e2ad0](https://github.com/spmeesseman/vscode-taskexplorer/commit/c4e2ad0))

# [1.29.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.28.0...v1.29.0) (2021-02-06)


### Bug Fixes

* if 'yarn is package manager set in VSCode, package.json tasks still show npm icon. [fix [#125](https://github.com/spmeesseman/vscode-taskexplorer/issues/125)] ([52acdc1](https://github.com/spmeesseman/vscode-taskexplorer/commit/52acdc1))
* problem matcher used in makefile tasks is undefined. [fixes [#123](https://github.com/spmeesseman/vscode-taskexplorer/issues/123)] ([cae79ea](https://github.com/spmeesseman/vscode-taskexplorer/commit/cae79ea))
* the context menu tasks for npm folder nodes does not run the package manager set in VSCode settings, will always use npm. [fix [#62](https://github.com/spmeesseman/vscode-taskexplorer/issues/62)] ([79695f0](https://github.com/spmeesseman/vscode-taskexplorer/commit/79695f0))
* vscode tasks - compound tasks with no 'command' property do not launch. [fixes [#130](https://github.com/spmeesseman/vscode-taskexplorer/issues/130)] ([f5a92fc](https://github.com/spmeesseman/vscode-taskexplorer/commit/f5a92fc))


### Documentation

* **readme:** update by-version features list ([97233be](https://github.com/spmeesseman/vscode-taskexplorer/commit/97233be))


### Features

* ADD option to disable auto-refresh. [closes [#124](https://github.com/spmeesseman/vscode-taskexplorer/issues/124)] ([82aa4bd](https://github.com/spmeesseman/vscode-taskexplorer/commit/82aa4bd))
* add support for 'User' tasks. [closes [#127](https://github.com/spmeesseman/vscode-taskexplorer/issues/127)] ([43f7399](https://github.com/spmeesseman/vscode-taskexplorer/commit/43f7399))
* add support for multi-level groupings (configurable level). [fix [#129](https://github.com/spmeesseman/vscode-taskexplorer/issues/129)] ([35da55e](https://github.com/spmeesseman/vscode-taskexplorer/commit/35da55e))

# [1.28.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.27.0...v1.28.0) (2021-02-05)


### Bug Fixes

* Get string instead of array ([a96f6bb](https://github.com/spmeesseman/vscode-taskexplorer/commit/a96f6bb))
* grouped tasks momre than two tree nodes deep are not appropriately renamed (by removing the grouped text from the task name). ([5e4622a](https://github.com/spmeesseman/vscode-taskexplorer/commit/5e4622a))
* if more than one package.json exists within a workspace directory, the task names do not have the 'separator paths' stripped out of the task name in the tree. [skip ci] ([99b10d7](https://github.com/spmeesseman/vscode-taskexplorer/commit/99b10d7))


### Code Refactoring

* Update to use .slice ([83121c5](https://github.com/spmeesseman/vscode-taskexplorer/commit/83121c5))


### Documentation

* Fix typos in README.md ([0e28fab](https://github.com/spmeesseman/vscode-taskexplorer/commit/0e28fab))


### Features

* Create parseTargetLine with support for Makefile aliases ([aeadb4e](https://github.com/spmeesseman/vscode-taskexplorer/commit/aeadb4e))

# [1.27.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.26.3...v1.27.0) (2020-09-27)


### Bug Fixes

* alternate name gulp files not picked up [Fixes [#73](https://github.com/spmeesseman/vscode-taskexplorer/issues/73)] ([753aae4](https://github.com/spmeesseman/vscode-taskexplorer/commit/753aae4))
* Gradle tasks not picked up from other task providers [Fixes [#113](https://github.com/spmeesseman/vscode-taskexplorer/issues/113)] ([3190242](https://github.com/spmeesseman/vscode-taskexplorer/commit/3190242))


### Code Refactoring

* default the 'group with separator' setting to true ([ab2b4c0](https://github.com/spmeesseman/vscode-taskexplorer/commit/ab2b4c0))
* modify deprecated registerTaskProvider call to use tasks namespace ([5cd0ad5](https://github.com/spmeesseman/vscode-taskexplorer/commit/5cd0ad5))
* update to latest vscode api calls ([4e69d2b](https://github.com/spmeesseman/vscode-taskexplorer/commit/4e69d2b))
* use ant itself to read tasks.  fall back to custom parser if cmd not present on system ([b3db802](https://github.com/spmeesseman/vscode-taskexplorer/commit/b3db802))
* use ant to read gulp tasks if ant is available. [References [#109](https://github.com/spmeesseman/vscode-taskexplorer/issues/109)] ([b6cd13c](https://github.com/spmeesseman/vscode-taskexplorer/commit/b6cd13c))
* use gulp to read gulp tasks if gulp is available [References [#73](https://github.com/spmeesseman/vscode-taskexplorer/issues/73)] ([434ee4e](https://github.com/spmeesseman/vscode-taskexplorer/commit/434ee4e))


### Documentation

* **readme:** add section 'Ant and Gulp Self Provided Tasks' [skip ci] ([8d9ea78](https://github.com/spmeesseman/vscode-taskexplorer/commit/8d9ea78))
* **readme:** update 1.27 feature ([ab20af5](https://github.com/spmeesseman/vscode-taskexplorer/commit/ab20af5))


### Features

* turn gulp/ant on/off to find tasks (uses cst parser when off) ([224973b](https://github.com/spmeesseman/vscode-taskexplorer/commit/224973b))

## [1.26.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.26.2...v1.26.3) (2020-03-28)


### Bug Fixes

* if tasks exist that start with a '-' character, and the 'group dashed' option is on, the tree explorer breaks ([723a86a](https://github.com/spmeesseman/vscode-taskexplorer/commit/723a86a))

## [1.26.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.26.1...v1.26.2) (2020-03-28)


### Documentation

* **readme:** add donation info and dev notes [skip-ci] ([347ae7d](https://github.com/spmeesseman/vscode-taskexplorer/commit/347ae7d))

## [1.26.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.26.0...v1.26.1) (2020-03-28)


### Bug Fixes

* gulp4 tasks in bracket notation are not picked up ([5fb9039](https://github.com/spmeesseman/vscode-taskexplorer/commit/5fb9039))
* re-enabling the 'show last tasks' option after disabling it causes an error ([f842b70](https://github.com/spmeesseman/vscode-taskexplorer/commit/f842b70))
* the 'taskExplorer.showOutput' command does not work ([ad14b14](https://github.com/spmeesseman/vscode-taskexplorer/commit/ad14b14))
* when enabling multiple task providers at the same time by editing settings.json, random task types are not initially imported ([c69de7a](https://github.com/spmeesseman/vscode-taskexplorer/commit/c69de7a))

# [1.26.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.25.1...v1.26.0) (2020-02-29)


### Bug Fixes

* the 'open terminal' button doesn't work for all tasks ([253f885](https://github.com/spmeesseman/vscode-taskexplorer/commit/253f885))


### Documentation

* **readme:** add 1.26 info, grammar fixes ([c5d05f8](https://github.com/spmeesseman/vscode-taskexplorer/commit/c5d05f8))
* **readme:** adjust ratings url in badge, add feedback link ([4687ccd](https://github.com/spmeesseman/vscode-taskexplorer/commit/4687ccd))


### Features

* add last ran running task in status bar (configurable) ([bd2de58](https://github.com/spmeesseman/vscode-taskexplorer/commit/bd2de58))

## [1.25.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.25.0...v1.25.1) (2020-02-27)


### Bug Fixes

* seemingly harmless 'element already exists' error is thrown when running a task in the 'last tasks' list ([81ffec0](https://github.com/spmeesseman/vscode-taskexplorer/commit/81ffec0))

# [1.25.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.24.4...v1.25.0) (2020-02-27)


### Bug Fixes

* new/removed cmd files are not picked up, must manually refresh ([dab6906](https://github.com/spmeesseman/vscode-taskexplorer/commit/dab6906))


### Documentation

* **reame:** update to 1.25 info ([88b55bb](https://github.com/spmeesseman/vscode-taskexplorer/commit/88b55bb))


### Features

* add support for a 'last tasks' pseudo-folder [closes [#47](https://github.com/spmeesseman/vscode-taskexplorer/issues/47)] ([10ba7f1](https://github.com/spmeesseman/vscode-taskexplorer/commit/10ba7f1))

## [1.24.4](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.24.3...v1.24.4) (2020-02-25)


### Bug Fixes

* when using the 'dashed groups' option, parenthesis or brackets in a task name breaks extension in previous release ([0d62ddc](https://github.com/spmeesseman/vscode-taskexplorer/commit/0d62ddc))

## [1.24.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.24.2...v1.24.3) (2020-02-25)


### Bug Fixes

* when using the 'dashed groups' feature, tsk names are not renamed if not all lowercase ([13ac7eb](https://github.com/spmeesseman/vscode-taskexplorer/commit/13ac7eb))

## [1.24.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.24.1...v1.24.2) (2020-02-23)


### Bug Fixes

* makefile target detection is malfunctioning - fixes [#82](https://github.com/spmeesseman/vscode-taskexplorer/issues/82) ([a3211da](https://github.com/spmeesseman/vscode-taskexplorer/commit/a3211da))


### Code Refactoring

* increase max width for status bar message ([a590f99](https://github.com/spmeesseman/vscode-taskexplorer/commit/a590f99))

## [1.24.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.24.0...v1.24.1) (2020-02-23)


### Code Refactoring

* when building the cache, the status messages cause any traling status messages to jump around too much ([ad717e7](https://github.com/spmeesseman/vscode-taskexplorer/commit/ad717e7))


### Documentation

* **readme:** update features section, remove maxage query param from github badges ([9eedc03](https://github.com/spmeesseman/vscode-taskexplorer/commit/9eedc03))

# [1.24.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.23.9...v1.24.0) (2020-02-21)


### Bug Fixes

* if logging is turned on, the output window is displayed when extension activates ([a7ace49](https://github.com/spmeesseman/vscode-taskexplorer/commit/a7ace49))


### Features

* add 'open temrinal' button for running tasks - closes [#39](https://github.com/spmeesseman/vscode-taskexplorer/issues/39) ([3b4be06](https://github.com/spmeesseman/vscode-taskexplorer/commit/3b4be06))

## [1.23.9](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.23.8...v1.23.9) (2020-02-20)


### Bug Fixes

* **gulp:** tasks defined as exports are not picked up - fixes [#41](https://github.com/spmeesseman/vscode-taskexplorer/issues/41) ([49d1ad8](https://github.com/spmeesseman/vscode-taskexplorer/commit/49d1ad8))


### Build System

* attempt fix broken vsce release ([c2c3fca](https://github.com/spmeesseman/vscode-taskexplorer/commit/c2c3fca))
* bump semantic-release-vsce to 3.0.1 - fixes broken vsce release ([5f75591](https://github.com/spmeesseman/vscode-taskexplorer/commit/5f75591))

## [1.23.8](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.23.7...v1.23.8) (2020-02-20)


### Documentation

* **readme:** update badges ([5927563](https://github.com/spmeesseman/vscode-taskexplorer/commit/5927563))

## [1.23.7](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.23.6...v1.23.7) (2020-02-19)


### Bug Fixes

* when copying and pasting multiple task files into the same folder, tasks randomly are no imported ([89534ea](https://github.com/spmeesseman/vscode-taskexplorer/commit/89534ea))

## [1.23.6](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.23.5...v1.23.6) (2020-02-18)


### Bug Fixes

* v1.23.5 is broken, receiving error 'each.removeScript is no a function' ([6ad65eb](https://github.com/spmeesseman/vscode-taskexplorer/commit/6ad65eb))


### Documentation

* **readme:** update badges with devops info ([81f1275](https://github.com/spmeesseman/vscode-taskexplorer/commit/81f1275))

## [1.23.5](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.23.4...v1.23.5) (2020-02-18)


### Bug Fixes

* app-publisher tasks 'mantis release' and 'send notification email' are mapped incorrectly and running the 're-publish' task. ([21831a4](https://github.com/spmeesseman/vscode-taskexplorer/commit/21831a4))
* when changing the default shell, some scripts will no longer run until a refresh or reload is done ([7854324](https://github.com/spmeesseman/vscode-taskexplorer/commit/7854324))

## [1.23.4](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.23.3...v1.23.4) (2020-02-18)


### Code Refactoring

* nodes created using 'dashed groupings' should be shown first under the parent node before any individual tasks are, i.e. the same behavior as that of a file explorer with files/folders ([431b456](https://github.com/spmeesseman/vscode-taskexplorer/commit/431b456))

## [1.23.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.23.2...v1.23.3) (2020-02-18)


### Bug Fixes

* removing a path from the 'includeAntPath' setting has does not remove the fswatcher until restart ([1a27d3f](https://github.com/spmeesseman/vscode-taskexplorer/commit/1a27d3f))
* when pasting multiple task files into a workspace folder, sometimes tasks do not get imported ([92b7a7b](https://github.com/spmeesseman/vscode-taskexplorer/commit/92b7a7b))


### Code Refactoring

* make addToExcludes fully async ([ff951bc](https://github.com/spmeesseman/vscode-taskexplorer/commit/ff951bc))
* make all 'enable' settings available in vscode folder settings ([2154498](https://github.com/spmeesseman/vscode-taskexplorer/commit/2154498))
* make checks on empty util.readfile ([d367895](https://github.com/spmeesseman/vscode-taskexplorer/commit/d367895))

## [1.23.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.23.1...v1.23.2) (2020-02-16)


### Bug Fixes

* when trying to start a task while the explorer is busy, error notification randomly pops up ([c7e8d1e](https://github.com/spmeesseman/vscode-taskexplorer/commit/c7e8d1e))

## [1.23.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.23.0...v1.23.1) (2020-02-14)


### Bug Fixes

* invalidation was broken in previous release - cache is rebuilt over and over ([be61019](https://github.com/spmeesseman/vscode-taskexplorer/commit/be61019))

# [1.23.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.22.3...v1.23.0) (2020-02-14)


### Bug Fixes

* run last task button no longer works ([17640bc](https://github.com/spmeesseman/vscode-taskexplorer/commit/17640bc))


### Documentation

* **readme:** add v1.23 screenshot ([afc15f0](https://github.com/spmeesseman/vscode-taskexplorer/commit/afc15f0))
* **readme:** update to version info, add section on new 'group dashed' feature. ([51b3f93](https://github.com/spmeesseman/vscode-taskexplorer/commit/51b3f93))


### Features

* add support to group task items further using dashes in the script name.  enabled by the 'groupd dashed' setting. ([3325d2e](https://github.com/spmeesseman/vscode-taskexplorer/commit/3325d2e))

## [1.22.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.22.2...v1.22.3) (2020-02-12)


### Documentation

* **readme:** update info ([8734985](https://github.com/spmeesseman/vscode-taskexplorer/commit/8734985))

## [1.22.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.22.1...v1.22.2) (2020-02-08)


### Bug Fixes

* the 'add to excludes' context menu item isn't displayed on group nodes. ([62e08ec](https://github.com/spmeesseman/vscode-taskexplorer/commit/62e08ec))

## [1.22.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.22.0...v1.22.1) (2020-02-04)


### Bug Fixes

* **open:** backslash in file path prevents open command for tasks.json when running in Linux. [fixes [#72](https://github.com/spmeesseman/vscode-taskexplorer/issues/72)] ([1ffa667](https://github.com/spmeesseman/vscode-taskexplorer/commit/1ffa667))
* the refresh button no longer works in v1.22 ([36874cc](https://github.com/spmeesseman/vscode-taskexplorer/commit/36874cc))


### Documentation

* **readme:** update 1.22 info, remove settings section ([da21b2a](https://github.com/spmeesseman/vscode-taskexplorer/commit/da21b2a))

# [1.22.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.21.0...v1.22.0) (2020-02-02)


### Build System

* **npm:** full npm dependency update ([21bf24a](https://github.com/spmeesseman/vscode-taskexplorer/commit/21bf24a))


### Code Refactoring

* kick of azure build test ([7d307f1](https://github.com/spmeesseman/vscode-taskexplorer/commit/7d307f1))


### Features

* add new app-publisher tasks: MantisRelease, PromptVersion ([7872746](https://github.com/spmeesseman/vscode-taskexplorer/commit/7872746))


### Performance Improvements

* task providers more responsive, warnings in VSCode near eliminated ([95e91a0](https://github.com/spmeesseman/vscode-taskexplorer/commit/95e91a0))

# [1.21.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.20.1...v1.21.0) (2019-11-24)


### Documentation

* **readme:** update version info [closes [#51](https://github.com/spmeesseman/vscode-taskexplorer/issues/51)] ([e6265d8](https://github.com/spmeesseman/vscode-taskexplorer/commit/e6265d8))


### Features

* add option to keep a terminal open if a task is stopped ([17debdb](https://github.com/spmeesseman/vscode-taskexplorer/commit/17debdb))
* add option to set the path to the preferred powershell program. [closes [#42](https://github.com/spmeesseman/vscode-taskexplorer/issues/42)] ([7981519](https://github.com/spmeesseman/vscode-taskexplorer/commit/7981519))
* add support for .cmd script files [closes [#44](https://github.com/spmeesseman/vscode-taskexplorer/issues/44)] ([5f5b57c](https://github.com/spmeesseman/vscode-taskexplorer/commit/5f5b57c))
* add support to mark the default task in the Ant tasks node [closes [#50](https://github.com/spmeesseman/vscode-taskexplorer/issues/50)] ([df65eea](https://github.com/spmeesseman/vscode-taskexplorer/commit/df65eea))

## [1.20.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.20.0...v1.20.1) (2019-08-21)


### Bug Fixes

* running an app-publisher task incorrectly causes all publish task icons ina ll nodes to display with the running spinner icon. ([0f1ead7](https://github.com/spmeesseman/vscode-taskexplorer/commit/0f1ead7))

# [1.20.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.19.3...v1.20.0) (2019-08-18)


### Code Refactoring

* remove unused nodejs tasks from app-publisher node ([d881cb2](https://github.com/spmeesseman/vscode-taskexplorer/commit/d881cb2))


### Documentation

* **readme:** update 1.19 info w app-publisher note [skip ci] ([55ed11b](https://github.com/spmeesseman/vscode-taskexplorer/commit/55ed11b))
* **readme:** update badges with github issues counts ([406268a](https://github.com/spmeesseman/vscode-taskexplorer/commit/406268a))


### Features

* add restart button ([c268ffd](https://github.com/spmeesseman/vscode-taskexplorer/commit/c268ffd))

## [1.19.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.19.2...v1.19.3) (2019-06-09)


### Bug Fixes

* error is shown when loading "taskdef.task.cmdLine" not defined ([4bb4583](https://github.com/spmeesseman/vscode-taskexplorer/commit/4bb4583))
* python builds are not working, too many tasks detected ([d059ae9](https://github.com/spmeesseman/vscode-taskexplorer/commit/d059ae9))

## [1.19.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.19.1...v1.19.2) (2019-06-04)


### Bug Fixes

* use npx to start app-publisher tasks (internal use only at this time) ([0f64e4c](https://github.com/spmeesseman/vscode-taskexplorer/commit/0f64e4c))

## [1.19.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.19.0...v1.19.1) (2019-06-02)


### Bug Fixes

* all app-publisher tasks always launch first task ([35f0c1c](https://github.com/spmeesseman/vscode-taskexplorer/commit/35f0c1c))
* gradle tasks without parentheses are not detected ([d76f72d](https://github.com/spmeesseman/vscode-taskexplorer/commit/d76f72d)), closes [#28](https://github.com/spmeesseman/vscode-taskexplorer/issues/28)


### Build System

* attempt fix failed publish run version mismatch ([a572a6b](https://github.com/spmeesseman/vscode-taskexplorer/commit/a572a6b))


### Documentation

* **readme:** remove some badges for less width taken ([310f21c](https://github.com/spmeesseman/vscode-taskexplorer/commit/310f21c))
* **readme:** removed untrusted app-publisher badge (untrusted vsce plugin) ([890fc81](https://github.com/spmeesseman/vscode-taskexplorer/commit/890fc81))

## [1.19.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.19.0...v1.19.1) (2019-06-02)


### Bug Fixes

* all app-publisher tasks always launch first task ([35f0c1c](https://github.com/spmeesseman/vscode-taskexplorer/commit/35f0c1c))
* gradle tasks without parentheses are not detected ([d76f72d](https://github.com/spmeesseman/vscode-taskexplorer/commit/d76f72d)), closes [#28](https://github.com/spmeesseman/vscode-taskexplorer/issues/28)


### Documentation

* **readme:** remove some badges for less width taken ([310f21c](https://github.com/spmeesseman/vscode-taskexplorer/commit/310f21c))

# [1.19.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.18.10...v1.19.0) (2019-05-27)


### Features

* add support for app-publisher tasks for upcoming app-publisher release ([be2713c](https://github.com/spmeesseman/vscode-taskexplorer/commit/be2713c))

## [1.18.10](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.18.9...v1.18.10) (2019-05-18)


### Documentation

* **readme:** add toc ([fcdd8ff](https://github.com/spmeesseman/vscode-taskexplorer/commit/fcdd8ff))

## [1.18.9](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.18.8...v1.18.9) (2019-05-15)


### Bug Fixes

* running a task shows spinner icon for tasks with same name under different task nodes ([97877a0](https://github.com/spmeesseman/vscode-taskexplorer/commit/97877a0))


### Build System

* **npm:** package.json cleanup [skip ci] ([03567d2](https://github.com/spmeesseman/vscode-taskexplorer/commit/03567d2))
* **npm:** re-add bugs and homepage properties ([260d837](https://github.com/spmeesseman/vscode-taskexplorer/commit/260d837))


### Documentation

* **todo:** update features todo [skip ci] ([39b7355](https://github.com/spmeesseman/vscode-taskexplorer/commit/39b7355))
* **todo:** update features todo [skip ci] ([525363a](https://github.com/spmeesseman/vscode-taskexplorer/commit/525363a))
* **todo:** update todo list ([f427a5a](https://github.com/spmeesseman/vscode-taskexplorer/commit/f427a5a))

## [1.18.8](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.18.7...v1.18.8) (2019-05-04)


### Bug Fixes

* running npm update package from npm task node fails with invalid command ([fb1ea1e](https://github.com/spmeesseman/vscode-taskexplorer/commit/fb1ea1e))

## [1.18.7](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.18.6...v1.18.7) (2019-05-02)


### Bug Fixes

* only lowercase task file names are auto-refreshing the tree when edited ([378b5cd](https://github.com/spmeesseman/vscode-taskexplorer/commit/378b5cd))
* view is refreshing every time it is made visible even when it does not need to ([cbb5d6a](https://github.com/spmeesseman/vscode-taskexplorer/commit/cbb5d6a))


### Documentation

* **todo:** update features list [skip ci] ([e34e6c2](https://github.com/spmeesseman/vscode-taskexplorer/commit/e34e6c2))

## [1.18.6](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.18.5...v1.18.6) (2019-05-01)


### Bug Fixes

* tsc task file nodes show path with missing last character ([5062da9](https://github.com/spmeesseman/vscode-taskexplorer/commit/5062da9))


### Documentation

* **readme:** remove builds info ([af00ea4](https://github.com/spmeesseman/vscode-taskexplorer/commit/af00ea4))
* **readme:** update thanks section for nsis icons ([4f9e9c8](https://github.com/spmeesseman/vscode-taskexplorer/commit/4f9e9c8))


### Minor Features

* update nsis tree icon to nsis logo ([b9dafbd](https://github.com/spmeesseman/vscode-taskexplorer/commit/b9dafbd))

## [1.18.5](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.18.4...v1.18.5) (2019-04-30)


### Bug Fixes

* do not use shift as keybinding start ([a086dc3](https://github.com/spmeesseman/vscode-taskexplorer/commit/a086dc3))

## [1.18.4](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.18.3...v1.18.4) (2019-04-30)


### Bug Fixes

* removing exclude globs manually in settings.json has no effect on explorer tree until next refresh. Works in sidebar tree. ([ef27223](https://github.com/spmeesseman/vscode-taskexplorer/commit/ef27223))


### Documentation

* **todo:** add refactoring ([45aff9d](https://github.com/spmeesseman/vscode-taskexplorer/commit/45aff9d))


### Minor Features

* add key binding for "run last task" - shift+r t ([c8c0ca9](https://github.com/spmeesseman/vscode-taskexplorer/commit/c8c0ca9))
* prompt for confirmation when adding a file to excluded tasks list. ([5747829](https://github.com/spmeesseman/vscode-taskexplorer/commit/5747829))

## [1.18.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.18.2...v1.18.3) (2019-04-29)


### Bug Fixes

* regression - powershell scripts no longer work, are bing ran as perl scripts ([99a06d0](https://github.com/spmeesseman/vscode-taskexplorer/commit/99a06d0))
* util function exception on empty last tasks array ([27a5ddd](https://github.com/spmeesseman/vscode-taskexplorer/commit/27a5ddd))


### Code Refactoring

* use extenison storage instead of user settings for saving last tasks. ([375c42b](https://github.com/spmeesseman/vscode-taskexplorer/commit/375c42b))


### Documentation

* **readme:** update builds section ([0a61b2b](https://github.com/spmeesseman/vscode-taskexplorer/commit/0a61b2b))

## [1.18.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.18.1...v1.18.2) (2019-04-29)


### Bug Fixes

* changing the pathToBash setting has no effect until next tree refresh ([e300af1](https://github.com/spmeesseman/vscode-taskexplorer/commit/e300af1))
* edit/save a gradle task file does not auto refresh tree ([b716f7b](https://github.com/spmeesseman/vscode-taskexplorer/commit/b716f7b))
* saving a bash/sh file causes tree to auto-refresh (script type tasks should not) ([314ab30](https://github.com/spmeesseman/vscode-taskexplorer/commit/314ab30))


### Documentation

* **todo:** update fixed known bugs ([7de81f6](https://github.com/spmeesseman/vscode-taskexplorer/commit/7de81f6))

## [1.18.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.18.0...v1.18.1) (2019-04-28)


### Bug Fixes

* add to excludes command is displayed twice in Explorer file node context menus ([2318d00](https://github.com/spmeesseman/vscode-taskexplorer/commit/2318d00))
* executing a batch script with an argument causes task to disappear from tree ([f0efeee](https://github.com/spmeesseman/vscode-taskexplorer/commit/f0efeee))


### Code Refactoring

* modify settings descriptions ([8152334](https://github.com/spmeesseman/vscode-taskexplorer/commit/8152334))


### Documentation

* **todo:** update known bugs ([d694dd7](https://github.com/spmeesseman/vscode-taskexplorer/commit/d694dd7))
* **todo:** update known bugs @ 1.18 ([468e881](https://github.com/spmeesseman/vscode-taskexplorer/commit/468e881))

# [1.18.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.17.0...v1.18.0) (2019-04-28)


### Bug Fixes

* bash script tasks do not work in windows ([184ace2](https://github.com/spmeesseman/vscode-taskexplorer/commit/184ace2))
* save configuration values to user settings not workspace ([d9ca51e](https://github.com/spmeesseman/vscode-taskexplorer/commit/d9ca51e))


### Code Refactoring

* add user setting taskExplorer.pathToBash ([2263b4f](https://github.com/spmeesseman/vscode-taskexplorer/commit/2263b4f))


### Documentation

* **readme:** update to 1.17 info ([9c36bad](https://github.com/spmeesseman/vscode-taskexplorer/commit/9c36bad))
* update to 1.18 info ([c60a2ad](https://github.com/spmeesseman/vscode-taskexplorer/commit/c60a2ad))
* **readme:** update with bash in wnidows info ([32ca416](https://github.com/spmeesseman/vscode-taskexplorer/commit/32ca416))


### Features

* add an "add to excludes" action to task file nodes ([aa4ebdb](https://github.com/spmeesseman/vscode-taskexplorer/commit/aa4ebdb))

# [1.17.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.16.0...v1.17.0) (2019-04-27)


### Bug Fixes

* regression - open and refresh commands no longer work ([00a7d10](https://github.com/spmeesseman/vscode-taskexplorer/commit/00a7d10))


### Features

* add "run last task" button to titlebar ([4b445de](https://github.com/spmeesseman/vscode-taskexplorer/commit/4b445de))

# [1.16.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.15.9...v1.16.0) (2019-04-27)


### Features

* add additional npm commands in npm file node context menu ([0a2b7b1](https://github.com/spmeesseman/vscode-taskexplorer/commit/0a2b7b1))

## [1.15.9](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.15.8...v1.15.9) (2019-04-26)


### Bug Fixes

* changing a "path to" setting does not take effect until vscode restarts ([c09b157](https://github.com/spmeesseman/vscode-taskexplorer/commit/c09b157))
* tree is not auto refreshing after saving certain settings (regression) ([9396bc9](https://github.com/spmeesseman/vscode-taskexplorer/commit/9396bc9))


### Documentation

* **todo:** update features list ([d00c459](https://github.com/spmeesseman/vscode-taskexplorer/commit/d00c459))
* **eradme:** update requirements and task provider info ([428ce1e](https://github.com/spmeesseman/vscode-taskexplorer/commit/428ce1e))

## [1.15.8](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.15.7...v1.15.8) (2019-04-25)


### Bug Fixes

* renaming a task file doesnt remove old node in tree on auto-refresh ([92d6d8d](https://github.com/spmeesseman/vscode-taskexplorer/commit/92d6d8d))


### Code Refactoring

* log file watcher events [skip ci] ([04de746](https://github.com/spmeesseman/vscode-taskexplorer/commit/04de746))


### Documentation

* **todo:** update known bugs [skip ci] ([b7027f9](https://github.com/spmeesseman/vscode-taskexplorer/commit/b7027f9))
* **todo:** update known bugs [skip ci] ([7e84efe](https://github.com/spmeesseman/vscode-taskexplorer/commit/7e84efe))

## [1.15.7](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.15.6...v1.15.7) (2019-04-24)


### Bug Fixes

* add/remove/edit ant files defined in includeAnt setting does not show in tree correctly after auto-refresh ([34da3ea](https://github.com/spmeesseman/vscode-taskexplorer/commit/34da3ea))
* editing a non-script type task file results in duplicate task nodes in tree after saving ([0d77a00](https://github.com/spmeesseman/vscode-taskexplorer/commit/0d77a00))


### Documentation

* **todo:** update [skip ci] ([6e1412c](https://github.com/spmeesseman/vscode-taskexplorer/commit/6e1412c))
* **todo:** update to current date ([b442837](https://github.com/spmeesseman/vscode-taskexplorer/commit/b442837))

## [1.15.6](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.15.5...v1.15.6) (2019-04-23)


### Bug Fixes

* if the view is changed while a task runs and finishes, the status icon of that task gets stuck at loading ([a290d01](https://github.com/spmeesseman/vscode-taskexplorer/commit/a290d01))

## [1.15.5](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.15.4...v1.15.5) (2019-04-22)


### Bug Fixes

* deleting a task file and exiting vscode before tree finishes refreshing throws exception ([0b09e4c](https://github.com/spmeesseman/vscode-taskexplorer/commit/0b09e4c))
* gradle files with upperacse extensions are not found ([9b622dd](https://github.com/spmeesseman/vscode-taskexplorer/commit/9b622dd))
* new batch file creation does not display in task tree after auto-refresh ([422ff51](https://github.com/spmeesseman/vscode-taskexplorer/commit/422ff51))

## [1.15.4](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.15.3...v1.15.4) (2019-04-13)


### Bug Fixes

* final file blacklist to decrease size of extension ([4431b43](https://github.com/spmeesseman/vscode-taskexplorer/commit/4431b43))

## [1.15.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.15.2...v1.15.3) (2019-04-13)


### Bug Fixes

* build included non-included not needed files ([4cb2423](https://github.com/spmeesseman/vscode-taskexplorer/commit/4cb2423))


### Build System

* complete ignore list from extension build ([f47e395](https://github.com/spmeesseman/vscode-taskexplorer/commit/f47e395))

## [1.15.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.15.1...v1.15.2) (2019-04-13)


### Documentation

* **readme:**  style/refresh info post 1.15 reelease ([e818c29](https://github.com/spmeesseman/vscode-taskexplorer/commit/e818c29))

## [1.15.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.15.0...v1.15.1) (2019-04-13)


### Documentation

* **readme:** update build by me section ([9ed6d91](https://github.com/spmeesseman/vscode-taskexplorer/commit/9ed6d91))
* **readme:** update info, more detail on vscode provided tasks and ant includes [skip ci] ([0b531ba](https://github.com/spmeesseman/vscode-taskexplorer/commit/0b531ba))
* **todo:** update post 1.15 [skip ci] ([43fc8ee](https://github.com/spmeesseman/vscode-taskexplorer/commit/43fc8ee))
* **license:** update to mit [skip ci] ([d80340f](https://github.com/spmeesseman/vscode-taskexplorer/commit/d80340f))

# [1.15.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.14.9...v1.15.0) (2019-04-13)


### Bug Fixes

* editing package.json file throws exception in scriptProvider (introduced 1.14.7) ([1379a74](https://github.com/spmeesseman/vscode-taskexplorer/commit/1379a74))


### Build System

* **npm:** update to gradle support ([0d15e1a](https://github.com/spmeesseman/vscode-taskexplorer/commit/0d15e1a))


### Code Refactoring

* add setting for path to gradle program ([ebb24e5](https://github.com/spmeesseman/vscode-taskexplorer/commit/ebb24e5))
* change bash script icon color to green ([7f35369](https://github.com/spmeesseman/vscode-taskexplorer/commit/7f35369))
* need to tweak taskFile properties again. ([6b9aac5](https://github.com/spmeesseman/vscode-taskexplorer/commit/6b9aac5))
* post merge touch gradle task provider with latest provider fixes ([1abff6f](https://github.com/spmeesseman/vscode-taskexplorer/commit/1abff6f))


### Documentation

* **readme:** fix typo in v1.15 feature note ([27c8f85](https://github.com/spmeesseman/vscode-taskexplorer/commit/27c8f85))
* **todo:** mark gradle support complete ([815c4f3](https://github.com/spmeesseman/vscode-taskexplorer/commit/815c4f3))
* **readme:** post merge update ([db2d6c1](https://github.com/spmeesseman/vscode-taskexplorer/commit/db2d6c1))
* **todo:** update ([a4bc7b0](https://github.com/spmeesseman/vscode-taskexplorer/commit/a4bc7b0))
* **readme:** update all task type icons in header row ([32b3bf7](https://github.com/spmeesseman/vscode-taskexplorer/commit/32b3bf7))
* **readme:** update grunt and nsis task type icons ([0c878d9](https://github.com/spmeesseman/vscode-taskexplorer/commit/0c878d9))
* **eadme:** update marketplace icon smoother edges ([630d689](https://github.com/spmeesseman/vscode-taskexplorer/commit/630d689))
* **readme:** update material icon theme info to credits ([58776e6](https://github.com/spmeesseman/vscode-taskexplorer/commit/58776e6))
* **readme:** update non transparent task type icons to show nice in dark theme ([da541ac](https://github.com/spmeesseman/vscode-taskexplorer/commit/da541ac))
* **todo:** update to v1.15 icon update info ([33a7ea8](https://github.com/spmeesseman/vscode-taskexplorer/commit/33a7ea8))
* **readme:** update to v1.15 info ([2dcdb31](https://github.com/spmeesseman/vscode-taskexplorer/commit/2dcdb31))
* **readme:** update to v1.15 info ([30441d7](https://github.com/spmeesseman/vscode-taskexplorer/commit/30441d7))


### Features

* add gradle support ([a8c1dc6](https://github.com/spmeesseman/vscode-taskexplorer/commit/a8c1dc6)), closes [#15](https://github.com/spmeesseman/vscode-taskexplorer/issues/15)
* display tree icons for all task types even if no icon theme is installed ([84ecabb](https://github.com/spmeesseman/vscode-taskexplorer/commit/84ecabb))
* support for gradle tasks ([bed6021](https://github.com/spmeesseman/vscode-taskexplorer/commit/bed6021))


### Performance Improvements

* reduce tree/icon refresh time when starting/stopping task. ([15b2823](https://github.com/spmeesseman/vscode-taskexplorer/commit/15b2823))

## [1.14.9](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.14.8...v1.14.9) (2019-04-12)


### Bug Fixes

* tasks found in root gulpfile run first task regardless of the specific task desired. ([17e796b](https://github.com/spmeesseman/vscode-taskexplorer/commit/17e796b)), closes [#19](https://github.com/spmeesseman/vscode-taskexplorer/issues/19)


### Build System

* **npm:** update security vulnerablities.  manual changes needed for tar vulnerability. ([e57944c](https://github.com/spmeesseman/vscode-taskexplorer/commit/e57944c))


### Code Refactoring

* remove resourcUri property from group nodes, use toolip "TaskType Task Files" ([37e4bf1](https://github.com/spmeesseman/vscode-taskexplorer/commit/37e4bf1))


### Documentation

* **readme:** add mention of the todo list extension ([69704ed](https://github.com/spmeesseman/vscode-taskexplorer/commit/69704ed))
* **todo:** update [skip ci] ([e2801a1](https://github.com/spmeesseman/vscode-taskexplorer/commit/e2801a1))

## [1.14.8](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.14.7...v1.14.8) (2019-04-12)


### Bug Fixes

* saving a gulp/gruntfile causes an extra task group node to appear in tree ([452ec79](https://github.com/spmeesseman/vscode-taskexplorer/commit/452ec79)), closes [#20](https://github.com/spmeesseman/vscode-taskexplorer/issues/20)


### Build System

* **semantic-release:** add extra keywords for commit analyzer and notes generator ([1f45e37](https://github.com/spmeesseman/vscode-taskexplorer/commit/1f45e37))


### Documentation

* **todo:** update ([44f7259](https://github.com/spmeesseman/vscode-taskexplorer/commit/44f7259))

## [1.14.7](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.14.6...v1.14.7) (2019-04-12)


### Bug Fixes

* stop processing a views events if it was turned off in settings ([aed18ac](https://github.com/spmeesseman/vscode-taskexplorer/commit/aed18ac))
* task nodes within a task type group in the tree are not alphabetized correctly ([a9d66ff](https://github.com/spmeesseman/vscode-taskexplorer/commit/a9d66ff))
* task tree does not auto refresh when nsis files are created/edited ([a316843](https://github.com/spmeesseman/vscode-taskexplorer/commit/a316843))
* when a script type task is edited (batch, bash, perl, etc), do not refresh the tree ui ([f40e970](https://github.com/spmeesseman/vscode-taskexplorer/commit/f40e970))


### Performance Improvements

* reduce tree refresh time by 20-40% after editing a task file ([1f1e054](https://github.com/spmeesseman/vscode-taskexplorer/commit/1f1e054))

## [1.14.6](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.14.5...v1.14.6) (2019-04-12)


### Performance Improvements

* after edit a task file, invalidate only that task tree node ([554394b](https://github.com/spmeesseman/vscode-taskexplorer/commit/554394b))

## [1.14.5](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.14.4...v1.14.5) (2019-04-12)


### Bug Fixes

* (1) grunt and gulp tasks found in subdirectories of the project root throw an error when ran, (2) tasks whose name occurs on a newline are not found ([1f04979](https://github.com/spmeesseman/vscode-taskexplorer/commit/1f04979))
* gruntfiles and gulpfiles that are not all lowercase are not found ([b9e397d](https://github.com/spmeesseman/vscode-taskexplorer/commit/b9e397d))
* makefile target parsing fails if a target name exists elsewhere in the file ([f7fb40d](https://github.com/spmeesseman/vscode-taskexplorer/commit/f7fb40d))
* running an nsis task uses nsis.exe, should use makensis.exe ([f1598d4](https://github.com/spmeesseman/vscode-taskexplorer/commit/f1598d4))

## [1.14.4](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.14.3...v1.14.4) (2019-04-12)


### Bug Fixes

* running a composite task (no shell) displays loading icon and stop icon, and is stuck in that state. ([d346c09](https://github.com/spmeesseman/vscode-taskexplorer/commit/d346c09))
* starting and stopping a task is invalidating the tree before refreshing. ([32abff3](https://github.com/spmeesseman/vscode-taskexplorer/commit/32abff3))

## [1.14.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.14.2...v1.14.3) (2019-04-07)


### Bug Fixes

* exclude globs have no effect on typescript tasks in subfolders ([75bcbda](https://github.com/spmeesseman/vscode-taskexplorer/commit/75bcbda))
* grouped nodes have a tooltip of one of the task files within ([6d02dd5](https://github.com/spmeesseman/vscode-taskexplorer/commit/6d02dd5))

## [1.14.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.14.1...v1.14.2) (2019-04-07)


### Bug Fixes

* gulp and grunt tasks in subdirs display incorrect task name. ([3d3f5bd](https://github.com/spmeesseman/vscode-taskexplorer/commit/3d3f5bd))
* refreshing task tree does not pick up new task files ([289c110](https://github.com/spmeesseman/vscode-taskexplorer/commit/289c110))

## [1.14.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.14.0...v1.14.1) (2019-04-07)


### Bug Fixes

* changing debug level in settings does not affect log output ([ce660bd](https://github.com/spmeesseman/vscode-taskexplorer/commit/ce660bd))
* nsis type tasks are not found unless the idleberg.nsis extension is installed ([c2c36ef](https://github.com/spmeesseman/vscode-taskexplorer/commit/c2c36ef))


### Code Refactoring

* double check exclsuion after finding scripts - vscode findFiles is case sensitive glabs ([cb0c5f5](https://github.com/spmeesseman/vscode-taskexplorer/commit/cb0c5f5))


### Documentation

* **todo:** update completed tasks, add gradle task support ([3154e5b](https://github.com/spmeesseman/vscode-taskexplorer/commit/3154e5b))
* **readme:** update screenshots ([af5232a](https://github.com/spmeesseman/vscode-taskexplorer/commit/af5232a))


### Performance Improvements

* apply excludes glob list to the underlying  file search for faster tree loading. ([87588a5](https://github.com/spmeesseman/vscode-taskexplorer/commit/87588a5))

# [1.14.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.13.3...v1.14.0) (2019-04-07)


### Documentation

* **todo:** rename todo file to . convention [skip ci] ([6324dea](https://github.com/spmeesseman/vscode-taskexplorer/commit/6324dea))
* **todo:** update 1.14 finished tasks ([e938d32](https://github.com/spmeesseman/vscode-taskexplorer/commit/e938d32))
* **readme:** update screenshots ([2dd81e0](https://github.com/spmeesseman/vscode-taskexplorer/commit/2dd81e0))
* **readme:** update v1.14 info ([8c69e32](https://github.com/spmeesseman/vscode-taskexplorer/commit/8c69e32))


### Features

* add support for grunt and gulp files not located in project root ([ced2462](https://github.com/spmeesseman/vscode-taskexplorer/commit/ced2462))

## [1.13.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.13.2...v1.13.3) (2019-04-06)


### Bug Fixes

* task tree does not auto refresh when enabling/disabling certain task types in settings ([256df86](https://github.com/spmeesseman/vscode-taskexplorer/commit/256df86))
* task tree doesnt refresh after editing a task file for most task types ([64208a2](https://github.com/spmeesseman/vscode-taskexplorer/commit/64208a2))
* tree refreshes multiple times when settings change ([2fdd0ea](https://github.com/spmeesseman/vscode-taskexplorer/commit/2fdd0ea))


### Documentation

* **todo:** update ([a80380f](https://github.com/spmeesseman/vscode-taskexplorer/commit/a80380f))
* **todo:** update info ([e578f6d](https://github.com/spmeesseman/vscode-taskexplorer/commit/e578f6d))
* **todo:** updated info ([abfee5f](https://github.com/spmeesseman/vscode-taskexplorer/commit/abfee5f))

## [1.13.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.13.1...v1.13.2) (2019-04-06)


### Bug Fixes

* cant run install command on npm nodes that are not in the project root ([2b0c091](https://github.com/spmeesseman/vscode-taskexplorer/commit/2b0c091))


### Code Refactoring

* include deactivate() implementation in extension ([e5aed57](https://github.com/spmeesseman/vscode-taskexplorer/commit/e5aed57))


### Documentation

* **readme:** fix screenshot table layout ([3ef94e7](https://github.com/spmeesseman/vscode-taskexplorer/commit/3ef94e7))

## [1.13.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.13.0...v1.13.1) (2019-04-06)


### Bug Fixes

* node icon for ant tasks is not centered ([532f4e8](https://github.com/spmeesseman/vscode-taskexplorer/commit/532f4e8))


### Build System

* **conventional-changelog-spm:** update to 1.1.4 ([7a1ee94](https://github.com/spmeesseman/vscode-taskexplorer/commit/7a1ee94))


### Documentation

* **todo:** update [skip ci] ([e7b9933](https://github.com/spmeesseman/vscode-taskexplorer/commit/e7b9933))
* **readme:** update 1.13 info, add note about icon set ([92be78c](https://github.com/spmeesseman/vscode-taskexplorer/commit/92be78c))
* **readme:** update screenshots ([09b7f1f](https://github.com/spmeesseman/vscode-taskexplorer/commit/09b7f1f))


### Minor Features

* add "Open [taskname]" tooltip when hover over task nodes ([7ebe446](https://github.com/spmeesseman/vscode-taskexplorer/commit/7ebe446))

# [1.13.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.12.6...v1.13.0) (2019-04-06)


### Bug Fixes

* multi-root groupings not working for some tasks after feature merge ([a721e66](https://github.com/spmeesseman/vscode-taskexplorer/commit/a721e66))


### Documentation

* **todo:** update [skip ci] ([78125ee](https://github.com/spmeesseman/vscode-taskexplorer/commit/78125ee))
* **todo:** update [skip ci] ([ba4669e](https://github.com/spmeesseman/vscode-taskexplorer/commit/ba4669e))
* **todo:** update [skip ci] ([0a422b1](https://github.com/spmeesseman/vscode-taskexplorer/commit/0a422b1))


### Features

* add taskfile group nodes ([53ac139](https://github.com/spmeesseman/vscode-taskexplorer/commit/53ac139))

## [1.12.6](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.12.5...v1.12.6) (2019-04-06)


### Bug Fixes

* make glob pattern excludes case insensitive ([4104252](https://github.com/spmeesseman/vscode-taskexplorer/commit/4104252))


### Documentation

* **readme:** update info and default path excludes [skip ci] ([e88471f](https://github.com/spmeesseman/vscode-taskexplorer/commit/e88471f))

## [1.12.5](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.12.4...v1.12.5) (2019-04-06)


### Bug Fixes

* **settings:** fix blank label ([e0d34d4](https://github.com/spmeesseman/vscode-taskexplorer/commit/e0d34d4))


### Code Refactoring

* lighten ant icon in file nodes to gray ([1ea196d](https://github.com/spmeesseman/vscode-taskexplorer/commit/1ea196d))
* sort task file nodes by task source ([a39dbf2](https://github.com/spmeesseman/vscode-taskexplorer/commit/a39dbf2))


### Documentation

* **readme:** reorder badges, place gk badge next to dep status badges ([de16924](https://github.com/spmeesseman/vscode-taskexplorer/commit/de16924))
* **todo:** update info ([a91d283](https://github.com/spmeesseman/vscode-taskexplorer/commit/a91d283))

## [1.12.4](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.12.3...v1.12.4) (2019-04-06)


### Documentation

* **readme:** fixed todo link ([a26bc4c](https://github.com/spmeesseman/vscode-taskexplorer/commit/a26bc4c))

## [1.12.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.12.2...v1.12.3) (2019-04-05)


### Bug Fixes

* add settings for specifying script intepreter location ([cda2c2e](https://github.com/spmeesseman/vscode-taskexplorer/commit/cda2c2e))


### Code Refactoring

* update todo ([735da5e](https://github.com/spmeesseman/vscode-taskexplorer/commit/735da5e))


### Documentation

* **readme:**  add link to todos ([5d39799](https://github.com/spmeesseman/vscode-taskexplorer/commit/5d39799))

## [1.12.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.12.1...v1.12.2) (2019-04-05)


### Bug Fixes

* task file labels still show uppercase letters ([4e91243](https://github.com/spmeesseman/vscode-taskexplorer/commit/4e91243))


### Build System

* **npm:** bump min version conventional-changelog-spm to 1.1.2 ([d081678](https://github.com/spmeesseman/vscode-taskexplorer/commit/d081678))
* **npm:** bump min version of conventional-changelog-spm to 1.1.3 ([7794095](https://github.com/spmeesseman/vscode-taskexplorer/commit/7794095))


### Documentation

* **readme:** add new settings descriptions ([3f46d5f](https://github.com/spmeesseman/vscode-taskexplorer/commit/3f46d5f))

## [1.12.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.12.0...v1.12.1) (2019-04-05)


### Build System

* **npm:** add dev dependency conventional-changelog-spm ([fd35851](https://github.com/spmeesseman/vscode-taskexplorer/commit/fd35851))
* **semantic-release:** cleanup config file ([23673d1](https://github.com/spmeesseman/vscode-taskexplorer/commit/23673d1))
* **semantic-release:** use separate releaserc.json config ([cb93891](https://github.com/spmeesseman/vscode-taskexplorer/commit/cb93891))
* **semantic-release:** use spm custom changelog preset ([a58a6c7](https://github.com/spmeesseman/vscode-taskexplorer/commit/a58a6c7))


### Code Refactoring

* lowercase file item labels ([6a1a86b](https://github.com/spmeesseman/vscode-taskexplorer/commit/6a1a86b))


### Documentation

* **readme:** update coming soon and test check in name [skip ci] ([5d4432b](https://github.com/spmeesseman/vscode-taskexplorer/commit/5d4432b))
* **readme:** update coming soon, test checkin username [skip ci] ([843e329](https://github.com/spmeesseman/vscode-taskexplorer/commit/843e329))

# [1.12.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.11.2...v1.12.0) (2019-04-05)


### Features

* add support for bash, python, perl, powershell, nsis, and ruby scripts ([17244d1](https://github.com/spmeesseman/vscode-taskexplorer/commit/17244d1))

## [1.11.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.11.1...v1.11.2) (2019-04-05)


### Bug Fixes

* make run install command from npm node asynchronous ([eb52c7e](https://github.com/spmeesseman/vscode-taskexplorer/commit/eb52c7e))
* run install command does not work in npm file node context menu ([a9895b3](https://github.com/spmeesseman/vscode-taskexplorer/commit/a9895b3))

## [1.11.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.11.0...v1.11.1) (2019-04-05)

# [1.11.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.10.0...v1.11.0) (2019-04-05)


### Features

* add support for batch scripts ([24b1bbb](https://github.com/spmeesseman/vscode-taskexplorer/commit/24b1bbb))
* auto prompt for script cmd line args ([7f99598](https://github.com/spmeesseman/vscode-taskexplorer/commit/7f99598))

# [1.10.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.9.3...v1.10.0) (2019-04-04)


### Bug Fixes

* register run install command for npm ([02d04b9](https://github.com/spmeesseman/vscode-taskexplorer/commit/02d04b9))
* run install command should be only for npm file nodes ([b1938e8](https://github.com/spmeesseman/vscode-taskexplorer/commit/b1938e8))
* wordage in settings for show view type ([acb3ea2](https://github.com/spmeesseman/vscode-taskexplorer/commit/acb3ea2))


### Features

* add support for makefile targets as tasks ([b75dbd5](https://github.com/spmeesseman/vscode-taskexplorer/commit/b75dbd5))

## [1.9.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.9.2...v1.9.3) (2019-04-04)


### Bug Fixes

* 'open' grunt tasks does not position cursor on task properly ([7a5a474](https://github.com/spmeesseman/vscode-taskexplorer/commit/7a5a474))
* enable/disable script types in settings has no effect ([02c08d2](https://github.com/spmeesseman/vscode-taskexplorer/commit/02c08d2))
* util camelcase fn returns invalud value ([2da68e9](https://github.com/spmeesseman/vscode-taskexplorer/commit/2da68e9))

## [1.9.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.9.1...v1.9.2) (2019-04-03)


### Bug Fixes

* task names with a dash surrounded by spaces ( - ) are being cut off in display ([4d72df7](https://github.com/spmeesseman/vscode-taskexplorer/commit/4d72df7))

## [1.9.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.9.0...v1.9.1) (2019-04-03)


### Bug Fixes

* exclude paths are working on some paths but not on others ([5dc7691](https://github.com/spmeesseman/vscode-taskexplorer/commit/5dc7691))
* tsc each task name displays relative path instead of file node ([757e4cb](https://github.com/spmeesseman/vscode-taskexplorer/commit/757e4cb))

# [1.9.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.8.0...v1.9.0) (2019-04-03)


### Bug Fixes

* for ant files display file name on task file node if not named build.xml ([70d773f](https://github.com/spmeesseman/vscode-taskexplorer/commit/70d773f))
* logValue for output window doesnt log empty string ([421bfd6](https://github.com/spmeesseman/vscode-taskexplorer/commit/421bfd6))
* task file cannot be found when opening if filename is not all lowercase ([9672798](https://github.com/spmeesseman/vscode-taskexplorer/commit/9672798))


### Features

* gulp task detection support ([5f05830](https://github.com/spmeesseman/vscode-taskexplorer/commit/5f05830))

# [1.8.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.7.8...v1.8.0) (2019-04-02)


### Bug Fixes

* empty file labeled as an ant file causes extension to stop working after parsing ([2051532](https://github.com/spmeesseman/vscode-taskexplorer/commit/2051532))
* make exclude setting non-resource type ([7cb2740](https://github.com/spmeesseman/vscode-taskexplorer/commit/7cb2740))


### Features

* add new setting to parse ant files not named B/build.xml ([4253452](https://github.com/spmeesseman/vscode-taskexplorer/commit/4253452))

## [1.7.8](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.7.7...v1.7.8) (2019-04-01)


### Bug Fixes

* ansicon for ant output colorization ([acf17fc](https://github.com/spmeesseman/vscode-taskexplorer/commit/acf17fc))
* vscode tasks of type 'npm' are not found when ran ([1b4ca1d](https://github.com/spmeesseman/vscode-taskexplorer/commit/1b4ca1d))


### Performance Improvements

* remove command lookups for tooltips in npm scripts for faster loading time in large workspaces ([77edcc4](https://github.com/spmeesseman/vscode-taskexplorer/commit/77edcc4))

## [1.7.7](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.7.6...v1.7.7) (2019-04-01)


### Bug Fixes

* extension stops working after reading an Ant build file with no targets ([76a0593](https://github.com/spmeesseman/vscode-taskexplorer/commit/76a0593))

## [1.7.6](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.7.5...v1.7.6) (2019-03-31)


### Bug Fixes

* change package icon color ([0ed4bea](https://github.com/spmeesseman/vscode-taskexplorer/commit/0ed4bea))

## [1.7.5](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.7.4...v1.7.5) (2019-03-30)


### Bug Fixes

* call destroyAllTempPath breaks promise if there are no temp dirs ([cd4e711](https://github.com/spmeesseman/vscode-taskexplorer/commit/cd4e711))
* refresh button in sidebar is missing ([0cbb946](https://github.com/spmeesseman/vscode-taskexplorer/commit/0cbb946))


### Performance Improvements

* remove jsonprovider requests to npmjs ([db037df](https://github.com/spmeesseman/vscode-taskexplorer/commit/db037df))

## [1.7.4](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.7.3...v1.7.4) (2019-03-30)

## [1.7.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.7.2...v1.7.3) (2019-03-30)

## [1.7.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.7.1...v1.7.2) (2019-03-30)

## [1.7.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.7.0...v1.7.1) (2019-03-30)


### Bug Fixes

* double text in sidebar view title ([436a826](https://github.com/spmeesseman/vscode-taskexplorer/commit/436a826))

# [1.7.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.6.0...v1.7.0) (2019-03-30)


### Features

* add sidebar view ([2595a39](https://github.com/spmeesseman/vscode-taskexplorer/commit/2595a39))

# [1.6.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.21...v1.6.0) (2019-03-30)


### Features

* display status for running task, stop running tasks ([4cf8af9](https://github.com/spmeesseman/vscode-taskexplorer/commit/4cf8af9))


### Performance Improvements

* make logging asynchronous ([c080a3d](https://github.com/spmeesseman/vscode-taskexplorer/commit/c080a3d))

## [1.5.21](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.20...v1.5.21) (2019-03-29)

## [1.5.20](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.19...v1.5.20) (2019-03-29)

## [1.5.19](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.18...v1.5.19) (2019-03-29)

## [1.5.18](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.17...v1.5.18) (2019-03-29)

## [1.5.17](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.16...v1.5.17) (2019-03-29)

## [1.5.16](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.15...v1.5.16) (2019-03-29)


### Performance Improvements

* set logging to false on install ([0c4696c](https://github.com/spmeesseman/vscode-taskexplorer/commit/0c4696c))

## [1.5.15](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.14...v1.5.15) (2019-03-29)

## [1.5.14](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.13...v1.5.14) (2019-03-29)

## [1.5.13](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.12...v1.5.13) (2019-03-29)

## [1.5.12](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.11...v1.5.12) (2019-03-29)


### Bug Fixes

* display correct extension name in error messages ([668d15a](https://github.com/spmeesseman/vscode-taskexplorer/commit/668d15a))
* show correct extension name in output window ([df1283a](https://github.com/spmeesseman/vscode-taskexplorer/commit/df1283a))

## [1.5.11](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.10...v1.5.11) (2019-03-28)

## [1.5.10](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.9...v1.5.10) (2019-03-28)

## [1.5.9](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.8...v1.5.9) (2019-03-28)

## [1.5.8](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.7...v1.5.8) (2019-03-28)

## [1.5.7](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.6...v1.5.7) (2019-03-28)


### Bug Fixes

* the open command for any task group other than npm does not work ([30fedc0](https://github.com/spmeesseman/vscode-taskexplorer/commit/30fedc0))

## [1.5.6](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.5...v1.5.6) (2019-03-28)

## [1.5.5](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.4...v1.5.5) (2019-03-28)

## [1.5.4](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.3...v1.5.4) (2019-03-28)

## [1.5.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.2...v1.5.3) (2019-03-28)


### Performance Improvements

* remove built in npm task provider, use vscode internal npm task provider ([221fa9d](https://github.com/spmeesseman/vscode-taskexplorer/commit/221fa9d))

## [1.5.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.1...v1.5.2) (2019-03-28)


### Bug Fixes

* ant files named Build.xml are not recognized, only build.xml ([66c0fc2](https://github.com/spmeesseman/vscode-taskexplorer/commit/66c0fc2))
* non-target xml nodes with name parameter are showing as targets ([85c734d](https://github.com/spmeesseman/vscode-taskexplorer/commit/85c734d))

## [1.5.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.5.0...v1.5.1) (2019-03-27)


### Performance Improvements

* remove tooltip loading for vscode tasks and ant targets ([64e7033](https://github.com/spmeesseman/vscode-taskexplorer/commit/64e7033))

# [1.5.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.4.1...v1.5.0) (2019-03-27)


### Bug Fixes

* (1) open command for ant targets found in subfolders of project root. (2) invalid path displayed in view ([09c7a27](https://github.com/spmeesseman/vscode-taskexplorer/commit/09c7a27))
* cannot launch ant tasks if build.xml is not in root project folder ([24d0c8d](https://github.com/spmeesseman/vscode-taskexplorer/commit/24d0c8d))


### Features

* add ansicon support, override ant path ([f36b612](https://github.com/spmeesseman/vscode-taskexplorer/commit/f36b612))
* name file tree nodes with respective task types, put relative paths in parenthesis ([f558d68](https://github.com/spmeesseman/vscode-taskexplorer/commit/f558d68))

## [1.4.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.4.0...v1.4.1) (2019-03-27)


### Bug Fixes

* add required new xml2js runtime dep. ([91a1422](https://github.com/spmeesseman/vscode-taskexplorer/commit/91a1422))

# [1.4.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.3.5...v1.4.0) (2019-03-27)


### Features

* add ant target support ([bba8552](https://github.com/spmeesseman/vscode-taskexplorer/commit/bba8552))

## [1.3.5](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.3.4...v1.3.5) (2019-03-27)


### Bug Fixes

* open command for vs code tasks ([1a9b374](https://github.com/spmeesseman/vscode-taskexplorer/commit/1a9b374))

## [1.3.4](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.3.3...v1.3.4) (2019-03-27)

## [1.3.3](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.3.2...v1.3.3) (2019-03-27)

## [1.3.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.3.1...v1.3.2) (2019-03-26)

## [1.3.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.3.0...v1.3.1) (2019-03-26)

# [1.3.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.2.0...v1.3.0) (2019-03-26)


### Features

* add collapse all button ([58204e9](https://github.com/spmeesseman/vscode-taskexplorer/commit/58204e9))

# [1.2.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.1.0...v1.2.0) (2019-03-26)


### Features

* bulk check in initial replica of vscode npm scripts explorer view, but with tasks [skip ci] ([dac97c1](https://github.com/spmeesseman/vscode-taskexplorer/commit/dac97c1))

# [1.1.0](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.0.2...v1.1.0) (2019-03-26)


### Bug Fixes

* invalid console.log ([07169ce](https://github.com/spmeesseman/vscode-taskexplorer/commit/07169ce))
* rogue text ([d6f2597](https://github.com/spmeesseman/vscode-taskexplorer/commit/d6f2597))


### Features

* first round of changes [skip ci] ([a06ed57](https://github.com/spmeesseman/vscode-taskexplorer/commit/a06ed57))

## [1.0.2](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.0.1...v1.0.2) (2019-03-26)

## [1.0.1](https://github.com/spmeesseman/vscode-taskexplorer/compare/v1.0.0...v1.0.1) (2019-03-26)

# 1.0.0 (2019-03-26)

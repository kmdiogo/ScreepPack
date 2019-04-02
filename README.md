# ScreepPack
Lightweight Python Script that Flattens and Refactors Screeps Module imports
 
 
## What Does ScreepPack Do?
Screeps does not support folders. As such, all source files must be in one directory when uploading code into the game. 
ScreepPack takes all files in your Screeps source code folder and creates a new "flattened" directory of files. A directory is 
"flattened" when all the contents of the directory are placed into a new directory, one that does not contain any subdirectories. This
means you can write all your Screeps files using folder organization then compile it down to a flattened version for use in-game.

Additionally, ScreepPack will also find any module imports and refactor them to use the appropriate flattened file names.
For example, for a file located in the root directory trying to import another file in 'Roles/Harvester.js', the module import would
look like:
```javascript
var roleHarvester = require('./Role/Harvester');
```
ScreepPack will automatically refactor the import to use the appropriate flattened version:
```javascript
var roleHarvester = require('Role.Harvester');
```

## Configuring ScreepPack
The screep-pack.json file contains all configuration options. The parameters are:
- output_directory: The directory where the flattened screep files will be sent
- flatten_separator: What character the flattener will use to separate directories. For example, if flatten_separator is '.', then
the file located in path 'Roles/Harvester.js' will be flattened to the file name 'Roles.Harvester'
- screeps_folder: The root directory of where your Screeps source code resides
- ignore_files: An array of names of files to ignore

## Running the script
Running ScreepPack.py will automatically flatten all folders into a specified directory. Note that the script is written for Python
versions >=3.

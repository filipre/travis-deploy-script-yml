# Travis deploy script provider

`.travis.yml` file for using the script provider inside the `deploy` section.

## How to:

1. Make script executable: `chmod +x script.sh`
2. Use a relative path: `script: ./script.sh`

## Experiments

### Using a Shebang
We imply that the program in the shebang is executable

- [x] Script executable, relative path, quotes: **worked** ([Travis log](https://travis-ci.org/filipre/travis-deploy-script-yml/builds/136508863))
- [x] Script not executable, relative path, quotes: **failed** ([Travis log](https://travis-ci.org/filipre/travis-deploy-script-yml/builds/136511458))
- [x] Script executable, file name only, quotes: **failed** ([Travis log](https://travis-ci.org/filipre/travis-deploy-script-yml/builds/136514030))
- [x] Script exectuable, relative path, no quotes: **worked** ([Travis log](https://travis-ci.org/filipre/travis-deploy-script-yml/builds/136519782))

### Without Using a Shebang
We use `/bin/sh` as program to call our script. We imply that the *program* is executable.

- [ ] *Script* not executable, file name only, no quotes: **na** (na)

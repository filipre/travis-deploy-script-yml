# Travis deploy script provider

`.travis.yml` file for using the script provider inside the `deploy` section.

## How to:

1. Make script executable: `chmod +x script.sh`
2. Use quotes and relative path: `script: "./script.sh"`

## Experiments

- [x] Script executable, relative path, quotes: **worked** ([Travis log](https://travis-ci.org/filipre/travis-deploy-script-yml/builds/136508863))
- [x] Script not executable, relative path, quotes: **failed** ([Travis log](https://travis-ci.org/filipre/travis-deploy-script-yml/builds/136511458))
- [x] Script executable, file name only, quotes: **failed** ([Travis log](https://travis-ci.org/filipre/travis-deploy-script-yml/builds/136514030))
- [ ] Script exectuable, relative path, no quotes: **na** (na)

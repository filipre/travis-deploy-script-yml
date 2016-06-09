# Travis deploy script provider
`.travis.yml` file for using the script provider inside the `deploy` section.

## How to:
If you use a shebang inside your script (e.g. `#!/bin/sh`):

1. Make your script executable: `chmod +x script.sh`
2. Use a relative path: `script: ./script.sh`

```yml
deploy:
  provider: script
  script: ./script.sh
  on:
    branch: master
```

If you use another program to call your files:

1. Make sure that the program is executable and you use the right path
2. That's it!

```yml
deploy:
  provider: script
  script: /bin/sh script.sh
  on:
    branch: master
```

## Experiments
**worked**: Build exited with `0` (and you should see the great proof from [[1]](http://mathoverflow.net/a/42519))

**failed**: Exit code is unequal `0` (like exit code `127`)

### Using a Shebang
We imply that the program in the shebang is executable

- [x] Script executable, relative path, quotes: **worked** ([Travis log](https://travis-ci.org/filipre/travis-deploy-script-yml/builds/136508863))
- [x] Script not executable, relative path, quotes: **failed** ([Travis log](https://travis-ci.org/filipre/travis-deploy-script-yml/builds/136511458))
- [x] Script executable, file name only, quotes: **failed** ([Travis log](https://travis-ci.org/filipre/travis-deploy-script-yml/builds/136514030))
- [x] Script exectuable, relative path, no quotes: **worked** ([Travis log](https://travis-ci.org/filipre/travis-deploy-script-yml/builds/136519782))

### Without Using a Shebang
We use `/bin/sh` as program to call our script. We imply that the *program* is executable.

- [x] *Script* not executable, file name only, no quotes: **worked** ([Travis log](https://travis-ci.org/filipre/travis-deploy-script-yml/builds/136525143))

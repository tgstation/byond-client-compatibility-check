# byond-client-compatibility-check
Github action to confirm that the required client version of byond world (.dmb) isn't higher than expected.

## Inputs:

* `dmb-location` - required, location of the dmb to inspect (likely compiled by a previous workflow step
* `max-required-client-version` - optional, the highest (inclusive) client version the byond world/dmb is allowed to require. if the dmb wants a higher version then this, the action will fail.

## Outputs:
* `required-client-version` - The detected client compatibility version of the dmb.

Usage example:

```yml
name: CI Suite
jobs:
  compile_game_code:
    name: Compile game
    runs-on: ubuntu-20.04
    steps:
      - uses: actions/checkout@v3
      [...]
      - name: compile dmb
      [...]
      - uses: MrStonedOne/byond-client-compatibility-check@v1
        with:
          dmb-location: tgstation.dmb
          max-required-client-version: 514
```

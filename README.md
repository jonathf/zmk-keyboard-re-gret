# Re-gret ZMK Module

This is a [ZMK Module](https://zmk.dev/docs/features/modules) for my [Re-gret keyboard](https://github.com/rschenk/re-gret).

To use this in your zmk-config, follow the [ZMK Module docs](https://zmk.dev/docs/features/modules) using the config below. You'll name your keymap `re-gret.keymap`.

## Usage

Add the following entries to `remotes` and `projects` in `config/west.yml`

```yaml
# config/west.yml
manifest:
  remotes:
    - name: zmkfirmware
      url-base: https://github.com/zmkfirmware
    - name: rschenk
      url-base: https://github.com/rschenk
  projects:
    - name: zmk
      remote: zmkfirmware
      revision: v0.4 # set to desired version
      import: app/west.yml
    - name: zmk-keyboard-re-gret
      remote: rschenk
      revision: v0.4 # set to same version as zmk above
  self:
    path: config
```

And then in your `build.yaml` file:

```yaml
# build.yaml
board: ["xiao_ble"]
shield: ["re-gret"]
```

## Versioning

ZMK introduced some breaking changes with v0.4. I have updated this module to compile with v0.4 but you should [pin your ZMK version](https://zmk.dev/blog/2025/06/20/pinned-zmk) and pin the version of `zmk-keyboard-re-gret` to match

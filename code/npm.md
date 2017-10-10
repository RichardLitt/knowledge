# npm

## Editing the `package.json` from the CLI

Currently, this isn't possible. See [https://github.com/npm/npm/issues/9397](https://github.com/npm/npm/issues/9397).

For now, use [json]() and run this: [1](https://stackoverflow.com/questions/25329241/edit-package-json-from-commandline)

```
$ cat package.json
{
  "name": "my-project",
  "description": "Project by @DerZyklop",
  "version": "0.0.0"
}

$ json -I -f package.json -e 'this.license="MIT"'
json: updated "package.json" in-place

$ cat package.json
{
  "name": "my-project",
  "description": "Project by @DerZyklop",
  "version": "0.0.0",
  "foo": "MIT"
}
```
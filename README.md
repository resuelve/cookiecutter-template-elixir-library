# cookiecutter-templete-elixir-library

This project helps Elixir developers publish their libraries to Hex.pm.

By using this template you can generate a project directory with the follow:

* **README.md**: Custom readme with usage instructions
* **.github/workflows/ci.yml** Github actions workflow for elixir continuos integration process
* **.github/workflows/publish-hexpm.yml** Github actions workflow for public elixir library in Hex.pm 

## Install

You need to install `cookiecutter` on your local with another testing tools:

``` shell
$ brew install cookiecutter
```

Additional you can use `yamllint` to validate that the generated manifests are valid.

``` shell
$ brew install yamllint
```

## Usage

Generate a template:

``` shell
$ cookiecutter git@github.com:resuelve/cookiecutter-templete-elixir-api.git
```

This command will ask you for your project attributes, and after that
creates a directory with your project's name, for example:

``` shell
$ find example-api
example-api
example-api/README.md
example-api/.github/workflows
example-api/.github/workflows/ci.yml
example-api/.github/workflows/publish-hexpm.yml
```

### Test resulting yaml

You can use `yamllint` to lint your resulting Github actions workflow, for example:

```shell
$ yamllint example-api/.github/workflows/ci.yml
```

Remember to test locally and fix any error reported by the linter before commit.

### Usage for CD workflows

If you wan to build this inside your CI/CD process using Github actions, you can
run cookiecutter without user intervention:

``` shell
$ cd data/vcs
$ cookiecutter git@github.com/resuelve/cookiecutter-templete-elixir-api.git \
  --no-input \
  --overwrite-if-exists \
  project_name=example-api
```
### Contributions

I you find this useful please buy me a gansito :P, I'm just kidding, just try to use it and give feedback.

### References

Please read the follow references for more details:

* [Cookicutter home](https://github.com/cookiecutter/cookiecutter)
* [Cookicutter documentation](https://cookiecutter.readthedocs.io/en/stable/)

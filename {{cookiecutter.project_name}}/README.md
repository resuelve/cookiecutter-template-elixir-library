# {{ cookiecutter.project_name }}

## Pipeline Flow

![alt text](/src/img/flow.png)

## Requirements

 * Elixir {{ cookiecutter.elixir_version }}

## Next steps

After creating your template, upload to the library directory:

.github/workflows/ci.yml
.github/workflows/publish-hexpm.yml

Later enter the mix.ex file and verify that the following lines:

##Inside the module "def project do"
 ```
description: "description of project",
package: package(),
aliases: aliases(),
 ```
 #Check to have the following module or put
 ```
   defp package do
    [
      organization: "resuelve",
      licenses: [],
      links: %{"GitHub" => "https://github.com/resuelve/name_of_proyect"}
    ]
  end
 ```
 #Check to have the following module or put
 ```
   def aliases do
    [
      ci: ["format --check-formatted", "credo", "test --cover", "dialyzer"]
    ]
  end
 ```
Note: In some cases, don't is necessary dialyzer, ask to developer owner of [proyect](proyect)  

You should have a mix.ex file like this example
 ```
defmodule Corelib.MixProject do
  use Mix.Project

  def project do
    [
      app: :name_proyect,
      version: "0.21.2",
      elixir: "~> 1.6",
      description: "description of the proyect",
      package: package(),
      start_permanent: Mix.env() == :prod,
      test_coverage: [tool: ExCoveralls],
      aliases: aliases(),
      deps: deps()
    ]
  end

  defp package do
    [
      organization: "resuelve",
      licenses: [],
      links: %{"GitHub" => "https://github.com/resuelve/name_proyect"}
    ]
  end

  # Run "mix help compile.app" to learn about applications.
  def application do
    [
      extra_applications: [:logger]
    ]
  end

  # Run "mix help deps" to learn about dependencies.
  defp deps do
    [
      {:bypass, "~> 1.0", only: :test},
      {:jason, "~> 1.1"},
      {:mojito, "~> 0.6.1"},
      {:credo, "~> 1.5", only: [:dev, :test], runtime: false},
      {:excoveralls, "~> 0.13.3", only: :test},
      {:ex_doc, "~> 0.21", only: :dev, runtime: false},
      {:dialyxir, "~> 1.0", only: [:dev, :test], runtime: false}
    ]
  end

  def aliases do
    [
      ci: ["format --check-formatted", "credo", "test --cover", "dialyzer"]
    ]
  end
end
 ```
## Test workflow
Since you have the mix.ex file configured correctly and successfully passing the CI. You can trigger a new version of the library to be uploaded.
In the github repository, go to the release section, check the release version number, and ask for advice from the developer owner of the library, to find out what kind of changes the next version would have, to put the tag number it would have and add it.

For example, an api with the version 1.7.2:

1 = The number of mayor versión changes

7 = The number of minor versión changes

2 = The number of bug fix in this minor versión

 ```
defmodule Corelib.MixProject do
  use Mix.Project

  def project do
    [
      app: :name_proyect,
      version: "0.21.2",
```
Since you made the library version number change, in mix.exs. He goes back to the release tags section on github and creates a new tag, as directed by the developer owner, which is the changes he wants to push, with the version number of the library he put in mix.exs.
This will trigger the publish-hexpm.yml stream. Once the pipeline is done, check in hex.pm that your new library version is up.

## References

  * Official website: https://www.phoenixframework.org/
  * Guides: https://hexdocs.pm/phoenix/overview.html
  * Docs: https://hexdocs.pm/phoenix
  * Forum: https://elixirforum.com/c/phoenix-forum
  * Source: https://github.com/phoenixframework/phoenix

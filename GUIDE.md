# AutoRA Template

## Quickstart Guide

Install this in an environment using your chosen package manager. In this example we are using virtualenv

Install:
- python (3.8 or greater): https://www.python.org/downloads/
- virtualenv: https://virtualenv.pypa.io/en/latest/installation.html

Create a new virtual environment:
```shell
virtualenv venv
```

Activate it:
```shell
source venv/bin/activate
```

Use `pip install` to install the current project (`"."`) in editable mode (`-e`) with dev-dependencies (`[dev]`):
```shell
pip install -e ".[dev]"
```

## Add your contribution 
Your autora-subpackage should include (1) your code implementing in the respective folder of src/autora/*, 
(2) **tests** for your contribution, and (3) respective **documentation**.

### Adding your code implementation
Add your code implementation to src/autora/theorist, src/autora/experimentalist or src/autora/experiment_runner. You can create new categories if none of them seems fitting.

### Adding tests
You should also add tests. These can be [doctests](https://docs.python.org/3/library/doctest.html) or as test cases in `tests/test_your_contribution_name.py`. 

### Adding documentation
***Whenever possible stick to the templates provided to ensure coherent documentation***
- You may document your contribution in `docs/index.md`. You can also add new pages in the `docs` folder
  - It is recommended to include at least a `index.md` file with an overview and a `quick_start_guide.md` file, where the setup is explained.
  - It is also very useful for users to include at least one example in form of a jupiter notebook. If you want to include a basic example, please use the basic_usage.ipynb file. You can add more examples (if possible, please replace the names of the additional_example to something more descriptive)
- Update the `mkdocs.yml` file to reflect structure of the documentation. You can add additional pages and examples here.
- Update the README.md file 

## Add new dependencies 

In pyproject.toml add the new dependencies under `dependencies`

Install the added dependencies
```shell
pip install -e ".[dev]"
```

## Publishing the package

Update the metadata under `project` in the pyproject.toml file to include name, description, author-name, author-email and version.
Also, update the URL for the repository under `project.urls`.

- Follow the guide here: https://packaging.python.org/en/latest/tutorials/packaging-projects/

Build the package using:
```shell
python -m build
```

Publish the package to PyPI using `twine`:
```shell
twine upload dist/*
```

### Publishing with GitHub actions
To automate the publishing process for your package, you can use a GitHub action instead of Twine:
- Add the GitHub action to the `.github/workflows` directory: For example, you can use the default publishing action:
  - Navigate to the `actions` on the GitHub website of your repository.
  - Search for the `Publish Python Package` action and add it to your project
- Create a new release: Click on `create new release` on the GitHub website of your repository.
- Choose a tag (this is the version number of the release. If you didn't set up dynamic versioning it should match the version in the `pyproject.toml` file)
- Generate release notes automatically by clicking `generate release`, which adds the markdown of the merged pull requests and the contributors.
- If this is a pre-release check the box `set as pre-release`
- Click on `publish release`

### Dynamic versioning
To automatically generate the version number for each release, you can use dynamic versioning instead of updating the version number manually. To set this up, you need to alter the `pyproject.toml` file:
- Replace `version = "..."` with `dynamic = ["version"]` under `project`
- Replace the `build-system` section with the following:
```toml
[build-system]
requires = ["setuptools", "setuptools_scm"]
build-backend = "setuptools.build_meta"
```
- Add a new section to the `pyproject.toml` file:
```toml
[tool.setuptools_scm]
```

#### Dynamic versioning: Publishing using `twine`
If you are using dynamic versioning with Twine, follow these steps to publish your package:
- Commit all of your changes.
- Tag the commit: Create an annotated Git tag at the commit you want to release. This is typically the most recent commit on your main branch. For example, you can run `git tag -a 1.0.0a` to create a tag named "1.0.0a" at the current commit.
- Build and release the package using Twine as described in the above section.

#### Dynamic versioning: Publishing via GitHub actions
You can use dynamic versioning with the GitHub action described in the previous section. The workflow remains the same, but you don't have to update the version in the `pyproject.toml` file. 

## Workflows
...

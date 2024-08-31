1. Find your language in *Python Developer's Guide* > *Documentation* >
   [*Translating*](https://devguide.python.org/documentation/translating/).
2. If it's missing there, [start a new translation](https://devguide.python.org/documentation/translating/#starting-a-new-translation).
3. If it's not using Transifex, [download Poedit](https://poedit.net/download).
4. If it's using Transifex, [sign up to Transifex](https://app.transifex.com/signup/open-source/).
5. Request to join a language team in [python-doc organization](https://www.transifex.com/python-doc/) on Transifex.

### Translating
1. Select a resource you want to start translating.
7. Locate a resource and a string in translating tool.
7. Look for the context of the paragraph/sentence to translate in rendered (built) docs.
8. Look for glossary terms underlined in a source string.
9. Optionally update the glossary.
10. Look for suggestions, and use it to base the new translation on one of them.
11. Make sure that you fully understand the sense and context of the paragraph/sentence.
12. Optionally you can use an external translation tool.
13. Using above points, try to come up with a few sentences. "Would it be understandable for your friend?"
14. You may want to consult something with the translation group, [use Discord](https://discord.gg/3faJmGKhta).
15. If you're not sure, you can use *Save as Suggestion*.
16. You may want to manually check the correctness of reStructuredText syntax of your translation. You can use [*Online Sphinx editor*](https://livesphinx.herokuapp.com/).

### Preview nightly build (applicable to languages that uses it in their CIs)
1. Open [*Actions* tab in the GitHub repository](https://github.com/python/python-docs-pl/actions/).
2. Look for most recent documentation build there.
3. If the build fails, read through the logs and try to locate and resolve the cause.
4. If the build succeeds, from *Artifacts* section download the documentation in desired version and format.

### Building the documentation locally
1. Clone [CPython repository](https://github.com/python/cpython).
2. Enter `Doc` directory.
3. Call `make venv`.
4. Activate the venv: `.venv/bin/activate`.
5. Call `make html`.
6. The generated files will be placed in the `_build/html` directory.

### Building the translation locally
1. Clone your language translation repository.
2. Create directories `locale/xx` in `cpython/Doc`, where `xx` is your language shortcut.
3. Create a symlink in the CPython repository pointing to freshly cloned translation. `ln -s cpython/Doc/locales/xx/LC_MESSAGES python-docs-xx`
4. Call `-e SPHINXOPTS="-D language='xx'" html` in `cpython/Doc` repository.
5. The generated files will be placed in the `_build/html` directory.

### Fetching the translation from Transifex locally
1. Go to Transifex user settings > [*API token*](https://www.transifex.com/user/settings/api/).
2. Generate a new token.
3. Set it as a TX_TOKEN environment variable.
4. In the language repository call `python manage_translation.py fetch`.

### Further reading/tools
* [poutils](https://github.com/afpy/poutils) for PO-file related tasks
* [sphinx-intl](https://www.sphinx-doc.org/en/master/usage/advanced/intl.html#translating-with-sphinx-intl) for updating existing translations with new source strings
* [Weblate's continuous localization](https://docs.weblate.org/en/latest/admin/continuous.html) – Transifex alternative
* [MyST](https://myst-parser.readthedocs.io/en/latest/) – reStructuredText alternative
* [docsbuild-scripts](https://github.com/python/docsbuild-scripts) – where the documentation is built for multiple versions and languages for docs.python.org
* [docspush-transifex](https://github.com/rffontenelle/docspush-transifex) – where the source strings updates are pushed to Transifex

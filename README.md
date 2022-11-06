1. Find your language in *Python Developer's Guide* > *Documentation* >
   [*Translating*](https://devguide.python.org/documentation/translating/).
2. If it's missing there, [start a new translation](https://devguide.python.org/documentation/translating/#starting-a-new-translation).
3. If it's not using Transifex, [download Poedit](https://poedit.net/download).
4. If it's using Transifex, [sign up to Transifex](https://www.transifex.com/signup/).
5. Request to join [python-doc organization](https://www.transifex.com/python-doc/) on Transifex.

=== Translating ===
6. Select a resource you want to start translating.
7. Locate a resource and a string in translating tool.
7. Look for the context of the paragraph/sentence to translate in rendered (built) docs.
8. Look for glossary terms underlined in a source string.
9. Optionally update the glossary.
10. Look for suggestions, and use it to base the new translation on one of them.
11. Make sure that you fully understand the sense and context of the paragraph/sentence.
12. Optionally you can use an external translation tool.
11. Using above points, try to come up with a few sentences, that your work acquitance would understand.

=== Preview nightly build (applicable to languages that uses it in their CIs) ===
11. Open [*Actions* tab in the GitHub repository](https://github.com/python/python-docs-pl/actions/).
12. Look for most recent documentation build there.
13. If the build fails, read through the logs and try to locate and resolve the cause.
13. If the build succeeds, from *Artifacts* section download the documentation in desired version and format.

=== Building the documentation locally ===
1. Clone [CPython repository](https://github.com/python/cpython).
2. Enter `Doc` directory.
3. Call `make venv`.
4. Activate the venv: `.venv/bin/activate`.
5. Call `make html`.

=== Building the translation locally ===
1. Clone your language translation repository.
2. Create directories `locale/xx` in `cpython/Doc`, where `xx` is your language shortcut.
3. Create a symlink in the CPython repository pointing to freshly cloned translation. `ln -s cpython/Doc/locales/xx/LC_MESSAGES python-docs-xx`
4. Call `-e SPHINXOPTS="-D language='xx'" html` in `cpython/Doc` repository.

=== Fetching the translation from Transifex locally ===
1. Go to Transifex user settings > [*API token*](https://www.transifex.com/user/settings/api/).
2. Generate a new token.
3. Set it as a TX_TOKEN environment variable.
4. In the language repository call `python manage_translation.py fetch`.

=== Further reading ===
* [poutils](https://github.com/afpy/poutils) for PO-file related tasks
* [Weblate's continuous localization](https://docs.weblate.org/en/latest/admin/continuous.html) – Transifex alternative

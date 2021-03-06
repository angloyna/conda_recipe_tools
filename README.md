Tools useful for maintaining and updating conda recipes and packages.

To install run `pip install -e .` or a similar command.

Recipe and Feedstock tools
--------------------------
* `sync_cf` : Rebase feedstocks against conda-forge
* `update_recipe` : Update a recipe to a specific version
* `prepare_batch_file` : Prepare a batch-file.txt for submission to c3i batch
* `create_clobber` : Create recipe_clobber.yaml files
* `show_git_messages` : Print out git messages for a set of feedstocks.
* `push_feedstock_changes` : Push up changes for a set of feedstocks.
* `create_diff_report` : Create a HTML report showing diffs for a collection of feedstocks.
* `find_changed_feedstocks` : Find feedstocks which have changed since they were last checked.
* `find_latest` : Find the latest version of a package or set of packages.
* `upstream_stats` : Report status of upstream rebase-ability for feedstocks.

Channel tools
-------------

* `channel_latest` : Show the newest version of packages in a channel.
* `upstream_newer` : Find packages where an upstream channel has a newer version.

Package tools
-------------

* `extract_index_json`
* `replace_index_json`

Misc tools
----------
* `run_grimlock` : Updates recipes and executes builds from a csv file of packages and versions.
* `gh` : Open a GitHub repository in the current web browser.
* `pypi` : Open a PyPI package page in the current web browser.
* `reqs` : Attempt to list packages dependencies from PyPI.
* `find_outdated_packages_pypi.py` : Find outdated packages on a Anaconda.org channel.
* `rebuild_what` : Print out a list of packages to rebuild for a migration.


Suggested workflow
------------------

Prepare and run a series of builds on concourse.

* Prepare of list of outdated feedstocks.
* Run `sync_cf` to rebase the feedstocks against conda-forge.
* Run `update_recipe` for each outdated feedstock.
* Run `prepare_batch_file` to create a batch-file.txt file.
* Submit builds to c3i using `c3i batch batch-file.txt` 

Once these builds are finished and have been added to the package reposistory.

* Run `show_git_messages` to prepare a set of git commit messages.
* Run `push_feedstock_changes` to push the feedstock changes to GitHub.
* Add changed feedstocks submodules and push to aggregate.

.. You should enable this project on travis-ci.org and coveralls.io to make
   these badges work. The necessary Travis and Coverage config files have been
   generated for you.

.. image:: https://travis-ci.org/espona/ckanext-oaipmh_repository.svg?branch=master
    :target: https://travis-ci.org/espona/ckanext-oaipmh_repository

.. image:: https://coveralls.io/repos/espona/ckanext-oaipmh_repository/badge.svg
  :target: https://coveralls.io/r/espona/ckanext-oaipmh_repository

.. image:: https://pypip.in/download/ckanext-oaipmh_repository/badge.svg
    :target: https://pypi.python.org/pypi//ckanext-oaipmh_repository/
    :alt: Downloads

.. image:: https://pypip.in/version/ckanext-oaipmh_repository/badge.svg
    :target: https://pypi.python.org/pypi/ckanext-oaipmh_repository/
    :alt: Latest Version

.. image:: https://pypip.in/py_versions/ckanext-oaipmh_repository/badge.svg
    :target: https://pypi.python.org/pypi/ckanext-oaipmh_repository/
    :alt: Supported Python versions

.. image:: https://pypip.in/status/ckanext-oaipmh_repository/badge.svg
    :target: https://pypi.python.org/pypi/ckanext-oaipmh_repository/
    :alt: Development Status

.. image:: https://pypip.in/license/ckanext-oaipmh_repository/badge.svg
    :target: https://pypi.python.org/pypi/ckanext-oaipmh_repository/
    :alt: License

=============
ckanext-oaipmh_repository
=============

.. Put a description of your extension here:
   What does it do? What features does it have?
   Consider including some screenshots or embedding a video!


------------
Requirements
------------

**Plugins required:** In order to use this plugin, the following dependencies/plugins must be installed

* **ckanext-package_converter** --> https://github.com/sedici/ckanext-package_converter
* **ckantoolkit** --> https://github.com/ckan/ckantoolkit
* **ckanext-scheming** --> https://github.com/ckan/ckanext-scheming



------------
Installation
------------

.. Add any additional install steps to the list below.
   For example installing any non-Python dependencies or adding any required
   config settings.

To install ckanext-oaipmh_repository:

1. Activate your CKAN virtual environment, for example::

.. code:: bash

     . /usr/lib/ckan/default/bin/activate

2. Install the ckanext-oaipmh_repository Python package into your virtual environment::

.. code:: bash

     pip install -e git+https://github.com/sedici/ckanext-oaipmh_repository.git#egg=ckanext-oaipmh_repository

3. Install the plugin dependencies

.. code:: bash

    pip install -e git+https://github.com/sedici/ckanext-package_converter.git#egg=ckanext-package_converter
    pip install -e git+https://github.com/ckan/ckantoolkit.git#egg=ckantoolkit
    pip install -e git+https://github.com/ckan/ckanext-scheming.git#egg=ckanext-scheming

4. Add configuration settings explained at `Config Settings <#config-settings>`__.

5. Add ``oaipmh_repository``, ``scheming-datasets``, ``package-converter`` to the ``ckan.plugins`` setting in your CKAN
   config file (by default the config file is located at
   ``/etc/ckan/default/production.ini``).

6. Restart CKAN. For example if you've deployed CKAN with Apache on Ubuntu::

     sudo service apache2 reload


---------------
Config Settings
---------------

The plugin may be configured through some configurations settings, described bellow.

.. code:: ini

    ##############
    ##OAIPMH Repository Configuration
    ##############
    ##Prefix used to construct the "Unique Identifier" of every OAI record. Defaults to "oai:ckan:id".
    #oaipmh_repository.id_prefix = oai:ckan:id:
    
    ##Every OAI record has an "Unique Identifier". Use this setting to set the dataset metadata used as identifier. Defaults to "name".
    #oaipmh_repository.id_field = name
    
    ##Limit the set of records exposed through OAIPMH to a certain regular expression (check Solr regular expression syntax). 
    ##This configuration is used along with the "oaipmh_repository.id_field" configured. Defaults to "*".
    #oaipmh_repository.regex = *
    
    ##Use this setting to limit the maximum number of records per page included in every OAI response. Defaults to 1000.
    #oaipmh_repository.max = 1000
    
    oaipmh_repository.sqlalchemy.url = %(sqlalchemy.url)s
    
    oaipmh_repository.site_id = %(ckan.site_id)s
    
    oaipmh_repository.solr_url = %(solr_url)s
    

Additionaly, the following **ckanext-scheming** configuration settings must be added in order to this plugin works (more at `ckanext-scheming documentation <https://github.com/ckan/ckanext-scheming>`__).

.. code:: ini

    ##Scheming Configuration (sacar si no hace falta...)
    #   module-path:file to schemas being used
    scheming.dataset_schemas = ckanext.scheming:ckan_dataset.json
    
    #   Preset files may be included as well. The default preset setting is:
    scheming.presets = ckanext.scheming:presets.json

------------------------
Development Installation
------------------------

To install ckanext-oaipmh_repository for development, activate your CKAN virtualenv and
do::

    git clone https://github.com/espona/ckanext-oaipmh_repository.git
    cd ckanext-oaipmh_repository
    python setup.py develop
    pip install -r dev-requirements.txt


-----------------
Running the Tests
-----------------

To run the tests, do::

    nosetests --nologcapture --with-pylons=test.ini

To run the tests and produce a coverage report, first make sure you have
coverage installed in your virtualenv (``pip install coverage``) then run::

    nosetests --nologcapture --with-pylons=test.ini --with-coverage --cover-package=ckanext.oaipmh_repository --cover-inclusive --cover-erase --cover-tests


---------------------------------
Registering ckanext-oaipmh_repository on PyPI
---------------------------------

ckanext-oaipmh_repository should be availabe on PyPI as
https://pypi.python.org/pypi/ckanext-oaipmh_repository. If that link doesn't work, then
you can register the project on PyPI for the first time by following these
steps:

1. Create a source distribution of the project::

     python setup.py sdist

2. Register the project::

     python setup.py register

3. Upload the source distribution to PyPI::

     python setup.py sdist upload

4. Tag the first release of the project on GitHub with the version number from
   the ``setup.py`` file. For example if the version number in ``setup.py`` is
   0.0.1 then do::

       git tag 0.0.1
       git push --tags


----------------------------------------
Releasing a New Version of ckanext-oaipmh_repository
----------------------------------------

ckanext-oaipmh_repository is availabe on PyPI as https://pypi.python.org/pypi/ckanext-oaipmh_repository.
To publish a new version to PyPI follow these steps:

1. Update the version number in the ``setup.py`` file.
   See `PEP 440 <http://legacy.python.org/dev/peps/pep-0440/#public-version-identifiers>`_
   for how to choose version numbers.

2. Create a source distribution of the new version::

     python setup.py sdist

3. Upload the source distribution to PyPI::

     python setup.py sdist upload

4. Tag the new release of the project on GitHub with the version number from
   the ``setup.py`` file. For example if the version number in ``setup.py`` is
   0.0.2 then do::

       git tag 0.0.2
       git push --tags

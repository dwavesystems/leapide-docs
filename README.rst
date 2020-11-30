========
Leap IDE
========

An Integrated Development Environment(IDE) for quantum applications hosted in
`Leap quantum applications environment <https://cloud.dwavesys.com/leap>`_.

.. figure:: _images/tmp.png
  :align: center
  :figclass: align-center
  :scale: 35%

  A view of the IDE.

The Leap IDE default workspace is a development environment pre-configured with
Ocean software and some typically used libraries such as Matplotlib. It also
includes D-Wave extensions such as the problem inspector and a navigation
flyout menu to provide quick links to D-Wave resources.

Getting Started
---------------

Open the IDE in one of the following ways:

* Log in to your `Leap <https://cloud.dwavesys.com/leap>`_ account, open the Workspaces
  page, and click on an example.
* In the address bar of your browser, prefix the URL of your GitHub repository
  (or a particular pull request, branch, or issue) with, ``https://ide.dwavesys.io/#``,
  for example, ``https://ide.dwavesys.io/#https://github.com/jane/myquantumapp``.

The IDE opens the repository files in a Docker container with a full developer
environment.

Start by selecting an example, opening and running it.

D-Wave tutorial videos are available on YouTube; for example, `Leap IDE <https://www.youtube.com/watch?v=62gDQ14pjwM>`.

Developing Applications
-----------------------

The recommended workflow for new application development is to start from a template
or example workspace and modify it.

On the Workspaces page, the menu under your User Name on the top righthand
corner lets you edit the following information:

* Access control: to save changes, you need to grant the IDE permission to write
  to your GitHub repo or, if you started with a D-Wave example, create a fork.
* Environmental variables such as your SAPI token (token used
  to authenticate client sessions when you connect to remote solvers such as D-Wave
  quantum computers and hybrid solvers).

Configuration
-------------

Some more advanced configurations include the following:

Repository Requirements
~~~~~~~~~~~~~~~~~~~~~~~

You can create a YAML file to open a repository with your required packages
loaded as follows::

  tasks:
   - init: pip install -r requirements.txt

User Dockerfile
~~~~~~~~~~~~~~~

The IDE uses a Docker image, based on python:3.7-slim, available within
the IDE as ``dwavesys/leapide:latest``. To build on top of it, your Dockerfile
should look like this::

  FROM dwavesys/leapide:latest

  USER root

  # install system packages
  RUN apt-get update \
      && apt-get install -yq --no-install-recommends \
          clang \
          libboost-dev \
      && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/*

  # install system-wide python package
  RUN pip install --no-cache-dir \
          dwave-ocean-sdk==4.0.0 \
      && rm -rf /tmp/*

API token
~~~~~~~~~

The IDE periodically imports your API token from
`Leap <https://cloud.dwavesys.com/leap/>`_. If you reset your token
on the Leap dashboard, your new token is automatically updated in the IDE within
a minute.

Every workspace you create is pinned to a project in your account. If your account
has access to multiple projects, the IDE imports the API token for the project
pinned to the current workspace. You can override the imported API token by
setting the ``DWAVE_API_TOKEN`` environment variable in the IDE.

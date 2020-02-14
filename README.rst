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

Tutorial videos are available here: <<NEED LINK TO OUR VIDEOS>>

Developing Applications
-----------------------

The recommended workflow for new application development is to start from a template
or example workspace and modify it.

On the Workspaces page, the menu under your User Name on the top righthand
corner lets you edit the following information:

* Access control: to save changes, you need to grant the IDE permission to write
  to your GitHub repo or, if you started with a D-Wave example, create a fork.
* Environmental variables: the IDE automatically sets your SAPI token (token used
  to authenticate client sessions when you connect to remote solvers such as D-Wave
  quantum computers and hybrid solvers).

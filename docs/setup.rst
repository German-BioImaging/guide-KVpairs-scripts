=====
Setup
=====

Setting up scripts for OMERO.web has to be done by an administrator of your \
server. Please contact them if the scripts are not present or in a different \
version as the one presented in this guide, and redirect them to this page.

The scripts menu is located in the top-right part of the OMERO.web client, \
on the left of the search bar. Please refer to the `script documentation \
<https://omero.readthedocs.io/en/stable/developers/scripts/index.html>`_ \
for more information.

Installing the scripts
----------------------
The Key-value pairs scripts have been updated in 2023 to enable \
them to annotate all the common object type in OMERO.web:

* Image
* Dataset
* Project
* Well
* Run/Acquisition
* Plate
* Screen

Check that the version of the currently installed scripts are of 2.0.0 and higher.

If not, you can find the scripts \
`here <https://github.com/German-BioImaging/guide-KVpairs-scripts>`_ and \
follow `these <https://omero.readthedocs.io/en/stable/developers/scripts/index.html#downloading-and-installing-scripts>`_ \
instructions to install them.

Configuring the Export script
-----------------------------
Note that the Export script can be fine tuned to your specific OMERO.web \
installation. For that, open the script and find the global parameter named \
"WEBCLIENT_URL", and set it to the URL of your webclient, without forgetting \
to add the http/https protocol in front:

``https://your-omeroweb-adress.org/webclient``

This will allow the script to return a link for the created .csv for a direct \
downloading. If not configured, the .csv can be found as an attachment of the \
first parent object passed in parameter of the export script (the file is \
attached regardless of whether the URL is set or not).
Parameter description
=====================

Generic parameters
------------------

Data Type
^^^^^^^^^
In combinaison with the parameter 'IDs', this selects the object \
from which targets are selected (targets of the given type).

For example, if Data Type is set to Project, and ID to 789, it will select all attached Datasets \
if 'Target Data Type' is set to Dataset, or all the Images if it is set to Image.

The Data Type can also be set to Tag, in which case the tagged objects of the "Target Data Type" \
are selected. This can be used for a more flexible selection of target object to process.

IDs
^^^
IDs of the object for the 'Data Type' selection.

Multiple ID can be provided at the same time, separated with a comma. In this case, \
the objects are processed sequentially.

Target Data Type
^^^^^^^^^^^^^^^^
The data type to be selected for processing by the script. Default to "<on current>" means that the \
objects specified by "Data Type" and "IDs" are the ones to be processed. In the other case, the selected \
type must correspond to a child object of the selected type (Image are child of Dataset and Project, \
Well are child of Screen and Plate, ...).


File Annotation
^^^^^^^^^^^^^^^
Parameter for the import of Key-Value pairs from a CSV file. Provided from the "Choose File" selection menu, \
the file will be temporarily uploaded to OMERO for the duration of the script.

The items listed in the CSV are matched to the Target object found. If an item of the CSV correspond to no \
target object, the item is skipped. As such, target objects coming from different parent objects can be \
annotated from a single CSV.

The matching of items in the CSV to target objects is done either via IDs or names (IDs have priority over names). \
The name of the columns containing either can be specified (see 'Target ID colname' and 'Target name colname'), but \
are by default respectively in upper case OBJECT_ID and OBJECT_NAME.

If no ID column is given in the CSV, the script attempts to match the items via the name. In this case, name duplicates \
are forbidden. (either from the CSV or inside OMERO, this will lead the script to fail).

Namespace
^^^^^^^^^
For the import of key-value pair, the namespace that will be given to the created key-value pairs. For the three other scripts,
limits the selection of key-value pairs to that namespace.

When no namespace is provided, matches the namespace 'openmicroscopy.org/omero/client/mapAnnotation', which \
makes the key-value pairs editable in OMERO.web (the only namespace that allows that).

Multiple namespace can be provided as a comma separated list. Or all namespace can be selected using the * character.

.. _Old Namespace:
Old Namespace
^^^^^^^^^^^^^
For the namespace conversion script. List of old namespace (comma separated) to convert to a different namespace (unique). \
This can be used to group key-value pairs into a single annotations (all found key-value pairs will be grouped to a single\
key-value pair).

.. _New Namespace:
New Namespace
^^^^^^^^^^^^^
For the namespace conversion script. The new namespace to assign to the key-value pairs found on the target \
object having the `Old Namespace`_. The found key-value pairs will be grouped into a single key-value pair per object with \
the 'New Namespace'.

Advanced parameters
-------------------

Separator
^^^^^^^^^
For the key-value pair import script, the separator used in the CSV to separate elements. By default \
set to 'guess' and will attempt to detect automatically the separator among ', ; TAB'.

For the key-value pair export script, the separator used in the generated CSV to separate elements. We \
recommend the use of TAB.

.. _Include column(s) of parents name:
Include column(s) of parents name
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
For the key-value pair export script. Check the box if you want to include in the first columns of the CSV output \
to contain for each objects the name of their parent containers.

The possible parents are PROJECT, DATASET, SCREEN, PLATE, RUN, WELL, depending on which object type \
is exported. These columns are ignored by default by the import script (see `Columns to exclude`_)

Include namespace
^^^^^^^^^^^^^^^^^
For the key-value pair export script. Check the box if you want to include in the CSV the namespace \
associated to each key as the first row of the document. This is interpreted back by the import script.

Include tags
^^^^^^^^^^^^
For the key-value pair export script. Check the box if you want to include in the CSV a column for the tags \
attached to the target objects. The tags are in the TAG[TAGSET] if the tags are part of a tagset.

.. _Columns to exclude:
Columns to exclude
^^^^^^^^^^^^^^^^^^
For the key-value pair import script. If the columns specified here are found in the CSV, they will be ignored \
for the generated key-value pairs.

Three default special values are given. <ID> corresponds to the name of the column for the object IDs specified by the \
parameter `Target ID colname`_. <NAME> corresponds to the name of the column for the object IDs specified by the \
parameter `Target name colname`_. <PARENT> corresponds to all possible parent containers type exported when using the \
paremeter `Include column(s) of parents name`_.

.. _Target ID colname:
Target ID colname
^^^^^^^^^^^^^^^^^
For the key-value pair import script. The name of the column in the CSV containing the objects IDs. If not present, \
the script will attempt to match the target objects by name. Defaults to OBJECT_ID as used by the export script.

.. _Target name colname:
Target name colname
^^^^^^^^^^^^^^^^^^^
For the key-value pair import script. The name of the column in the CSV containing the objects names. \
The names are used only to identify target objects if the ID column is not present. Defaults to \
OBJECT_NAME as used by the export script.

Exclude empty values
^^^^^^^^^^^^^^^^^^^^
For the key-value pair import script. Check this box if you wish to avoid creating an entry in the key-value \
pairs when a cell in the CSV is empty.

Attach csv to parents
^^^^^^^^^^^^^^^^^^^^^
For the key-value pair import script. Check this box if you wish to attach the chosen CSV file to the object used for the \
selection of targets.

Split value on
^^^^^^^^^^^^^^
For the key-value pair import script. The characters used to split the cells in the CSV into multiple entries. \
The character used here must be different from the CSV separator character.

Use only personal tags
^^^^^^^^^^^^^^^^^^^^^^
For the key-value pair import script. When tags are specified in the CSV (under a column named TAG), check this box \
if you want to restrict the use of tags to tags owned by you.

Create new tags
^^^^^^^^^^^^^^^
For the key-value pair import script. When tags are specified in the CSV (under a column named TAG), check this box \
if you want to allow the creation of tags when the don't exist. This also applies to tags for which a tagset is specified.
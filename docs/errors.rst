Assertion errors explained
--------------------------

<Something> is not a valid target for <SomethingElse>
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Objects are selected from a parent object TO a child object. Check out \
this section for more explanations on how to select objects with \
those scripts.

Annotation <xxx> not found:
^^^^^^^^^^^^^^^^^^^^^^^^^^^
Try reloading the page. This error can happen when you try to use the script on an object from a \
group after opening a second tab in a different group.

Cannot split cells with a character used as CSV separator
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Multiple values per cell can be used, but the character to split them must be \
different from the separator used by the csv.

CSV rows lenght mismatch: Header has <N> items, while line <line number> has <M>
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
This error shows either that one of the csv row has a different number of item from the header, or that \
something wrong happened with the parsing of the csv. (make sure that your csv separator is not a comma and that \
you use also a comma to have multiple value per cells, like in the case of tags).

Failed to sniff CSV delimiter please specify the separator
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
It happens that the sniffer to detect fails to understand what separator was \
used inside you .csv file. Please indicate in the parameter the separator used \
inside your .csv.

File annotation ID must be given when using Tag as source
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Because files cannot be attached to tags, and thus cannot be searched \
automatically when providing tags as source, you must provide a file as \
input to the script.

Neither the column for the objects name or the objects index were found
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Make sure that the column in your .csv match the columns given as parameter \
of the import script. Both are optional, but at least one is required!

No .csv FileAnnotation was found on <OBJ_TYPE>:<OBJ_ID>
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When providing no file from the select File button, nor giving \
a file annotation to read Key-Value pairs from, the script attempt to \
search specifically for a .csv file attached to the current parent object.
If none is found, you obtain this error. Try to provide a .csv file instead \
of letting the script guessing.

Number of Source IDs and FileAnnotation IDs must match
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When providing more than one parent object, the Key-Value pairs can \
be read from either a single .csv file, or by multiple files. In the later \
scenario, there must be an identical number of FileAnnotation and parent \
objects, in order for the script to understand which corresponds to which.

Please confirm that you understood the risks
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
It seems that you forgot to confirm that you understood the risk associated \
with a batch deletion of annotations. TODO cf to section on why ticking the box.

Target objects identified by name have duplicate
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Because no column specifying the ID of the object to annotate was found, \
the script attempted to uniquely identify the objects by their name. It seemed \
however that in the list of all objects founds from the parent you gave, \
multiple objects have the same name. Please try again by adding a column \
with the IDs of the objects to annoate. (OBJECT_ID is the default of the \
scripts).

The provided annotation ID must reference a FileAnnotation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The ID of the file annotation seems incorrect. Make sure that you gave the \
FileAnnotation ID and not the LinkAnnotation ID, as indicated in the image bellow.

.. image:: images/expert_3_file_annotation_id.png
   :scale: 100%

The tag ID:{tagid} is not in the permitted selection of tags
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
This error either means that the given ID for the tag is wrong, or that the ID \
corresponds to a tag in a different group or belonging to a different user (and \
option 'Use only personal tags' is unchecked). Another possibility is that you have \
a tagset with a name made of numbers only, and thus is interpreted as a tag ID.

The tag {tagname} doesn't correspond to the tag on the server with ID:{tagid}
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
This error tells you that the tag found from the given ID has a name different \
from the one you used in the csv. This is to prevent you from using the wrong tag.

Tag '{tagname}' does not exist while creation of new tags is not permitted
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
If your tags do not exist yet (or if you only use your own tag), remember to \
check the box 'Create new tags' if you wish to generate the tags automatically.

Tag '{tagname}' in TagSet '{tagset}' does not exist while creation of new tags is not permitted
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Same as the error above, but in the case a tagset is specified.

The .csv contains duplicates {duplicates} which makes it impossible to correctly allocate the annotations
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When no ID is used to identify the objects to annotate, names are use instead. In that case, there can not \
be two object with the same name in the csv (and in the selected object on OMERO), in which case it is \
impossible to identify which object should be annotated.

Grep a pattern (ignoring case) in specific files::

    grep -ri --include <files> <pattern>     # -r is recursive; -i ignores case
    grep -ri --include \*.xml <pattern>      # \*.xml for any XML file
    grep -ri --include test.xml <pattern>    # For all files named test.xml

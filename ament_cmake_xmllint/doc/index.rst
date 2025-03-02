ament_xmllint
=============

Checks XML markup files using `xmllint <http://xmlsoft.org/xmllint.html>`_.
Files with the following extensions are being considered: ``.xml``.


How to run the check from the command line?
-------------------------------------------

The command line tool is provided by the package `ament_xmllint
<https://github.com/ament/ament_lint>`_.


How to run the check from within a CMake ament package as part of the tests?
----------------------------------------------------------------------------

``package.xml``:

.. code:: xml

    <buildtool_depend>ament_cmake</buildtool_depend>
    <test_depend>ament_cmake_xmllint</test_depend>

``CMakeLists.txt``:

.. code:: cmake

    find_package(ament_cmake REQUIRED)
    if(BUILD_TESTING)
      find_package(ament_cmake_xmllint REQUIRED)
      ament_xmllint(
        # PATHS .
        # EXCLUDE specific_file.xml
        # EXTENSIONS xml urdf xacro
      )
    endif()

When running multiple linters as part of the CMake tests the documentation of
the package `ament_lint_auto <https://github.com/ament/ament_lint>`_ might
contain some useful information.

When you want to customize the extensions of the files to be checked, while using `ament_lint_auto`, you can use the following code snippet:

``CMakeLists.txt``:

.. code:: cmake

    find_package(ament_cmake REQUIRED)
    if(BUILD_TESTING)
      find_package(ament_lint_auto REQUIRED)
      set(ament_cmake_xmllint_EXTENSIONS "xml urdf xacro")
      ament_lint_auto_find_test_dependencies()
    endif()

The documentation of the package `ament_cmake_test
<https://github.com/ament/ament_cmake>`_ provides more information on testing
in CMake ament packages.

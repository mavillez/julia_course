Filesystem Navigation
=====================

Print the current directory

.. code-block:: julia

  julia> pwd()
  
Change to the parent directory (in Linux and MacOS)

.. code-block:: julia
  
  julia> cd("<Folder Name>") 
  
In windows Change to ``C:\``

.. code-block:: julia
  
  julia> cd("C:/")

List the contents of a directory

.. code-block:: julia
  
  julia> readdir()
  
Make a new directory

.. code-block:: julia

  julia> mkdir("<folder_name>")

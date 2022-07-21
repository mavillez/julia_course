Filesystem Navigation
=====================

Print the current directory

.. code-block:: julia

  julia> pwd()
  
  
To learn about what ``pwd`` does just use ``help`` in the prompt

.. code-block:: julia

  help?> pwd
  search: pwd powermod
  
    pwd() -> AbstractString
  
    Get the current working directory.
  
    See also: cd, tempdir.
  
    Examples
    ≡≡≡≡≡≡≡≡≡≡
    julia> pwd()
    "/home/JuliaUser"

  
Change to the parent directory (in Linux and MacOS)

.. code-block:: julia
  
  julia> cd("<Folder Name>") 
  
In windows Change to ``C:\``

.. code-block:: julia
  
  julia> cd("C:/")
  
To learn more on ``cd`` just ask for ``help``  
  
.. code-block:: julia

  help?> cd
  search: cd Cdouble gcd gcdx secd asecd cld 
  Cmd codeunit codeunits codepoint code_llvm
  
    cd(dir::AbstractString=homedir())
  
    Set the current working directory.
    
    See also: pwd, mkdir, mkpath, mktempdir.
  
    Examples
    ≡≡≡≡≡≡≡≡≡≡
  
    julia> cd("/home/JuliaUser/Projects/julia")


List the contents of a directory

.. code-block:: julia
  
  julia> readdir()
  
Make a new directory

.. code-block:: julia

  julia> mkdir("<folder_name>")

Input/Output
============

Opening and Reading a File in Julia
-----------------------------------

File handling in Julia is achieved using functions such as open(), read(), close().

* open(): To open a file existing in an absolute path, provided as the parameter.
* read(): Read the contents of the file into a single string.
* close(): Close the file object or the variable holding the instance of an opened file.

Read the contents of a file use: 

* readline()
* readlines()
* read()

Opening a file
--------------

**Method 1**

.. code-block:: julia

  f = open("cars.txt", "r")       # Opening a file in read_mode “r”
    # do some file operations
  close(f)                        # close the file instance
  
**Method 2**

.. code-block:: julia

  open("cars.txt") do f         # opening a file in read_mode and cycle through the lines
    # do stuff with the open file instance 'f'
  end

The opened file is automatically closed after the “do control” ends.

Reading the file contents
-------------------------

**Read the file contents line by line (one line at a time) using readline() function**

.. code-block:: julia

  open("cars.txt") do f
    line = 0                      # line_number
    while ! eof(f)                # read till end of file
      s = readline(f)             # read a new line for every iteration
      println("$s")               # print the line
    end
  end

obtaining

.. code-block:: console

  Brand           Price  Year
  Honda Civic     22000  2015
  Toyota Corolla  25000  2013
  Ford Focus      27000  2018
  Audi A4         35000  2018
  
**Count the lines and print the line number**

.. code-block:: julia
  
  open("cars.txt") do f
    line = 0                      # line_number
    while ! eof(f)                # read till end of file
        
      s = readline(f)              # read a new line for every iteration
      line = line + 1 
      println("$line . $s")
    end 
  end

giving

.. code-block:: console

  1 . Brand           Price  Year
  2 . Honda Civic     22000  2015
  3 . Toyota Corolla  25000  2013
  4 . Ford Focus      27000  2018
  5 . Audi A4         35000  2018
  
**Reading all the lines of a file into a String array using readlines()**

.. code-block:: julia

  f = open("cars.txt", "r")      # opening a file in read_mode “r” 
  line_count = 0                 # to count total lines in the file 
  for lines in readlines(f)    
    global line_count = line_count + 1    # Define the line_count variable global and increment it
    println(lines)                        # print the line
  end
  println("line count is $line_count")    # total lines in file
  close(f)
  
obtaining  
  
.. code-block:: console  

  Brand           Price  Year
  Honda Civic     22000  2015
  Toyota Corolla  25000  2013
  Ford Focus      27000  2018
  Audi A4         35000  2018
  line count is 5
  
**Read all contents of a file into a String at once using read()**

.. code-block:: julia

  f = open("cars.txt", "r")             # opening a file in read mode “r”
  s = read(f, String)                   # read entire file into a string
  print(s)                            
  close(f)
  
obtaining

.. code-block:: console
  
  Brand           Price  Year
  Honda Civic     22000  2015
  Toyota Corolla  25000  2013
  Ford Focus      27000  2018
  Audi A4         35000  2018

Writing into a file
-------------------

.. code-block:: julia
  
  output=open(“output_file.txt","w")      # opening a file in write mode “w”
  write(output, “BMW  40000  2021\n")     # write some data into the file
  close(output)

Check the presence of the file in the disk by chaning to the `shell` environment by

.. code-block:: julia

  julia>;
  
obtaining  
  
.. code-block:: julia
  
  shell>
  
Now just use `ls` to list the files in the directory and `cat output_file.txt` to see the file contents

.. code-block:: julia
  
  shell> ls
  
giving

.. code-block:: console
  
  DataFrames-RDatasets.pages
  DataFrames-RDatasets.pdf
  Dataframes.pages
  Input_Output.pages
  Input_Output.pdf
  Julia_introduction.ipynb
  Session 1 - Introduction Solved.ipynb
  Session 2 - Files and Data.ipynb
  Session-2
  Session-3
  cars.txt
  output_file.txt
  
and 

.. code-block:: julia
  
  shell> cat output_file.txt
  
to give

.. code-block:: console
  
  BMW  40000  2021


.. warning::
  
  Accessing the shell commands is a little bit different in the command line console (also known as `terminal`) and in Jupyter notebook.

  In CLI we only need to type `;` in front of the julia> prompt

  .. code-block:: julia
  
    julia> ;
  
  then appears the shell prompt

  .. code-block:: julia
  
    shell>
  
  Now one can type the shell commands as wish.

  In Jupyter notebook one need to type `;` followed with the shell command in the same line, say list the folder contents using `ls`:

  .. code-block:: julia

    ; ls
  
  

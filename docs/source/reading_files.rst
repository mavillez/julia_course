
Opening and Reading a File in Julia
-----------------------------------

File handling in Julia is achieved using functions such as open(), read(), close().

* open(): To open a file existing in an absolute path, provided as the parameter.
* read(): Read the contents of the file into a single string.
* close(): Close the file object or the variable holding the instance of an opened file.

Read the contents of a file use: readline(), readlines() or just read().

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

Read the file contents line by line (one line at a time) using readline() function

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
  
Count the lines and print the line number
-----------------------------------------

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
  
Reading all the lines of a file into a String array using readlines()
---------------------------------------------------------------------

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

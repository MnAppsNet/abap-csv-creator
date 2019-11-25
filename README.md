# ABAP CSV Creator
A simple static class to make the creation of a csv file easy in ABAP

# How to use :

#### To add an instraction on what sould the output has (they are column instractions, so for every instraction you add a column) :

**cl_save_to_csv=>add_instraction( table_reference , column_header, column_name, fixed_value )** 
  - table_reference : the table from which the value will be taken for the output
  - column_name     : the name of the field in the table_reference table that you want to get the value for the output
  - column_header   : the header of the column that will be shown on the output (*optional*)
  - fixed_value     : set to 'X' if you want to have a fixed value on the column, the fixed value will be the value of column_name

#### To get the table with the instraction :

**DATA(instraction_table) = cl_save_to_csv=>get_instraction_table( )**
  - the returning value is of type **ty_instraction_t** which is declared in the class.

-> Set instractions from table :

**cl_save_to_csv=>add_instraction_table( instraction_table )**
  - set the instractions from the table instraction_table of type **ty_instraction_t** which is declared in the class

#### Clear all the instractions :

**cl_save_to_csv=>clear_instractions( )**

#### Set the seperator between the columns :

**cl_save_to_csv=>set_seperator( S )**
  - set the seperator to be char S. Default seperator is ';'
  
#### Get the output csv : 

**Data(lt_csv) = cl_save_to_csv=>get_output( )**
  - The returning value is of type **standard table of string** and contains all the rows of the output csv file. You can loop into it and write all the data to an output file.
  
  

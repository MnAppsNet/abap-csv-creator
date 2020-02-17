# ABAP CSV Creator
A simple static class to make the creation of a csv file easy in ABAP

# How to use :

#### To add an instruction on what sould the output has (they are column instructions, so for every instruction you add a column) :

**cl_save_to_csv=>add_instruction( table_reference , column_header, column_name, fixed_value )** 
  - table_reference : the table from which the value will be taken for the output
  - column_name     : the name of the field in the table_reference table that you want to get the value for the output
  - column_header   : the header of the column that will be shown on the output (*optional*)
  - fixed_value     : set to 'X' if you want to have a fixed value on the column, the fixed value will be the value of column_name
___
#### To get the table with the instruction :

**DATA(instruction_table) = cl_save_to_csv=>get_instruction_table( )**
  - the returning value is of type **ty_instruction_t** which is declared in the class.

-> Set instructions from table :

**cl_save_to_csv=>add_instruction_table( instruction_table )**
  - set the instructions from the table instruction_table of type **ty_instruction_t** which is declared in the class
___
#### Clear all the instructions :

**cl_save_to_csv=>clear_instructions( )**
___
#### Set the seperator between the columns :

**cl_save_to_csv=>set_seperator( S )**
  - set the seperator to be char S. Default seperator is ';'
___  
#### Get the output csv : 

**Data(lt_csv) = cl_save_to_csv=>get_output( )**
  - The returning value is of type **standard table of string** and contains all the rows of the output csv file. You can loop into it and write all the data to an output file.
  
  

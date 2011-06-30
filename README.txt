README.TXT


                 GWM-2000 - Version: 1.1.4 6/31/2011
                 Built from MODFLOW-2000 Version 1.17.02
       Three-dimensional finite-difference groundwater flow model
                                With
                  Groundwater Management (GWM) Process


NOTE: Any use of trade, product or firm names is for descriptive 
purposes only and does not imply endorsement by the U.S. Government.

This version of MODFLOW-2000 with the GWM Process is packaged for 
personal computers using Microsoft Windows 95, 98, ME, NT, 2000, or XP.



                            TABLE OF CONTENTS

                         A. DISTRIBUTION FILE
                         B. EXTRACTING FILES
                         C. COMPILING
                         D. INSTALLING
                         E. RUNNING THE SOFTWARE
                         F. TESTING


A. DISTRIBUTION FILE

The following self-extracting distribution file is for use on personal
computers:

         gwm2000.1_1_4.exe

The distribution file contains:

          Compiled DOS executable and source code for GWM-2000.
          GWM documentation and input instructions in pdf files.
          Test data sets.


B. EXTRACTING FILES

The distribution file is a self-extracting program.  Execution of the
distribution file creates numerous individual files.  The extraction
program allows you to specify the directory in which the files should
be restored. The following directory structure will be created in the 
directory that you specify:


   |
   |--gwm2000.1_1_4
   |    |--bin       ; compiled executable
   |    |--data      ; standard data sets used in verification tests
   |    |--doc       ; documentation files
   |    |--src       ; source code
   |    |--test-win  ; batch files to run verification tests


It is recommended that no user files are kept in the gwm2000.1_1_4 
directory structure.  If you do plan to put files in the gwm2000.1_1_4 
directory structure, do so only by creating subdirectories.

Included in directory gwm2000.1_1_4\doc is a Portable Document Format 
(PDF) file. The PDF file is readable and printable on various computer 
platforms using Acrobat Reader from Adobe. The Acrobat Reader is freely 
available from the following World Wide Web sites:
      http://www.adobe.com/
      http://www.shareware.com/
Also, included in gwm2000.1_1_4\doc is a PDF file called "GWM Addendum" which 
contains information on modifications to GWM since the publication of the
primary documentation.


C. COMPILING

Although an executable version of the program is provided, the source 
code is available in the gwm2000.1_1_4\src directory so that the 
programs can be recompiled if necessary.  However, no support can be 
provided for users generating their own versions of the software. 

In general, the requirements for compiling GWM-2000 are a Fortran 
compiler, a C compiler, and the knowledge of using the compilers.  The 
Fortran source-code files (files ending in .f, .for .inc, or .com) must be 
compiled with a Fortran (90 or 95) compiler.  To compile GWM-2000 with 
the GMG Package, the source-code files written in the C language (files 
ending in .c or .h) must be compiled with a C compiler and all the 
resulting object files must be linked together.  Alternatively, calls to 
GMG subroutines may be removed from mf2k.f, and the Fortran source-code 
files may be compiled with only a Fortran compiler.  If the calls to GMG 
subroutines are removed, the GMG Package will not be available when 
GWM-2000 is run.  For tips on compiling the mixed-language code of 
GWM-2000 with various compilers, see:
      http://water.usgs.gov/nrp/gwsoftware/modflow2000/MFDOC/Compiling.html
and follow instructions for compiling MODFLOW-2000.

GWM uses FORTRAN 90 MODULE structures and USE statements to define and 
access variables between packages.  During compilation, it is important 
that modules that will be accessed by other packages are compiled 
first.  That is, the order of compilation is important.  Some 
compilers, such as Compaq Visual Fortran, allow multiple compilation 
passes so that modules not available on a first pass will be available 
on subsequent passes.  However, other compilers may have difficulty 
with this.

To facilitate one-pass compilation, two of the GWM packages are divided 
into two separate files: The GWM1BAS1 package consists of the GWM1BAS1 
and GWM1BAS1SUBS files and the GWM1RMS1 package consists of the 
GWM1RMS1MOD and GWM1RMS1 files. The files distributed with GWM should 
be compiled in the following order:
     GWM1BAS1
     GWM1RMS1MOD
     GWM1DCV1
     GWM1OBJ1
     GWM1DCC1
     GWM1HDC1
     GWM1STC1
     GWM1SMC1
     GWM1RMS1
     GWM1BAS1SUBS
     GWM2000

It is important when compiling GWM-2000 to enforce default double precision 
for all REAL variables.  This is needed to obtain adequate precision in 
perturbation calculations.  For the executable file in the \bin directory, 
which was compiled with the Intel Fortran Compiler Integration for Microsoft 
Visual Studio 2005, this was accomplished using the default Release configuration, 
with the exception that the default REAL KIND is set to 8, so that all real 
variables are treated as double precision. 


D. INSTALLING 

To make the executable versions of the programs accessible from any
directory, the directory containing the executable (gwm2000.1_1_4\bin)
should be included in the PATH environment variable. For example, you 
could add the following line to the AUTOEXEC.BAT file on Windows9x and 
Windows ME systems:

  PATH=%PATH%;C:\GWMpathname\gwm2000.1_1_4\bin

Where GWMpathname is the directory path you selected for installing 
GWM-2000.

Note, reboot your system after modifying AUTOEXEC.BAT.

On Windows NT systems, from the Start menu, select Settings and then
Control Panel. Double-click System and select the Environment tab.
To add a new user variable, enter "PATH" in the Variable field and 
enter

   %PATH%;C:\GWMpathname\gwm2000.1_1_4\bin

in the Value field.  Click Set and then click OK.  If a PATH user 
variable already is defined, click on it in the User Variables pane, 
add ";C:\GWMpathname\gwm2000.1_1_4\bin" to its definition in the Value 
field, and click OK. Initiate and use a new MS-DOS Command Prompt 
window after making this change.

On Windows 2000 or XP systems, from the Start menu, select Settings and 
then Control Panel. Double-click System and select the Advanced tab.  
Click on Environment Variables. If a PATH user variable already is 
defined, click on it in the User Variables pane, then click Edit. In 
the Edit User Variable window, add ";C:\GWMpathname\gwm2000.1_1_4\bin" 
to the end of the Variable Value(ensure that the current contents of 
the User Value are not deleted) and click OK. If a PATH user variable 
is not already defined, in the User variables pane of the Environment 
Variables window, click New. In the New User Variable window, define a 
new variable PATH as shown above. Click OK. Click OK in the Environment 
Variables window and again in the System Properties window. Initiate 
and use a new MS-DOS Command Prompt window.


E. RUNNING THE SOFTWARE

GWM with GWM has been compiled using the Intel Fortran
Compiler Integration for Microsoft Visual Studio 2005, Version 
9.1.3427.2005.  The C source code was compiled with Microsoft Visual C++ 
2005.

The data arrays in GWM2000, as with MODFLOW-2000, are dynamically 
allocated, so models are not limited by hard-coded array limits. 
However, it is best to have enough random-access memory (RAM) available 
to hold all of the required data. If there is less available RAM than 
this, the program will use virtual memory, but this slows computations 
significantly.

After the files in the gwm2000.1_1_4\bin directory are installed in a
directory that is included in your PATH, the programs are initiated in
a DOS Command-Prompt window using the commands:

          gwm2000 [Fname]

The optional Fname argument is the MODFLOW name file. If no argument is 
used, the user is prompted to enter the name file. If the name file 
ends in ".nam", then the file name can be specified without including 
".nam".  For example, if the name file is named abc.nam, then the 
simulation can be run by entering:

          gwm2000 abc

As an alternative, you can copy the executable (gwm2000.exe) into the 
directory in which your model input files are located (including all of 
the required GWM input files) and double-click on the executable. This 
will activate the program, which will prompt you for the name of the 
MODFLOW name file. 


F. TESTING

Data files for four test problems are provided to confirm that 
MODFLOW-2000 with GWM is correctly installed and running on the system.  
The tests may also be looked at as examples of how to use the program.  
The directory gwm2000.1_1_4\data contains the input data and expected 
results for the tests.

The directory gwm2000.1_1_4\test-win can be used to conveniently run the
tests without destroying the original results in the gwm2000.1_1_4\data
directory. The gwm2000.1_1_4\test-win directory contains batch (BAT) 
files to run the tests.  Each test can be run by entering the name of 
the test as a command in a DOS command-prompt window with the current 
directory being gwm2000.1_1_4\test-win or by double-clicking on the 
corresponding BAT file in Windows Explorer.  The output files that are 
created in gwm2000.1_1_4\test-win can then be compared to those in 
gwm2000.1_1_4\data.  

The four tests are described in the GWM documentation report (USGS 
Open-File Report 2005-1072).  The supply2 problem is a revised version 
of the original supply problem.  See the GWM Addendum for discussion 
of the revision:


test name      description of test
------------   -------------------------------------------------------
 dewater       DEWATER sample problem, linear formulation
 dewatermb     DEWATER sample problem, mixed-binary linear formulation
 seawater      SEAWATER sample problem, nonlinear formulation
 supply2       SUPPLY sample problem, nonlinear formulation

Ahlfeld, D.P., Barlow, P.M., and Mulligan, A.E., 2005, GWM—A ground-
water management process for the U.S. Geological Survey modular ground-
water model (MODFLOW-2000): U.S. Geological Survey Open-File Report 
2005-1072, 124 p.

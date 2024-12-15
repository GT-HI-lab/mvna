# Installation

This repo is forked from rcraggs/mvna but just with custom documentation on how to run it, since the original repo doesn't have it.

Clone this repository into your desired workspace first: ``git clone https://github.com/rcraggs/mvna.git``

Or download the ZIP if you're not familiar with the terminal.

This code is a Java application packaged in [IntelliJ IDEA](https://www.jetbrains.com/idea/download/), a Java IDE used particularly to develop Java apps. You will need to install IntelliJ IDEA onto your computer. Extended usage requires a license, but there is a free trial for about a month that you can start with.

# Loading the GUI 
Once IntelliJ IDEA is installed, open the application and complete any initialization, if it's your first time installing. From IDEA, open the repo folder from the workspace where you installed it.

The GUI specifically is housed in ``src/multiValuedNominalAlpha/ui/Gui.java``. Once you navigate to this file, you will see in IntelliJ a little green arrow near the top right corner that says "Run" when you hover over it. Press this button to run the GUI. You should see a GUI pop-up automatically after pressing the arrow.

# Formatting your data file

For best results, format your data as CSV (e.g. export your Excel sheet as CSV). Other file formats are supported but it plays nicest with CSV. According to the original authors, "Any text file containing tabular data can be opened including tab delimited and comma separated files."

Before you export to CSV, replace any *empty cells* to {}, since {} represents an empty set in the program. If you intend for a cell to have a NULL or zero value, write that in explicitly.

For cells that have *multiple items* (e.g. cell value is "1, 3, 4"), make sure that each individual value within the cell is delimited with the pipe operator, |, and that all whitespace is removed. For instance, if your cell value is "1, 3, 4", it should be reformatted to "1|3|4". Other delimiters like commas work in theory, but when I tested it with anything but the pipe operator as delimiter, the alpha was calculated incorrectly.

# Loading files into the GUI

Once you locate and load your desired file, you need to set some parameters in the GUI so that it can properly read your file. At the top bar, you will see formatting parameters, four of which are relevant: Row, Column, Value Separator, and Unit Separator.

Row and Column indicate the row and column at which your data frame starts. You can change this if in our original file, the first row and column are header, which it typically is. For example, starting both Row and Column at 2 takes out the header row and column. *This does not modify the original file – only how it is fed to the GUI.*

Unit Separator should be set to "|", which is a dropdown option. This lets you denote what operator distinguishes different units of data in your file. This is critical, as calculating the MVNA is dependent on the program identifying which values are distinct. Value Separator can just be set to comma – this doesn't seem to matter.

Press the Run button up at the top, and you should see the reliability alpha value calculated in the console output at the bottom. If you want to see a detailed log of the alpha calculation, check "Log calculations" next to the Run button. Note that if your file is large (lots of data), this will significantly slow down the calculation and in some cases crash the program if the dataset is overly large.

If you want to see additional statistics related to the reliability calculation (e.g. disagreements between specific codes) feel free to check out the other tabs at the bottom.

*This document was authored by Stephanie Kim.*

Download Link: https://assignmentchef.com/product/solved-ccu-oop-homework-6-account-portfolio
<br>
<strong>HW #6 </strong><strong>(Account Portfolio</strong><strong>)</strong>

<ul>

 <li>You will design a set of classes for storing information regarding bank accounts, along with a class that will manage a list of accounts.</li>

 <li>Data must be imported from files for storage in the list, and summary reports with computed balances must be saved to output files.</li>

 <li>You are expect to do the work in C++ (or Java if you prefer).</li>

</ul>

<h1>HW #6</h1>

<h2>Classes Details</h2>

<ul>

 <li>Design a set of classes to store bank account information. There should be one base class called <strong>Account </strong>to store common data about bank accounts, and three derived classes that divide the set of accounts into three categories: <strong>Savings</strong>, <strong>Checking</strong>, and <strong>Investment </strong></li>

 <li>All data stored in these classes should be <strong>private </strong>or <strong>protected</strong>. Any access to class data from outside (besides accessing base class data from derived classes) should be done through <strong>public </strong>member functions. Make use of <strong>virtual </strong>and <strong>abstract </strong>functions wherever appropriate.</li>

 <li>The base class <strong>Account </strong>should allocate storage for the following data (and only this data): Account holder’s <strong>first name </strong>(you may assume it is up to 20 characters long), account holder’s <strong>last name </strong>(you may assume it is up to 20 characters long), the <strong>type </strong>of account (<strong>Savings</strong>, <strong>Checking</strong>, or <strong>Investment</strong>).</li>

 <li>Each class (base class and derived classes) should have a function that will compute and return the account’s projected balance based on the stored information. All balances are in <strong>dollars</strong>.</li>

 <li>Here is the information that needs to be stored for each account, along with the breakdown for computing each projected balance:</li>

</ul>

<h1>HW #6</h1>

<ul>

 <li><strong>Savings Account </strong></li>

 <li>Stores: — Current Balance</li>

</ul>

— Interest rate

ProjectedBalance = CurrentBalance * (1 + Interest rate)

<ul>

 <li><strong>Checking Account </strong></li>

 <li>Stores: — Current Balance</li>

</ul>

ProjectedBalance = CurrentBalance + 0.1

<ul>

 <li><strong>Investment Account </strong></li>

 <li>An investment account is made up of <strong>five </strong>ExchangeTraded Funds (ETFs). The investment class should store the information for the five ETs. Each ETF has the following four pieces of information: 1) amount invested (A), 2) initial value per share (IVS), 3) current value per share (CVS), and 4) interest rate (I).</li>

 <li>The projected balance of the investment account is given by the current value (CV) of the five ETFs + their dividends.</li>

</ul>




<ul>

 <li>The current value of an ETF is computed as follows: CV = ( A / IVS ) * CVS</li>

 <li>The dividends yielded by each ETF is computed as follows:</li>

</ul>

DIV = I * A

<ul>

 <li>The projected balance of an investment account is computed as follows: (5 ETFs)</li>

</ul>

ProjectedBalance =   ∑   ( CV + DIV )

ETFs

<ul>

 <li>Write a class called <strong>Portfolio</strong>, which will be used to store the list of various accounts, using <strong>a single array of flexible size</strong>.</li>

 <li>Note that this array will act as a <strong>heterogeneous </strong>list, and it will need to be dynamically managed. Each item in the array should be an <strong>Account </strong>pointer (so you will have a dynamically allocated array of <strong>Account </strong>pointers, i.e., <strong>Account** alist</strong>), which should point to the appropriate type of object.</li>

 <li>Your list should only be big enough to store the accounts currently in it.</li>

 <li>Your <strong>Portfolio </strong>class needs to have at least the following public functions available:</li>

 <li><strong>Portfolio() </strong>— default constructor. Sets up an empty list of accounts.</li>

 <li><strong>~Portfolio() </strong>— destructor. Needs to clean up all dynamically allocated data being managed inside a <strong>Portfolio </strong>object, before it is de-allocated<em>.</em></li>

 <li><strong>bool importFile(const char* filename) </strong></li>

 <li>This function should add all data from the file given as parameter into the internally managed list of accounts. The file format is specified below in this write-up. Note that if there is already data in the list from a previous import, this call should add MORE data to the list. Records should be added at the end of the given list in the same order they appear in the input file.</li>

 <li>If the file does not exist or cannot be opened, return false to indicate failure of the import. Otherwise, after importing the file, return true for success.</li>

</ul>




<h1>HW #6</h1>

<ul>

 <li><strong>bool createReportFile(const char* filename) </strong></li>

 <li>This function should create a banking report and write it to the given output file (filename given in the parameter). The format of the banking report file is described below in this write-up. If the output file cannot be opened, return false for failure. Otherwise, after writing the report file, return true for success.</li>

</ul>

<h1>HW #6</h1>

<ul>

 <li><strong>void showAccounts() const </strong></li>

 <li>This function should print to the screen the current list of accounts, one account per line. The only information needed in this printout is last name, first name, account type, and current balance (in the case of investment accounts, instead of current balance you will print <strong>the total amount invested</strong>, i.e., the sum of the invested amounts (A) in the five ETFs). Format this output so that it lines up in columns.</li>

</ul>

<h1>HW #6</h1>

<ul>

 <li>Write a main menu program in a separate file called <strong>main.cpp </strong>that creates a single <strong>Portfolio </strong>object and then implements a menu interface to allow interaction with the object. Your main program should implement the following menu loop (any single letter options should work on both <strong>lower</strong>– and <strong>upper</strong>-case inputs):</li>

</ul>

<strong>*** Portfolio Management menu *** </strong>

<strong>I         Import accounts from a file </strong>

<strong>S        Show accounts (brief) </strong>

<strong>E        Export a banking report (to file) </strong>

<strong>M        Show this menu </strong>

<strong>Q        Quit program</strong>




<ul>

 <li>The import and export options should start by asking for user input of a filename (you may assume it will be up to 30 characters long, no spaces), then call the appropriate class function for importing accounts from a file or printing the banking report to a file, respectively.</li>

 <li>The program must print a message indicating the task was unsuccessful if the import/export fails.</li>

 <li>The “Show accounts (brief)” option should call the class function that prints the brief account info to screen (names, account type, and current balance/invested amount only).</li>

</ul>

<h1>HW #6</h1>

<ul>

 <li>The “Show this menu” option should re-display the menu.</li>

 <li>“Quit” should print “Goodbye” and exit program. (Until this option is selected, keep looping back for menu selections.)</li>

 <li><strong>Input File </strong>— The first line of the input file to import accounts from will contain the number of accounts listed in the file. This will tell you how many accounts are being imported from this file.</li>

 <li>After the first line, every set of two lines constitutes a single account entry. The first line of an entry is the account holder’s full name, in the format lastName, firstName. Note that a name could include spaces — the comma will delimit last name from first name.</li>

</ul>




<ul>

 <li>The second line will contain the type of account (“Savings”, “Checking”, or “Investment”), followed by a list of account information, all separated by spaces. There will be no extra spaces at the end of the line in the file. The order of the account information for each type is as follows:</li>

 <li>for Savings accounts: current Balance, then Interest rate (the values on a line will be separated by space).</li>

 <li>for Checking accounts: current Balance.</li>

 <li>for Investment accounts: 1) amount invested for ETF1, 2) initial value for ETF1, 3) current value for ETF1, 4) interest rate for ETF1;</li>

</ul>

1) amount invested for ETF2, 2) initial value for ETF2, 3) current value for ETF2, 4) interest rate for ETF2;

1) amount invested for ETF3, 2) initial value for ETF3, 3) current value for ETF3, 4) interest rate for ETF3;

1) amount invested for ETF4, 2) initial value for ETF4, 3) current value for ETF4, 4) interest rate for ETF4;

1) amount invested for ETF5, 2) initial value for ETF5, 3) current value for ETF5, 4) interest rate for ETF5. (The values on a line will be separated by space.)




<table width="864">

 <tbody>

  <tr>

   <td width="864"><strong>Example </strong><strong>1 </strong><strong>of input file </strong>(test1.txt)4Alfaro, Emily-GraceSavings 900.89 0.001Morgan, ArthurChecking 89Dipwart, MarvinInvestment 40 80 80.84 0.02 45 20 20 0.2 150 76.3 76 0.0545 80 76 0.07 408 5 100 0.9 van Houten, Milhouse Savings 45.80 0.79</td>

  </tr>

 </tbody>

</table>







<table width="864">

 <tbody>

  <tr>

   <td width="864"><strong>Example </strong><strong>2 </strong><strong>of input file </strong>(test2.txt)2Polar Bear, MayaChecking 40.90Polar Bear, MayaSavings 60.72 7.8</td>

  </tr>

 </tbody>

</table>

<h1>HW #6</h1>

<ul>

 <li><strong>Output File </strong>— The output file that you print should list each account holder’s name (firstName lastName – no extra punctuation between), Initial Balance, and projected balance. All the balances should be printed to <strong>two </strong>decimal places.</li>

 <li>The Output should be separated by subject, with an appropriate heading for each section, and each account’s information listed on a separate line, in an organized fashion.</li>

</ul>

<h1>HW #6</h1>

<ul>

 <li>The order of the accounts within any given category should be the same as they appear in the portfolio.</li>

 <li>Data must line up appropriately in columns when multiple lines are printed in the file.</li>

 <li>At the bottom of the output file, print the account distribution of ALL accounts in the portfolio (i.e., how many Saving accounts, Checking accounts, and Investment accounts there are) and the average projected value per type of account.</li>

</ul>




<table width="864">

 <tbody>

  <tr>

   <td width="864"><strong>Sample run of Portfolio management program.</strong>It includes screen input and output, where the keyboard input start with “&gt;” here to differentiate output from input.*** Portfolio Management menu ***I         Import accounts from a fileS        Show accounts (brief)E        Export a banking report (to file)M  Show this menu Q     Quit Program&gt; iEnter filename: test1.txt</td>

  </tr>

 </tbody>

</table>




<table width="864">

 <tbody>

  <tr>

   <td width="586">&gt; sHolder                               Type</td>

   <td width="278">Balance</td>

  </tr>

  <tr>

   <td width="586">  Alfaro Emily Grace             Savings</td>

   <td width="278">900.89</td>

  </tr>

  <tr>

   <td width="586">  Morgan Arthur                   Checking</td>

   <td width="278">89.00</td>

  </tr>

  <tr>

   <td width="586">  Dipwart Marvin                  Investment</td>

   <td width="278">688.00</td>

  </tr>

  <tr>

   <td width="586">  van Houten Milhouse         Savings&gt; IEnter filename: banking.txtInvalid file. No data imported&gt; IEnter filename: test2.txt</td>

   <td width="278">45.80</td>

  </tr>

 </tbody>

</table>




<table width="864">

 <tbody>

  <tr>

   <td width="394">&gt;SHolder</td>

   <td width="192">Type</td>

   <td width="278">Balance</td>

  </tr>

  <tr>

   <td width="394">Alfaro Emily Grace</td>

   <td width="192">Savings</td>

   <td width="278">900.89</td>

  </tr>

  <tr>

   <td width="394">Morgan Arthur</td>

   <td width="192">Checking</td>

   <td width="278">89.00</td>

  </tr>

  <tr>

   <td width="394">Dipwart Marvin</td>

   <td width="192">Investment</td>

   <td width="278">688.00</td>

  </tr>

  <tr>

   <td width="394">van Houten Milhouse</td>

   <td width="192">Savings</td>

   <td width="278">45.80</td>

  </tr>

  <tr>

   <td width="394">Polar Bear Maya</td>

   <td width="192">Checking</td>

   <td width="278">40.90</td>

  </tr>

  <tr>

   <td colspan="2" width="586">  Polar Bear Maya                Savings&gt; EEnter filename: summary.txt&gt; qGoodbye!</td>

   <td width="278">60.72</td>

  </tr>

 </tbody>

</table>




<table width="864">

 <tbody>

  <tr>

   <td width="864"><strong>Sample output </strong>(summary.txt)Banking Summary————————Saving AccountsHolder’s Name                   Initial Balance   Projected Balance—————————————————————————Emily-Grace Alfaro            900.89          901.79Milhouse van Houten         45.80            81.98Maya Polar Bear                60.72            534.34</td>

  </tr>

 </tbody>

</table>




<table width="864">

 <tbody>

  <tr>

   <td width="864">Checking AccountsHolder’s Name                   Initial Balance   Projected Balance——————————————————————————Arthur Morgan                   89.00            89.10Maya Polar Bear                40.90            41.00Investment AccountsHolder’s Name                   Initial Balance   Projected Balance——————————————————————————Marvin Dipwart                  688.00          8825.23</td>

  </tr>

 </tbody>

</table>




<table width="864">

 <tbody>

  <tr>

   <td width="864">Overall Account distributionSavings:       3        –         506.04Checking:     2        –         65.05Investment: 1         –         8825.23</td>

  </tr>

 </tbody>

</table>



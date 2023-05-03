Download Link: https://assignmentchef.com/product/solved-cs1331-homework-14-stock-market
<br>
<h1>Problem Background</h1>

Many times when programming, you will come across situations where you’re trying to deal with data that doesn’t come right away. Tasks like accessing a webpage over the internet or reading through a file system need some processing time in the background before they can be done. For tasks like these, we sometimes employ event-driven programming in order to make our programs fast and reactive when the data comes back.

In this homework, you will be creating an application that keeps track of changes in a stock market database and reports information out when relevant. In our sample stock market, data might be coming in and changing in real time. When values of stocks change, we want to build a system that can reevaluate the new values of these stocks and print out updated analysis.

<h1>Solution Description</h1>

For this assignment, create the following file: StockTracker.java.

You have also been provided with Stock.java, Market.java, and Tester.java. We have a few analysis questions that you must respond to as a comment!

<strong>Provided classes/interfaces</strong>

<strong>Stock.java:</strong>

An enum that holds instances of the Stocks that we might track. You should look at the JavaDoc comments for getCompanyName and getInitialValue inside this file.

<strong>Market.java:</strong>

An interface that specifies a contract for a stock markets with stocks that change values. You should look at the JavaDocs for registerHandler inside this file. You will NOT be implementing Market yourself but you will be using instances of classes that implement Market. These instances will be created for you and passed into the methods that you create inside of StockTracker.java.

<strong>Tester.java:</strong>

This class is provided for you so that you can test your code. It contains a main method which creates an instance of Market and calls the methods inside of StockTracker. It is setup to simulate asynchronously accessing information from the actual stock market. It may be useful to read through the main method but don’t worry about the implementation details.

<strong>StockTracker Class:</strong>

<em>Instance Variables</em>:

<ul>

 <li>List&lt;Stock&gt; trackedStocks – A List of the stocks that this tracker is tracking</li>

 <li>int cutoff – The threshold for buying or selling a stock</li>

 <li>Market market – The Market that this StockTracker is tracking</li>

</ul>

All fields should be private and non-static.

<em>Constructor</em>:

<ul>

 <li>StockTracker(Market market, Stock[] stocks, int cutoff) – Takes in a an array of Stocks and adds them to trackedStocks. Afterwards, assign the instance variables market and cutoff to their respective fields. When this is done, register a buy, hold, and sell tracker on every stock passed in using the private helper methods in the class.</li>

</ul>

Constructor should be public.

<em>Methods</em>:

<ul>

 <li>getter for trackedStocks. Returns a deep copy of trackedStocks</li>

 <li>getters for market and cutoff</li>

 <li>private void registerHoldTracker(Stock stock) – Should make sure that a message is printed any time a change in the stock’s value causes it to be valued both &gt;= the stock’s initalValue and &lt;= the stock’s initialValue + cutoff. When this happens print out “{Company Name} is valued at ${value}. Hold on to what you have.”.

  <ul>

   <li>You should achieve this by registering an event handler on the market for the given stock.</li>

   <li><strong>This method must use only an instance of a named inner class when creating the handler</strong></li>

  </ul></li>

 <li>private void registerBuyTracker(Stock stock) – Should make sure that a message is printed any time a change in the stock’s value causes it to be valued &lt; the stock’s initialValue – cutoff. When this happens print out “{Company Name} just dropped to ${value}. Buy now!”.

  <ul>

   <li>You should achieve this by registering an event handler on the market for the given stock.</li>

   <li><strong>This method must use only an anonymous inner class when creating the handler</strong></li>

  </ul></li>

 <li>private void registerSellTracker(Stock stock) – Should make sure that a message is printed any time a change in the stock’s value causes it to be valued &gt; the stock’s initialValue + cutoff.</li>

</ul>

When this happens print out “{Company Name} just rose to ${value}. Sell now!”.

<ul>

 <li>You should achieve this by registering an event handler on the market for the given stock.</li>

 <li><strong>This method must use only a lambda expression when creating the handler</strong></li>

</ul>

Getters should follow best practices taught in class

<h1>Analysis Questions</h1>

Answer these at the top of StockTracker.java in a comment. Put your collab statement first and then a multiline comment with your answers.

<ol>

 <li>What are the pros and cons of using named inner classes, anonymous inner classes, and lambda expressions? (4-7 bullet points. &lt; 200 words.)</li>

 <li>Why syntactically can we use a lambda expression when we are registering an event handler for the market? (1-3 sentences. &lt; 150 words.)</li>

 <li>Why would we decide to use event driven programming to access the stock market? (2-5 sentences. &lt; 220 words)</li>

</ol>

<strong>Testing your code:</strong>

If you want to test out your own code before submitting we recommend creating a separate java file and implementing a main method there.

We have also provided sample tests in Tester.java <strong>These tests are not comprehensive!</strong>

This should be the output of Tester.java:

Apple is valued at $402. Hold on to what you have.

Pfizer is valued at $609. Hold on to what you have.

Cisco is valued at $411. Hold on to what you have.

Apple is valued at $403. Hold on to what you have.

AT&amp;T just dropped to $117. Buy now!

Pfizer just rose to $614. Sell now!

Facebook is valued at $709. Hold on to what you have.

Intel is valued at $258. Hold on to what you have.

Pfizer just rose to $622. Sell now!

Facebook just rose to $715. Sell now!

Apple is valued at $407. Hold on to what you have. General Electric just dropped to $488. Buy now!

Cisco is valued at $418. Hold on to what you have.

AT&amp;T just dropped to $121. Buy now!

Facebook just rose to $719. Sell now!

Apple just rose to $412. Sell now!

Microsoft is valued at $354. Hold on to what you have.

Intel is valued at $254. Hold on to what you have.

Cisco is valued at $420. Hold on to what you have.

Facebook just rose to $720. Sell now!

Apple just rose to $411. Sell now!

General Electric just dropped to $482. Buy now!

Intel is valued at $258. Hold on to what you have.

Intel is valued at $254. Hold on to what you have.

Ford is valued at $303. Hold on to what you have.

Apple just rose to $420. Sell now!

Cisco is valued at $411. Hold on to what you have.

AT&amp;T just dropped to $114. Buy now!

Ford is valued at $305. Hold on to what you have.

Facebook just rose to $728. Sell now!

Bank of America is valued at $300. Hold on to what you have.

General Electric just dropped to $477. Buy now!

Intel is valued at $255. Hold on to what you have.

Pfizer just rose to $630. Sell now!

Facebook just rose to $724. Sell now!

Note that Tester will not finishing running immediately because it is (fake) accessing data from the Stock Market.

Feel free to modify or create your own tests in the main method!

<h1>Allowed Imports</h1>

<ul>

 <li>You are allowed to import the following classes:</li>

 <li>util.Arrays</li>

 <li>util.ArrayList</li>

 <li>util.List</li>

 <li>util.function.Consumer</li>

</ul>

<h1>Rubric</h1>

<ul>

 <li>[100] StockTracker</li>

 <li>[3] Instance variables</li>

 <li>[6] Getters</li>

 <li>[10] Constructor</li>

</ul>

∗ [1] constructor assigns instance variables correctly

∗ [9] constructor registers all the trackers

<ul>

 <li>[20] registerBuyTracker</li>

</ul>

∗ [10] Correctly registers the handler

∗ [10] Uses an anonymous inner class

<ul>

 <li>[20] registerSellTracker</li>

</ul>

∗ [10] Correctly registers the handler

∗ [10] Uses a lambda expression

<ul>

 <li>[20] registerHoldTracker</li>

</ul>

∗ [10] Correctly registers the handler

∗ [10] Uses an instance of a named inner class <strong>– </strong>[21] Analysis Questions

<h1>Javadocs</h1>

For this assignment, you will be commenting your code with Javadocs. Javadocs are a clean and useful way to document your code’s functionality. For more information on what Javadocs are and why they are awesome, the <a href="http://www.oracle.com/technetwork/java/javase/documentation/index-137868.html">online overview</a> for them is extremely detailed and helpful.

You can generate the javadocs for your code using the command below, which will put all the files into a folder called javadoc:

$ javadoc *.java -d javadoc

The relevant tags that you need to include are @author, @version, @param, and @return. Here is an example of a properly Javadoc’d class:

<table width="632">

 <tbody>

  <tr>

   <td width="632"><strong>import </strong>java.util.Scanner;<em>/**</em>* This class represents a Dog object<em>.</em>* <strong>@author </strong>George P<em>. </em>Burdell* <strong>@version </strong><em>1.0</em><em>*/ </em><strong>public class </strong>Dog {<em>/**</em>* Creates an awesome dog <em>(</em>NOT a dawg<em>!) */</em><strong>public </strong>Dog() { …}<em>/**</em>* This method takes in two ints and returns their sum* <strong>@param a </strong>first number* <strong>@param b </strong>second number <em>* </em><strong>@return </strong>sum of a and b<em>*/</em></td>

  </tr>

  <tr>

   <td width="632"><strong>public </strong>int add(int a, int b) {…}}</td>

  </tr>

 </tbody>

</table>

A more thorough tutorial for Javadocs can be found <a href="https://cs1331.gitlab.io/cs1331-style-guide.html">here</a>. Take note of a few things:

<ol>

 <li>Javadocs are begun with /** and ended with */.</li>

 <li>Every class you write must be Javadoc’d and the @author and @verion tag included. The comments for a class should start with a brief description of the role of the class in your program.</li>

 <li>Every non-private method you write must be Javadoc’d and the @param tag included for every method parameter. The format for an @param tag is @param &lt;name of parameter as written in method header&gt; &lt;description of parameter&gt;. If the method has a non-void return type, include the @return tag which should have a simple description of what the method returns, semantically.</li>

</ol>



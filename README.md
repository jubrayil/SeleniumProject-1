# SeleniumProject-1
# Selenium-TestNG-Framework


# Introduction
Selenium TestNG Framework (Maven Project)

This is a page object model framework. Below are the features that are incorporated and their status.

1) Page Modeling Example with Scripts of Google.com and yahoo.co.in

2) Data are read from Oracle Database. 

        i)Database Connection
    
        ii)Oracle DB Read
    
        iii) Oracle DB Write

3) Read and Write from Excel File

4) Read data from Property file

5) Selenium Repository which contains all possible permutation and  combination of actions,events and etc that can be performed in a web page

6) Browser invocation (Chrome, IE and Firefox)

7) Firefox Proxy Settings

8) XML File Generation Example TestNG.XML

9) Web Services Testing Like Soap and Rest

10) TestNG Listener Implementation

11) TestNG Reporter Implementataion 

12) HTML End Report Generation- Sample is added. Required to be modified as per the project/requirement

13) Bug Tracking Tool integration - 
        
        i) QC  
 
14) Email Connection 

15) Folder Creation with Time Stamp 

16) TestNG Assertion 

17) TestNg Annotations and DataProvider 

18) Selenium Grid Implementation- Required to be added as per project/ Requirement

19) Reading a Response XML

20) Image Comparision 

21) Firefox geckodriver included

# How to use

      Understanding Various Packages included and its use. Please import this Maven project to any IDE. So that you can browse the packages and understand the description mentioned.

1) database package (com.abc.database)

        it contains code for retriving single and multiple rows from the database. Database connection details are taken from the property file (DBDetails.property). Passing proper value from property file will automatically connect to the db and return you the result set in proper manner. If your requirement is of a singleton class. Please open a case so that i can assist you accordingly
        
2) listener package ( com.abc.listener) TestNG Listner

        Use of this package is to listen any operation/event that happened during any execution. for this TestNG listner methods like onstart,onfinish,ontestpassed, onTestskipped etc are overwritten. Listener and Reporter has to be implement jointly and in a planned manner as per the requirement. So few sample features are implemented in this project. Please open a case if you require more assistance in Listener and Reporter package/functionality.
   
3) Reporter Package (com.abc.report) TestNg Reporter

        Use this package for custom reporting as per your organisation. This has to be in collabration with the Listner package. Generally all listner methods logs data as per their listened activity which is picked by the reporter at the end to prepare a consoldated report in some format like HTML, PDF. Some sample commented code are available for reference or use. Please open a case for further assistance
 
4) Page Object Package (com.abc.projectpage)

        This package is used for modelling of page objects. various page objects are stored as By class objects which will be used by testscripts and page wise reuseable code. Sample code for Google and Yahoo has been done.
       
       [Note] - Inplace of locators being stored as By Class object i have stored them as string in format "LocatorType==Locator". Example "xpath==.//*[@id='gb_70']" or "id==lst-ib" . Here locator type is id and Locator is lst-ib. 
        benefit of this method is that we can store the locator in other places also in same format as string or key-value pair. So to accomodate this change. code just before the findelement method(selenium method which identify the object in the page) has a string split using "==" and pass then pass the locator to it. you can return back to the page object by using BY object method and little modification of findelement method in seleniumrepo package.
        
5) Selenium Repository Package (com.abc.seleniumrepository)
        
        In this package all the permutation and combination of thing that can be done over a webpage has been build as methods so that they can be used by testscript and no need to write the selenium code each and everytime during the scripting. it almost reduce the scripts lines of code to one-fifth or more.
        Example if you want to click any object over the webpage just pass the locator to click method. or if you want to write something to a textbox then pass the locator and the string to enterText method.
        
        Request you to go through the method as it will give you understanding of how things are working
  
6) Utility Package (com.abc.util)
        
        In this package all the external usable jars and related functionality codes are available to be used in various type of scripting. Present package have functionality like CSV file read, Email Report, Image comparision, Property file read, Taking Screenshot and Read write Excel File.
    
7) Web Service Package (com.abc.webservice)
        
       This Package deal with functionality of webservices. This package should include xml Generation, xml read. Json Parse, Json Generation other file read write. Also various types of connection like ftp connection code can be included in this package. I have only included a XML file generation code. The code will generate you a Testng.xml file.

8) TestScript Package(com.abc.testscript)
          
         Understand the code of a sample testscript
   
            Each java file in this package have lot many method and each methods are indivisual testscript. Along with the Testscript we have 2 more methods i.e beforemethod and aftermethod which help us in starting and closing browser for each test. you can distiguish a testscript with these two methods by marking the annotaion @test just above a method.
            Now coming to the testscript. For example we have a script which will open a browser will navigate to a specific url, click on some button and enter some text. So my testscript code will contain 3-4 lines of code only. 1st line will be calling seleniumrepo.GotoURL and pass the url as parameter and As the url is present in the propertyfile so we will read through the property file and pass the one as parameter.Example SeleniumRepo.GoToUrl(PropertyFileRead.FileRead("ProjectData.properties","TS01SiteURLNavigation")); .
            our 2nd step is to click on a button so we will call the click method from seleniumrepo again and pass the locator as parameter. locator can be passed from property file or from the pageboject pages. Example SeleniumRepo.click(PropertyFileRead.FileRead("ProjectData.properties","FirstNameErr"));
            Final step will be enter something on the textbox so we will call entertext method from the seleniumrepo and pass the locator and the text to be entered as parameter.
            various kind of validation/assertion can be done by looking into the return type of these seleniumrepo methods. Please go through the sample testscript to understand further.
  
9) Data Provider Package (com.abc.dataprovider)
       
        DataProvider using an Excel feature has been added recently. Here we are using a file data.xls(Path of the Excel is hardcoded in file ExcelDataProvider.java). Dynamically this excel is read and no of colums are data for each script run. Each rows in the excel is one set of data for a indivisual run. Please open the data.xls. You can notice that 1st row is the heading and row number 2 onwards are indivisual data set for each script.
        Inorder to access the data in the script object of the class ExcelDataProviderObject is declared and ExcelDataProviderObject.DataArray gives you a array list which contains all the column data of a particular row in a serial manner. Example if the excel have 3 rows and 5 column then the script will run 3 times as it has 3 rows and on each run ExcelDataProviderObject.DataArray will be a arraylist which contains all the 5 column data in serial manner. Implementaion example is available in TC002MapSearchPage.java's SearchPageTest method.
  
10) propertyfile

        Here we keep all our property files and other excel files for read. Property file are maintained in a key-value pair. We have data like db detail, browsertype and other that are to be used by the scripts.

#  What happens when a build is triggered

        Step 1.
        Build is triggered through Maven by using the command- clean install exec:java
        
        Step 2.
        It triggers the testNG.xml. testNG.xml file have 2 script mapped
            i)  Classname: com.abc.testscript.TC001ValidateFormTestCase 
        Methodname (This is the script and this code will execute): FormValidationTest
            ii) Classname: com.abc.testscript.TC002MapSearchPage
        Methodname (This is the script and this code will execute): SearchPageTest
        Both the script will execute one after another. 
        It’s advisable to dynamically generate this file in your project so that you can have control over the testing suite that you want to run.
        For me I have implemented it using a database with table which contains all my scripts id. It also have a column with name as run with values Y/N. Every time during the start I pick all the script id’s with Y flag and generate the testing xml dynamically. You can also find sample testing.xml file generator in com.abc.webService. XMLFileGeneration.java .
       
        Step 3.
        Prior to script start below methods runs
            i)  Listener onStart method – You can configure your one time database connections.
            ii) TestNG BeforeTest (This method will run before every script. In our case 2 times it will run once before script1 and again before script2) – It starts a browser. Before browser start if any proxy is configured then it is set and all the temporary files in the system is cleaned. So that browser can have a clean and fresh session.

        Step 4.
        Then the 1st script is executed. In order to execute the script, you require data to the script. So, data provider has been configured. It has been configured using an excel sheet. Each row in the excel sheet is a set of data and each column are individual data for a specific row.
        After Execution of the script below methods executes
        i)  TestNG AfterTest Method- It closes the browser instance 
        ii) Listner onFinish Method: It can be used to destroy any connection object
 
 # Note: 
 Before triggering the Build do validate the POM.xml placed in root of the folder. Because the Maven and other dependency version may be old or a mismatch. Also take a recent copy of IEDriverServer.exe, chromedriver.exe and geckodriver.exe

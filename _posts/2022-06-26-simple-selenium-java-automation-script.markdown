---
layout: "post"
title: "[Selenium] Simple Java Automation Script"
description: Learn about Agile Software Development
date: "2022-06-26 16:24"
author: Kautsar Virzawan
categories: [Front End Testing, Selenium]
tags: [Learning]
---
For learning purpose!!  
This article will show an example about how to create simple automation script using Selenium with Java language.

## Prerequisites
1. Install [**Java JDK**](https://www.oracle.com/java/technologies/downloads/)  
2. Install IDE, usually i'm using [**Intellij IDE**](https://www.jetbrains.com/idea/download/)
3. Download [**Selenium Java Clients Driver**](https://www.selenium.dev/downloads/)
4. Download Webdriver depends in which browser we want to test, the most famous one is [**ChromeDriver**](https://chromedriver.chromium.org/downloads) (Note: ChromeDriver version should be same as the currently used Chrome version)

## Installation
**Step 1** : Create new Java project in Intellij  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-26_at_21.02.39_1KA-ygmS1.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656252461225"/>{: width="80%"}  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-26_at_21.02.48_7VgeO2EJ2.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656252460851"/>{: width="80%"}  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-26_at_21.03.03_kdlKvhfd0.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656252460605"/>{: width="80%"}  

**Step 2** : Add the downloaded selenium JAR into Intellij as external libraries  

    <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-26_at_21.10.40_RWMIt2rCh.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656252870421"/>{: width="30%"}  

    <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-26_at_21.11.24_5Y2adeUcE.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656252868942"/>{: width="70%"}  

    <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-26_at_21.12.28_ZEg-ZeFuH.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656252870957"/>{: width="60%"}
    _Select all JAR files and libs folder_  

**Step 3** : Create webdriver directory inside project and put the downloaded Chromedriver into the folder  

    <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-26_at_21.36.11_OPg1fCm91.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656254270722"/>{: width="60%"}  

## Implementation
Now we will create some simple automation script using dummy website that i recommend for learning create automation script [**katalon-demo-cura.herokuapp.com**](katalon-demo-cura.herokuapp.com). First, we need to create new Java class inside src directory.  

    <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-26_at_21.53.01_2LZgzBtFh.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656255193173"/>{: width="60%"}  

The scenario is to verify user successfully make an appointment, here is the complete source code  

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;

import java.util.List;
import java.util.concurrent.ThreadLocalRandom;

public class simpleSeleniumTest {
    public static void main(String[] args){

        //Create Chromedriver Object
        System.setProperty("webdriver.chrome.driver","./webdriver/chromedriver");   //Set path to Chromedriver manually
        ChromeDriver driver = new ChromeDriver();                                   //instantiate Chromedriver

        //Open Browser and enter the URL
        driver.get("https://katalon-demo-cura.herokuapp.com/");

        //Assert website title header with expected title
        String title = driver.getTitle();                   //Get website title
        String expectedtitle = "CURA Healthcare Service";   //Expected title
        if (title.contentEquals(expectedtitle)) {           //Create condition for checking whether title already correct or not
            System.out.println("Title Match!");
        }
        else {
            System.out.println("Title Doesn't Match");
        }

        //User click the Appointment button
        WebElement buttonAppointment = driver.findElement(By.id("btn-make-appointment"));   //Create Appointment button object with ID
        buttonAppointment.click();                                                          //Click Appointment button

        //Verify login page is displayed
        String loginURL = driver.getCurrentUrl();                                               //Get the current URL
        if (loginURL.equals("https://katalon-demo-cura.herokuapp.com/profile.php#login")) {     //Create condition for checking whether Login URL already correct or not
            System.out.println("Login URL correct!");
        }
        else {
            System.out.println("Incorrect Login URL!");
        }
        WebElement labelLogin = driver.findElement(By.xpath("//*[@id='login']/div/div/div[1]/h2"));    //Create Login label object with XPATH
        String loginText = labelLogin.getText();                                                       //Get login label text
        if (loginText.equals("Login")) {                                                               //Create condition for checking whether Login text already correct or not
            System.out.println("Login Page Opened!");
        }
        else {
            System.out.println("Login Page Not Found!");
        }

        //User login with username and password
        WebElement inputUsername = driver.findElement(By.id("txt-username"));    //Create Username input field object by ID
        inputUsername.sendKeys("John Doe");                                      //Input text into Username field
        WebElement inputPassword = driver.findElement(By.id("txt-password"));    //Create Password input field object by ID
        inputPassword.sendKeys("ThisIsNotAPassword");                            //Input text into Password field
        WebElement buttonLogin = driver.findElement(By.id("btn-login"));         //Create Login button object by ID
        buttonLogin.click();                                                     //Click Login button

        //Verify appointment page is displayed
        String appointmentURL = driver.getCurrentUrl();                                               //Get the current URL
        if (appointmentURL.equals("https://katalon-demo-cura.herokuapp.com/#appointment")) {          //Create condition for checking whether appointment URL already correct or not
            System.out.println("Appointment URL correct!");
        }
        else {
            System.out.println("Incorrect Appointment URL!");
        }
        WebElement labelAppointment = driver.findElement(By.xpath("//*[@id='appointment']/div/div/div/h2"));    //Create Appointment label object with XPATH
        String appointmentText = labelAppointment.getText();                                                    //Get Appointment label text
        if (appointmentText.equals("Make Appointment")) {                                                       //Create condition for checking whether Appointment text already correct or not
            System.out.println("Appointment Page Opened!");
        }
        else {
            System.out.println("Appointment Page Not Found!");
        }

        //User select facility droplist
        Select drpFacility = new Select(driver.findElement(By.id("combo_facility")));       //Create Facility droplist object by ID
        drpFacility.selectByValue("Hongkong CURA Healthcare Center");                       //Select Facility droplist by value
        String selectedValue = drpFacility.getWrappedElement().getDomProperty("value");     //Get the selected droplist value based on DOM property

        //User checklist hospital readmission checkbox
        WebElement chkAdmission = driver.findElement(By.id("chk_hospotal_readmission"));    //Create Readmission checkbox object by ID
        chkAdmission.click();                                                               //Click Readmission checkbox
        String chkAdmissionFlag;                                                            //Create Admission flag variable
        if(chkAdmission.isSelected()){                                                      //Get the checkbox checked state based on DOM property
            chkAdmissionFlag = "Yes";
        }
        else{
            chkAdmissionFlag = "No";
        }

        //User select healthcare program radiobutton
        WebElement radioMedicaid = driver.findElement(By.id("radio_program_medicaid"));     //Create Healthcare Program radiobutton object by ID
        radioMedicaid.click();                                                              //Click Healthcare Program radiobutton
        String radioMedicaidText = radioMedicaid.getDomProperty("value");                   //Get the radiobutton value based on DOM property

        //User select visit date
        WebElement buttonCalendar = driver.findElement(By.id("txt_visit_date"));                                                    //Create Visit Calendar button object by ID
        buttonCalendar.click();                                                                                                     //Click Visit Calendar
        List<WebElement> date = driver.findElements(By.xpath("//td[@class='day']"));                                                //Create element lists of date object to get the maximum date on a month
        int randomDate = ThreadLocalRandom.current().nextInt(1, date.size() + 1);                                                   //Create variable for input random date between 1-maximum date in a month
        WebElement selectDate = driver.findElement(By.xpath("//td[@class='day' and normalize-space(text())='"+randomDate+"']"));    //Create date object based on inputted number in variable randomDate
        selectDate.click();                                                                                                         //Click date
        String selectedDate = buttonCalendar.getDomProperty("value");                                                               //Get the date value based on DOM property

        //User input comment
        WebElement inputComment = driver.findElement(By.id("txt_comment"));     //Create Comment input object by ID
        inputComment.sendKeys("Test Selenium");                                 //Input text into Comment field
        String inputtedComment = inputComment.getDomProperty("value");          //Get the inputted Comment value based on DOM property

        //User submit appointment
        WebElement buttonBook = driver.findElement(By.id("btn-book-appointment"));     //Create Appointment button object by ID
        buttonBook.click();                                                            //Click Appointment button

        //Verify appointment confirmation page displayed
        String appointmentConfirmationURL = driver.getCurrentUrl();                                                     //Get the current URL
        if (appointmentConfirmationURL.equals("https://katalon-demo-cura.herokuapp.com/appointment.php#summary")) {     //Create condition for checking whether appointment confirmation URL already correct or not
            System.out.println("Appointment Confirmation URL correct!");
        }
        else {
            System.out.println("Incorrect Appointment Confirmation URL!");
        }
        WebElement labelConfirmation = driver.findElement(By.xpath("//*[@id='summary']/div/div/div[1]/h2"));  //Create Appointment Confirmation label object with XPATH
        String confirmationText = labelConfirmation.getText();                                                //Get Appointment Confirmation label text
        if (confirmationText.equals("Appointment Confirmation")) {                                            //Create condition for checking whether Appointment Confirmation text already correct or not
            System.out.println("Appointment Confirmation Opened!");
        }
        else {
            System.out.println("Appointment Confirmation Not Found!");
        }

        //Assert appointment confirmation data with expected result based on inputted data on previous page
        WebElement labelFacility = driver.findElement(By.id("facility"));                     //Create Facility text object with ID
        WebElement labelReadmission = driver.findElement(By.id("hospital_readmission"));      //Create Readmission text object with ID
        WebElement labelProgram = driver.findElement(By.id("program"));                       //Create Healthcare Program text object with ID
        WebElement labelVisitDate = driver.findElement(By.id("visit_date"));                  //Create Visit Date text object with ID
        WebElement labelComment = driver.findElement(By.id("comment"));                       //Create Comment text object with ID
        System.out.println("Facility : "+selectedValue);
        System.out.println("Hospital Readmission : "+chkAdmissionFlag);
        System.out.println("Healthcare Program : "+radioMedicaidText);
        System.out.println("Visit Date : "+selectedDate);
        System.out.println("Comment : "+inputtedComment);
        if (labelFacility.getText().equals(selectedValue)                                     //Create condition for checking whether all displayed fields are identics with the inputted data
            && labelReadmission.getText().equals(chkAdmissionFlag)
            && labelProgram.getText().equals(radioMedicaidText)
            && labelVisitDate.getText().equals(selectedDate)
            && labelComment.getText().equals(inputtedComment)) {
            System.out.println("Test Passed!");
        }
        else {
            System.out.println("Test Failed!");
        }

        //Close browser
        driver.close();
    }
}
```  

## Code Explanation
### Step 1 : Setting up the ChromeDriver and instantiate the ChromeDriver object
We need to specify our ChromeDriver path by using `System.setProperty("webdriver.chrome.driver","PATH_TO_CHROMEDRIVER");` and also instantiate the ChromeDriver object  

```java
//Create Chromedriver Object
System.setProperty("webdriver.chrome.driver","./webdriver/chromedriver");   //Set path to Chromedriver manually
ChromeDriver driver = new ChromeDriver();                                   //instantiate Chromedriver
```  

### Step 2 : Open the browser and check the browser Title
In this step we want to open the browser and navigate into the website url by using `driver.get("WEBSITE_URL");` after the web opened, we want to get the website title and store it into String variable by using  `String title = driver.getTitle();`  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-26_at_22.14.32_oW6kzjYJe.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656256486966"/>{: width="50%"}
   _Website Title_  

Then we will create condition to check whether title already same as the expected title or not  

```java
//Open Browser and enter the URL
driver.get("https://katalon-demo-cura.herokuapp.com/");

//Assert website title header with expected title
String title = driver.getTitle();                   //Get website title
String expectedtitle = "CURA Healthcare Service";   //Expected title
if (title.contentEquals(expectedtitle)) {           //Create condition for checking whether title already correct or not
    System.out.println("Title Match!");
}
else {
    System.out.println("Title Doesn't Match");
}
```

### Step 3 : User open the login page
User need to click the Appointment button in the screen to make appointment  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-26_at_22.22.00_haZD1yzAV.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656257132268"/>{: width="80%"}  

We need to create the Appointment button object so the driver able to click the button, for creating the object we can use this code depends on the suitable locator type  
`WebElement objectName = driver.findElement(By.id("ELEMENT_ID"));`  
`WebElement objectName = driver.findElement(By.xpath("ELEMENT_XPATH"));`  
`WebElement objectName = driver.findElement(By.cssSelector("ELEMENT_CSS"));`  
`WebElement objectName = driver.findElement(By.linkText("ELEMENT_LINKTEXT"));`  
`WebElement objectName = driver.findElement(By.className("ELEMENT_CLASSNAME"));`  
`WebElement objectName = driver.findElement(By.name("ELEMENT_NAME"));`  

We can find the object locator by using chrome inspect element (right click on the object and select inspect). Button Appointment has id `btn-make-appointment` so we can use `WebElement buttonAppointment = driver.findElement(By.id("btn-make-appointment"));` and to click the button `buttonAppointment.click();`  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-26_at_22.31.44_JJepdcl9L.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656257661763"/>{: width="80%"}  

```java
//User click the Appointment button
WebElement buttonAppointment = driver.findElement(By.id("btn-make-appointment"));   //Create Appointment button object with ID
buttonAppointment.click();                                                          //Click Appointment button
```  

After user click the Appointment button, then login page displayed, we need to verify it. We can store the current opened URL into String variable by using `String loginurl = driver.getCurrentUrl();` and then create a condition to check whether the opened URL already same as the expected URL or not. Also we want to verify some object inside the Login page to make sure the page is opened, we can create the Login title header object by using xpath locator `WebElement labelLogin = driver.findElement(By.xpath("//*[@id='login']/div/div/div[1]/h2"));`  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-27_at_07.25.28_g2AVpPQVu.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656289823161"/>{: width="80%"}
   _Getting XPATH on the object_  

Then we need to get the text from the object that we already created and store it into a variable, we can use `String loginText = labelLogin.getText();` Now we able to create condition to check whether the Login header object text already same as the expected text or not  

```java
//Verify login page is displayed
String loginURL = driver.getCurrentUrl();                                               //Get the current URL
if (loginURL.equals("https://katalon-demo-cura.herokuapp.com/profile.php#login")) {     //Create condition for checking whether Login URL already correct or not
    System.out.println("Login URL correct!");
}
else {
    System.out.println("Incorrect Login URL!");
}
WebElement labelLogin = driver.findElement(By.xpath("//*[@id='login']/div/div/div[1]/h2"));    //Create Login label object with XPATH
String loginText = labelLogin.getText();                                                       //Get login label text
if (loginText.equals("Login")) {                                                               //Create condition for checking whether Login text already correct or not
    System.out.println("Login Page Opened!");
}
else {
    System.out.println("Login Page Not Found!");
}
```  

### Step 4 : User successfully login
In order to login, we need to input Username, Password and click the Login button.  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-27_at_07.55.27_C2PtGtQBb.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656291361976"/>{: width="80%"}  

First, we need to create the object for Username input field by using `WebElement inputUsername = driver.findElement(By.id("txt-username"));` and input the username text into the object by using `inputUsername.sendKeys("John Doe");`  

Next, we create the object for Password input field by using `WebElement inputPassword = driver.findElement(By.id("txt-password")); ` and input the password text into the object by using `inputPassword.sendKeys("ThisIsNotAPassword");");`  

Now we need to click the Login button, as usual we create the Login button object with `WebElement buttonLogin = driver.findElement(By.id("btn-login"));` and click the button with `buttonLogin.click();`  

```java
//User login with username and password
WebElement inputUsername = driver.findElement(By.id("txt-username"));    //Create Username input field object by ID
inputUsername.sendKeys("John Doe");                                      //Input text into Username field
WebElement inputPassword = driver.findElement(By.id("txt-password"));    //Create Password input field object by ID
inputPassword.sendKeys("ThisIsNotAPassword");                            //Input text into Password field
WebElement buttonLogin = driver.findElement(By.id("btn-login"));         //Create Login button object by ID
buttonLogin.click();                                                     //Click Login button
```  

We need to make sure the user is successfully logged in, to verify it, we can get the currently opened page URL with `String appointmenturl = driver.getCurrentUrl();` and then create a condition to check whether the opened URL already correct as expected or not.  

Also we can verify it by using an object inside the page, we will create an object that contains Make Appointment title label by using `WebElement labelAppointment = driver.findElement(By.xpath("//*[@id='appointment']/div/div/div/h2"));` and then create a condition to check whether the object text already correct as expected or not.  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-27_at_18.55.37_34XPP-DRe.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656330955809"/>{: width="100%"}  

```java
//Verify appointment page is displayed
String appointmentURL = driver.getCurrentUrl();                                               //Get the current URL
if (appointmentURL.equals("https://katalon-demo-cura.herokuapp.com/#appointment")) {          //Create condition for checking whether appointment URL already correct or not
    System.out.println("Appointment URL correct!");
}
else {
    System.out.println("Incorrect Appointment URL!");
}
WebElement labelAppointment = driver.findElement(By.xpath("//*[@id='appointment']/div/div/div/h2"));    //Create Appointment label object with XPATH
String appointmentText = labelAppointment.getText();                                                    //Get Appointment label text
if (appointmentText.equals("Make Appointment")) {                                                       //Create condition for checking whether Appointment text already correct or not
    System.out.println("Appointment Page Opened!");
}
else {
    System.out.println("Appointment Page Not Found!");
}
```

### Step 5 : User submit an appointment
In the Make Appointment page, there are several types of fields, Facility is a droplist, Hospital Readmission is a checkbox, Healthcare Program is a radio button, Visit Date is a calendar, Comment is an input textfield. Each type of fields have different treatment.  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-27_at_18.55.37_34XPP-DRe.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656330955809"/>{: width="100%"}  

Let's start from Facility, Because Facility is a droplist, to create the object we need to use `Select` instead of `WebElement`. This is the example `Select drpFacility = new Select(driver.findElement(By.id("combo_facility")));` and to select the droplist we can use several options
1. By Value (Value can be found inside the HTML attribute) `drpFacility.selectByValue("Hongkong CURA Healthcare Center");`  
2. By Droplist Index (Index start from 0) `drpFacility.selectByIndex(1);`  
3. By Visible Text `drpFacility.selectByVisibleText("Hongkong CURA Healthcare Center");`  

After droplist is selected, we want to save the selected value and store it into a variable that we will use later in the last step, we will get the DOM property named value by using `String selectedValue = drpFacility.getWrappedElement().getDomProperty("value");` we can check the property in browser inspect element and then open Properties tab  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-27_at_19.29.48_30k4NCFJI.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656333109299"/>{: width="80%"}  

```java
//User select facility droplist
Select drpFacility = new Select(driver.findElement(By.id("combo_facility")));       //Create Facility droplist object by ID
drpFacility.selectByValue("Hongkong CURA Healthcare Center");                       //Select Facility droplist by value
String selectedValue = drpFacility.getWrappedElement().getDomProperty("value");     //Get the selected droplist value based on DOM property
```  

Next we create checkbox object with `WebElement chkAdmission = driver.findElement(By.id("chk_hospotal_readmission"));` and click it with `chkAdmission.click();` then we can create a condition to check whether the user click the checkbox or not with `chkAdmission.isSelected()` and we can store the flag into `chkAdmissionFlag` variable  

```java
//User checklist hospital readmission checkbox
WebElement chkAdmission = driver.findElement(By.id("chk_hospotal_readmission"));    //Create Readmission checkbox object by ID
chkAdmission.click();                                                               //Click Readmission checkbox
String chkAdmissionFlag;                                                            //Create Admission flag variable
if(chkAdmission.isSelected()){                                                      //Get the checkbox checked state based on DOM property
    chkAdmissionFlag = "Yes";
}
else{
    chkAdmissionFlag = "No";
}
```  

For radiobutton is same like usual, we can use `WebElement` like this `WebElement radioMedicaid = driver.findElement(By.id("radio_program_medicaid"));` and then to click the radiobutton we use `radioMedicaid.click();` also we want to save the selected radiobutton value and store it into a variable that we will use later in the last step with `String radioMedicaidText = radioMedicaid.getDomProperty("value");`  

```java
//User select healthcare program radiobutton
WebElement radioMedicaid = driver.findElement(By.id("radio_program_medicaid"));     //Create Healthcare Program radiobutton object by ID
radioMedicaid.click();                                                              //Click Healthcare Program radiobutton
String radioMedicaidText = radioMedicaid.getDomProperty("value");                   //Get the radiobutton value based on DOM property
```  

For Calendar is also same, to create the object we use `WebElement` like this `WebElement buttonCalendar = driver.findElement(By.id("txt_visit_date"));` then user need to click the object to open the Calendar pop up `buttonCalendar.click();` after the pop up displayed, we want to get all of the displayed date elements and put it into list by using `List<WebElement> date = driver.findElements(By.xpath("//td[@class='day']"));`  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-27_at_20.10.22_oFn_lEiX_.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656335451627"/>{: width="50%"}  

Now we can use the created list for determining the maximum date in the current month, we are doing this because each month have different total days between 28-31 days. Then we can create a random number generator that generate number between 1-`date.size()` this function used to determine total days in selected month, the code looks like this `int randomDate = ThreadLocalRandom.current().nextInt(1, date.size() + 1);` next we create an object that able to find the date based on previously generated random number by using `WebElement selectDate = driver.findElement(By.xpath("//td[@class='day' and normalize-space(text())='"+randomDate+"']"));` then click the date with `selectDate.click();` now we save the selected date value and store it into a variable that we will use later in the last step with `String selectedDate = buttonCalendar.getDomProperty("value");`  

```java
//User select visit date
WebElement buttonCalendar = driver.findElement(By.id("txt_visit_date"));                                                    //Create Visit Calendar button object by ID
buttonCalendar.click();                                                                                                     //Click Visit Calendar
List<WebElement> date = driver.findElements(By.xpath("//td[@class='day']"));                                                //Create element lists of date object to get the maximum date on a month
int randomDate = ThreadLocalRandom.current().nextInt(1, date.size() + 1);                                                   //Create variable for input random date between 1-maximum date in a month
WebElement selectDate = driver.findElement(By.xpath("//td[@class='day' and normalize-space(text())='"+randomDate+"']"));    //Create date object based on inputted number in variable randomDate
selectDate.click();                                                                                                         //Click date
String selectedDate = buttonCalendar.getDomProperty("value");                                                               //Get the date value based on DOM property
```  

For the Comment field is same like username input field that we already created before, we create the object with `WebElement inputComment = driver.findElement(By.id("txt_comment"));` and input the text into it `inputComment.sendKeys("Test Selenium");` also save the inputted value into a variable `String inputtedComment = inputComment.getDomProperty("value");`  

```java
//User input comment
WebElement inputComment = driver.findElement(By.id("txt_comment"));     //Create Comment input object by ID
inputComment.sendKeys("Test Selenium");                                 //Input text into Comment field
String inputtedComment = inputComment.getDomProperty("value");          //Get the inputted Comment value based on DOM property
```

Finally we can click the booking button, as always we need to create the object first `WebElement buttonBook = driver.findElement(By.id("btn-book-appointment"));` then we can interact to click the button with `buttonBook.click();`  

```java
//User submit appointment
WebElement buttonBook = driver.findElement(By.id("btn-book-appointment"));     //Create Appointment button object by ID
buttonBook.click();  
```  

### Step 6 : User successfully making an appointment

This will be our last step, after submit an appointment, user will be directed to confirmation page, we need to verify whether confirmation page is displayed correctly or not.  

   <img src="https://ik.imagekit.io/13kivbmzawg7/2022-06-26-simple-selenium-java-automation-script/Screenshot_2022-06-27_at_20.34.25_EwMzRE2J4.png?ik-sdk-version=javascript-1.4.3&updatedAt=1656336892476"/>{: width="80%"}  

We want to verify whether the opened URL already correct or not, we need to get the current URL and store it into a variable with `String appointmentConfirmationURL = driver.getCurrentUrl();` then create a condition to check whether the URL already as expected or not. After that we want to verify the Appointment Confirmation title label, so we create an object for the label with `WebElement labelConfirmation = driver.findElement(By.xpath("//*[@id='summary']/div/div/div[1]/h2"));` and store the label text into a variable with `String confirmationText = labelConfirmation.getText();` now we can create a condition to check whether the Appointment Confirmation title text already as expected or not.  

```java
//Verify appointment confirmation page displayed
String appointmentConfirmationURL = driver.getCurrentUrl();                                                     //Get the current URL
if (appointmentConfirmationURL.equals("https://katalon-demo-cura.herokuapp.com/appointment.php#summary")) {     //Create condition for checking whether appointment confirmation URL already correct or not
    System.out.println("Appointment Confirmation URL correct!");
}
else {
    System.out.println("Incorrect Appointment Confirmation URL!");
}
WebElement labelConfirmation = driver.findElement(By.xpath("//*[@id='summary']/div/div/div[1]/h2"));  //Create Appointment Confirmation label object with XPATH
String confirmationText = labelConfirmation.getText();                                                //Get Appointment Confirmation label text
if (confirmationText.equals("Appointment Confirmation")) {                                            //Create condition for checking whether Appointment Confirmation text already correct or not
    System.out.println("Appointment Confirmation Opened!");
}
else {
    System.out.println("Appointment Confirmation Not Found!");
}
```  

Now we want to assert all of the inputted data on the previous page with the displayed data in the Confirmation Page, first we need to create objects to get the value label on each fields, then we create a condition to compare the text for each fields on the Confirmation page with the variables that we already created on the previous page, if all of the text equals, then we will show `Test Passed!` in the console, otherwise `Test Failed!` will displayed.

```java
//Assert appointment confirmation data with expected result based on inputted data on previous page
WebElement labelFacility = driver.findElement(By.id("facility"));                     //Create Facility text object with ID
WebElement labelReadmission = driver.findElement(By.id("hospital_readmission"));      //Create Readmission text object with ID
WebElement labelProgram = driver.findElement(By.id("program"));                       //Create Healthcare Program text object with ID
WebElement labelVisitDate = driver.findElement(By.id("visit_date"));                  //Create Visit Date text object with ID
WebElement labelComment = driver.findElement(By.id("comment"));                       //Create Comment text object with ID
System.out.println("Facility : "+selectedValue);
System.out.println("Hospital Readmission : "+chkAdmissionFlag);
System.out.println("Healthcare Program : "+radioMedicaidText);
System.out.println("Visit Date : "+selectedDate);
System.out.println("Comment : "+inputtedComment);
if (labelFacility.getText().equals(selectedValue)                                     //Create condition for checking whether all displayed fields are identics with the inputted data
    && labelReadmission.getText().equals(chkAdmissionFlag)
    && labelProgram.getText().equals(radioMedicaidText)
    && labelVisitDate.getText().equals(selectedDate)
    && labelComment.getText().equals(inputtedComment)) {
    System.out.println("Test Passed!");
}
else {
    System.out.println("Test Failed!");
}
```  

After the test finished, we close the browser.  

```java
//Close browser
driver.close();
```

Source code repository : [**Github**](https://github.com/Kautsarv/simple-selenium.git)

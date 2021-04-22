# AjitRaskarTechChallenge

Author:Ajit Raskar

# Summary: 
This project has built a client which communicates with open weather map API called One call API. Main task of this client is to predict weather and temperature of Sydney for upcoming 7 days from the current date.
This project also has one TestNG class which tests this client.

# Table of Contents
* Tools and Technology used
* Problem statement
* Instructions to execute the code
* Test cases executed
* Test case result artifacts
* Project structure
* Sample output
* Understanding the output
* To be noted

# Tools and Technology used:
* Java 8
* Rest assured library (3.0.6)
* TestNG (6.14.3),
* Maven (3.8.1)
* Log4j API(1.2.17)
* API used: One call API  https://openweathermap.org/api/one-call-api

# Problem statement:
Find the number of days in Sydney where the temperature is predicated to be above 20 degrees (at the time of calling the API) in the next 7 days (from the current days date), or whichever period the free subscription will allow.
Also find how many days it is predicted to be sunny in the same time period.

# Instructions to execute the code
* Clone the repository https://github.com/aaraskar/AjitRaskarTechChallenge.git
* Navigate to root directory and fire the command mvn clean install
* Or the other way is once you have the code mentioned in above git repository in your editor then right click the testng.xml and select Run As TestNG Suite

Note:testng.xml is present at the root directory level. This is a main configuration file in TestNG

# Test cases executed:
* validateResponseCodeTest : This verifies the status code of API execution.
* validateLatitudeLongitudeTest: This verifies values of latitude and longitude from API response.
* validateTimezoneTest :  This verifies the value of timezone from API response.
* validateWeatherDetailsTest: This test focusses on parsing the response of API execution and prints the result for the requirement mentioned in ‘Problem statement’ section.

# Test case result artifacts:
After executing the code, refer below files for more information.
* <<Root Dir>>/Result.log : This contains the detailed report for the requirement mentioned in ‘Problem statement’ section
* <<Root Dir>>/target/request.log: Contains logs related to request
* <<Root Dir>>/target/response.log: Contains logs related to response
* <<Root Dir>>/test-output/index.html : Contains results of all the test cases

# Project structure:
* <<Root Dir>>\src\main\java\com\qa\base\TestBase.java : This is a super class of all classes and it loads the configuration file(config.properties)
* <<Root Dir>>\src\main\java\com\qa\utils\Utility.java : This contains various utility methods for parsing the response and printing the result.
* <<Root Dir>>\src\main\java\com\qa\WeatherClient\WeatherAPIClient.java  This is a weather api client code.
* <<Root Dir>>src\test\java\com\qa\test\WeatherAPITest.java : This is a testNG class which tests the weather api client.
* <<Root Dir>>\src\main\resources\config.properties: This is a property file containing various parameters for request.
* <<Root Dir>>\src\main\resources\log4j.properties : This is a configuration file for logging mechanism.
* <<Root Dir>>\testng.xml : This is a testNG configuration file.
* <<Root Dir>>\pom.xml : This file contains all the maven dependencies.



# Sample output
Below is the sample output which shows the number of days in Sydney where the temperature is predicated to be above 20 degrees in next 7 days from the current date and find how days it is predicted to be sunny in the same time period.
Note here current date at the time of writing this readme was 23-04-2021. 
Sydney is specified using its latitude and longitude values in the request.
Output:
* Printing below details for Sydney
* Day and Predicted Temperature of all upcoming 7 days in Sydney where current date is :23-04-2021
   * Day :24-04-2021(1619226000), Temperature : 18.24 degrees
   * Day :25-04-2021(1619312400), Temperature : 17.8 degrees
   * Day :26-04-2021(1619398800), Temperature : 17.38 degrees
   * Day :27-04-2021(1619485200), Temperature : 17.98 degrees
   * Day :28-04-2021(1619571600), Temperature : 18.83 degrees
   * Day :29-04-2021(1619658000), Temperature : 18.95 degrees
   * Day :30-04-2021(1619744400), Temperature : 19.44 degrees

#########################################################################


* Above data confirms that there is no single day in Sydney in next 7 days where temperature is predicated to be above 20 degrees


#########################################################################

* Day and Predicted Weather of all upcoming 7 days in Sydney where current date is :23-04-2021
  * Day :24-04-2021(1619226000), Weather : Clouds
  * Day :25-04-2021(1619312400), Weather : Clouds
  * Day :26-04-2021(1619398800), Weather : Rain
  * Day :27-04-2021(1619485200), Weather : Rain
  * Day :28-04-2021(1619571600), Weather : Rain
  * Day :29-04-2021(1619658000), Weather : Rain
  * Day :30-04-2021(1619744400), Weather : Rain


#########################################################################
* Above data confirms that there is no single sunny day in Sydney in next 7 days


# Understanding the output
* There are 4 sections of the output
  * Section 1: It contains Day and Predicted Temperature in Sydney for all upcoming 7 days from the current date.
  * Section 2: Prints numbers of days where temperature is predicted to be above 20 degrees.
  * Section 3: Prints Day and Predicted weather in Sydney for all upcoming 7 days from the current date.
  * Section 4: Prints number of predicted sunny days in Sydney

# To be noted
* A day which has weather predicted as Clear is treated as a sunny day.
From the response there is a parameter called **daily.weather.main** which treats a day either sunny/rainy/cloudy etc . 
For various weather parameters refer https://openweathermap.org/api/one-call-api
For more information on various weather conditions, refer https://openweathermap.org/weather-conditions#Weather-Condition-Codes-2 

* Different combinations of city, predicted temperature and predicted weather type can be passed in config.properties 
Pass correct latitude and longitude in config.properties to represent city.  
timeZone variable has the format <<CountryName/CityName>>
For e.g Australia/Sydney



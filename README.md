# REST-API-CLIENT

*COMPANY*: CODTECH IT SOLUTIONS

*NAME*: RAHUL SANJAY THAKARE

*INTERN ID*:CTIS6516

*DOMAIN*: JAVA PROGRAMMING

*DURATION*: 12 WEEKS

*MENTOR*: NEELA SANTOSH

## Description

The Weather Application is a simple and useful web-based project developed during my internship in Front End Development at CODTECH IT Solutions. The main goal of this project is to provide real-time weather information in a clean, easy-to-use interface so that users can quickly check the weather of any city.

This application is built using basic front-end technologies like HTML, CSS, and JavaScript. It connects to a weather API to fetch live weather data such as temperature, humidity, wind speed, and weather conditions (like sunny, cloudy, or rainy). The user just needs to enter the name of a city, and the application will display the current weather details instantly.

One of the best parts of this application is its simplicity. The user interface is designed in a very user-friendly way so that anyone can use it without confusion. There is a search box where users can type the city name, and with just one click, they can get the weather report. The results are displayed clearly with proper labels and icons to make the information easy to understand.

JavaScript plays an important role in making the application interactive. It is used to fetch data from the API and update the webpage dynamically without refreshing it. This makes the app fast and smooth. Error handling is also included, so if the user enters an incorrect city name, the app shows a proper message instead of crashing.

The design of the Weather Application is responsive, which means it works well on different devices like mobile phones, tablets, and laptops. CSS is used to create a neat layout, attractive colors, and proper spacing so that the app looks modern and professional.

Another important feature of this application is real-time updates. The data shown is not static; it comes directly from the API, ensuring that users always get the latest weather information. This makes the application practical and useful in daily life, especially for planning travel or outdoor activities.

Through this project, I improved my skills in API integration, JavaScript programming, and responsive web design. I also learned how to handle user input and display data in a structured way. This project helped me understand how real-world applications work and how to connect front-end interfaces with external data sources.

In conclusion, the Weather Application is a simple yet powerful project that demonstrates the use of front-end technologies to build a real-time, interactive system. It provides a great user experience while solving a real-life problem. In the future, this project can be enhanced by adding features like weather forecasts for multiple days, location-based weather detection, and more advanced UI designs.



## Code
Class App.java

package codtech.WeatherApp;
public class App 
{
    public static void main( String[] args )
    {
        System.out.println( "Hello World!" );
    }
}

Class WeatherApp.java 

package codtech.WeatherApp;
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.net.HttpURLConnection;
import java.net.URL;

import org.json.JSONObject;

public class WeatherApp {

    public static void main(String[] args) {

        try {
            String city = "Pune";
            String apiKey = "e4a3e92a1baa6ef4946afe09a1fe5761";

            String urlString = "https://api.openweathermap.org/data/2.5/weather?q="
                    + city + "&appid=" + apiKey + "&units=metric";

            URL url = new URL(urlString);
            HttpURLConnection conn = (HttpURLConnection) url.openConnection();
            conn.setRequestMethod("GET");

            BufferedReader reader = new BufferedReader(
                    new InputStreamReader(conn.getInputStream()));

            String inputLine;
            StringBuilder response = new StringBuilder();

            while ((inputLine = reader.readLine()) != null) {
                response.append(inputLine);
            }
            reader.close();

            
            JSONObject jsonObject = new JSONObject(response.toString());

            String cityName = jsonObject.getString("name");
            JSONObject main = jsonObject.getJSONObject("main");
            double temperature = main.getDouble("temp");
            double humidity = main.getDouble("humidity");

            String weatherDescription = jsonObject
                    .getJSONArray("weather")
                    .getJSONObject(0)
                    .getString("description");

            
            System.out.println("===== Weather Report =====");
            System.out.println("City: " + cityName);
            System.out.println("Temperature: " + temperature + " °C");
            System.out.println("Humidity: " + humidity + " %");
            System.out.println("Weather: " + weatherDescription);

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

## OUTPUT


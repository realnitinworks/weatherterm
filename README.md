# WeatherTerm Application

A web scraping application that will scrape weather forecast information from https://weather.com and present it in a terminal.

The options that can be passed to this command line application are:
1. The temperature unit (Celsius or Fahrenheit)
2. The area where you can get the weather forecast
3. Output options where the user of our application can choose between the current forecast, a five-day forecast, a ten-day forecast, and the weekend
4. Ways to complement the output with extra information such as wind and humidity

This application is designed to be extendable, which means that we can create parsers for different websites to get a weather forecast, and these parsers will be available as argument options.

```
# python -m weatherterm -h                 
usage: weatherterm [-h] -p {WeatherComParser} [-u {Celsius,Fahrenheit}] -a
                   AREA_CODE [-v] [-td] [-5d] [-10d] [-w]

Weather info from weather.com on your terminal

optional arguments:
  -h, --help            show this help message and exit
  -u {Celsius,Fahrenheit}, --unit {Celsius,Fahrenheit}
                        Specify the unit that will be used to display the
                        temperatures.
  -v, --version         show program's version number and exit
  -td, --today          Show the weather forecast for the current day.
  -5d, --fivedays       Shows the weather forecast for the next 5 days.
  -10d, --tendays       Shows the weather forecast for the next 10 days.
  -w, --weekend         Shows the weather forecast for the weekend.

required arguments:
  -p {WeatherComParser}, --parser {WeatherComParser}
                        Specify which parser is going to be used to scrape
                        weather information.
  -a AREA_CODE, --areacode AREA_CODE
                        The code area to get the weather broadcast from. It
                        can be obtained from https://weather.com
```


# Running the application

1. Create a virtual environment and install the requirements.

```
# python -m venv .env
# source .env/bin/activate
# pip install -r requirements.txt
```

2. Run the command line utility providing the required arguments: the Parser and the area code.

You can obtain the area code from [here](https://weather.codes/). For instance the area code of Bangalore is INXX0012.

Following are some of the examples
```
# python -m weatherterm -u Celsius -a INXX0012 -p WeatherComParser -td
>> Sun Mar 29
    25.6°
    High 0° / Low 18.3° (Fair)
    Wind: 34% / Humidity: ESE 8 mph 
    
# python -m weatherterm -u Fahrenheit -a INXX0012 -p WeatherComParser -5d
>> Tonight MAR 29
    High 6° / Low 5° (Mostly Clear)
    Wind: SE 8 mph  / Humidity: 58%

>> Mon MAR 30
    High 94° / Low 65° (Mostly Sunny)
    Wind: ESE 12 mph  / Humidity: 37%

>> Tue MAR 31
    High 95° / Low 66° (Sunny)
    Wind: ESE 10 mph  / Humidity: 33%

>> Wed APR 1
    High 95° / Low 67° (Sunny)
    Wind: ESE 10 mph  / Humidity: 33%

>> Thu APR 2
    High 95° / Low 68° (Mostly Sunny)
    Wind: SE 10 mph  / Humidity: 36%

>> Fri APR 3
    High 95° / Low 68° (Mostly Sunny)
    Wind: SE 10 mph  / Humidity: 35%
    
# python -m weatherterm -u Fahrenheit -a INXX0012 -p WeatherComParser -w 
>> Ton ightMAR 29
    High 6° / Low 5° (Mostly Clear)
    Wind: SE 8 mph  / Humidity: 58%



import requests

api_key = "b61c3b46b34f31e03340ce65247dcc68"


user_input = input("Enter city: ")

weather_data = requests.get(
    f"https://api.openweathermap.org/data/2.5/weather?q={user_input}&units=imperial&APPID={api_key}")

if weather_data.json()["cod"] == "404":
    print("no city found")
else:
    weather = weather_data.json()["weather"][0]["main"]
    temp = round(weather_data.json()["main"]["temp"])

    print(f"the weather in {user_input} is: {weather}")
    print(f"The temperature in {user_input} is: {temp}°f")


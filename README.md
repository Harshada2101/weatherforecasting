# weatherforecasting
message through weather detecting and warning notification 
import os 
import sys
import requests 
from datetime import datetime

# Global Parameters 
LANG= 'en'

# Darksky.net API Parameters
DS_API_HOST =
'http://api.darksky.net/forecast'
DS_API_KEY = os.environ.get('DS_API_KEY')
DS_UNITS ='si'

#Google Maps Geocoding API Parameters
GM_ENDPOINT =
'http://maps.google.com/maps/api/geocode/json'
GM_API_KEY = os.environ.get('GM_API_KEY')

def make_get_request(uri:str, payload):
"""
response = requests.get(uri,payload)
if response.status_code !=200;
else:
return response.json()
def get_geo_data(address: str):
    """ Function to get coordinates from Google Maps Geocoding API
    :param address:
    """
    payload ={'address': address,'language': LANG, 'key': GM_API_KEY}
    response = 
    make_get_request(GM_ENDPOINT, payload)
    
        if not response:
           return None
           
           data = response['results'][0]
           formatted_address = 
           data['formatted_address']
           lat = data['geometry'][location]['lat']
           lng = data['geometry'][location]['lng']
              
              return{'lat': lat, 'lng': lng,'formatted_address': formatted_address': formatted_address}
              
              def get_forecast_data(lat: str, lng: str):
              """Function to get Forecast data from Darksky.net API
                    :param lat:
                    :param lng:
                    :return:
                    """
                    uri = DS_API_HOST +'/'+ DS_API_KEY + '/' + str(lat) + ','+ str(lng)
                    payload ={'lang': LANG, 'units':DS_UNITS}
                    response = make_get_request(uri,payload)
                   
                   if not response :
                   return None
                   
                   return response['daily']
                   
                   
                   def print_daily_forecast(geo,forecast):
                   """
                   Function to print daily weather forecast information 
                   :param geo:
                   :param forecast:
                   """
                   print('Getting Forecast for: ' +
                   geo['formatted_address'])
                        print('weekly Summary: ' +
                   forecast['summary'])
                   print()
                   
                   for day in forecast['data']:
                   date = 
                   datetime.fromtimestamp(day['time']:
                   
                   if date.date() ==
                   datetime.now().date():
                               day_name = 'Today'
                            else:
                            day_name = date.strftime("%A")
                            
                        summary = day['summary']
                        temperature-min =
                  str(round(day['temperatureMin'])) + 'degree c'
                            temperature_max =
                  str(round(day['temperatureMax'])) + 'degree c'
                            print(
                                  date.strftime('%d/%m/%y') = ' (' + day_name + '): ' +
                                           summary + ' ' +
                                  temperature_min + ' _ ' + temperature_max)
                                  print()
                            
             def print_header():
             print('---------------------------------------------')
             print('          WEATHER FORECAST  1.0              ')
             print('---------------------------------------------')
             print()
             
             def main():
             """
             Main Function 
             """
             Main Function
             """
             if len(sys.argv) < 2 or DS_API_KEY is
             none:
                  exit('Error: no location or env vars found')
                  geo_data = get_geo_data(sys.argv[1])
                  
                  if not geo_data:
                                  exit('Error: Address not found or invalid response')
                                  forecast_data = get_forecast_data(geo_data['lat'],
                                  geo_data['lng'])
                                  
                                  if not forecast_data:
                                       exit(Error: Forecast not found or invalid response')
                                       
                                       #print Output Forecast information
                                       print_header()
                                       print_daily_forecast(geo_data,forecast_data)
                                       
                                       if ___name___ ==  '___main___':
                                       main()
                                  
                                  
                                  
(
        

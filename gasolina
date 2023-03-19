import http.client
import json
import requests
from bs4 import BeautifulSoup

url = 'https://www.fuelflash.eu/es/autonetoil-palma-españa-carrer-de-son-pendola-1-61933/'

# Realizamos la petición a la URL
response = http.client.HTTPSConnection("api.telegram.org")

# Obtener el precio del gasóleo
soup = BeautifulSoup(requests.get(url).text, 'html.parser')
precio_gasoleo = soup.find('span', {'class': 'preis_part1'}).text.strip()

# Definimos el mensaje a enviar
mensaje = f"El precio del gasóleo es: {precio_gasoleo}"

# Definimos los parámetros para la solicitud HTTP POST
bot_token = "484135027:AAGGd-kcO4PRvQ1Ca5jioMZDDSZvAxdSvl0"
chat_id = "-1001830405274"
headers = {'Content-type': 'application/json'}
data = {
    'text': mensaje,
    'chat_id': chat_id
}

# Codificamos los parámetros a formato JSON
json_data = json.dumps(data)

# Enviamos la solicitud HTTP POST a la API de Telegram para enviar el mensaje
response.request("POST", f"/bot{bot_token}/sendMessage", json_data, headers)

# Obtenemos la respuesta de la API de Telegram
response = response.getresponse()

# Imprimimos la respuesta en la consola
print(response.read().decode())

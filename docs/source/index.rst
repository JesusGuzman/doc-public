API Blokko
===================================

**Blokko Gateway** es una API REST .
A continuacion se describe la forma de integrar/conectarse a Blokko Gateway

Endpoints Disponibles 
=====================

* `POST` /trx
* `POST` /status
  
POST /trx
============

Parametros:
-----------

* ``Merchant_ID``
* ``Terminal_ID``
* ``Amount``
* ``Coin``
* ``Currency``
* ``Exchange_ID``
    * CoinBase: 2
    * CryptoCom: 4
    * Binance: 5
    * IBEX: 6
* ``TX_ID``
* ``Status``
* ``API_KEY``

.. note::
   Para ``API_KEY`` comunicarse con Blokko

Ejemplo con CURL:
----------------- 

.. code-block:: console

    curl --location --request POST 'http://35.192.13.236:5000/trx' \
    --header 'Merchant_ID: 21' \
    --header 'Terminal_ID: 1' \
    --header 'Amount: 1.00' \
    --header 'Coin: USD' \
    --header 'Currency: USD' \
    --header 'Exchange_ID: 6' \
    --header 'TX_ID: 7' \
    --header 'Status: WAITING_CONFIRMATION' \
    --header 'API_KEY: a7dk20aksl3a9sn3asdb3Fas'


Ejemplo con Python:
----------------- 

.. code-block:: console

   import requests

   url = "http://35.192.13.236:5000/trx"

   payload={}
   headers = {
   'Merchant_ID': '21',
   'Terminal_ID': '1',
   'Amount': '1.00',
   'Coin': 'USD',
   'Currency': 'USD',
   'Exchange_ID': '6',
   'TX_ID': '7',
   'Status': 'WAITING_CONFIRMATION',
   'API_KEY': 'a7dk20aksl3a9sn3asdb3Fas'
   }

   response = requests.request("POST", url, headers=headers, data=payload)

   print(response.text)


Response:
---------

.. code-block:: console

    {
    "Amount": "1.00",
    "Currency": "USD",
    "Exchange_ID": "6",
    "Merchant_ID": "21",
    "Status": "WAITING_PAYMENT",
    "TX_ID": "7",
    "Terminal_ID": "1",
    "crypto_amount": "3293",
    "payment_url": "ln9552eph0yq9qyyssqvwsdasd252c9gcvp8n39xp9cs3sgm56eyg4jxeyxajn6eppskelnwsgvy7fq7llmm8jjgcq5tkjny",
    "qr_url": "https://tinyurl.com/532ashcv9"
    }


POST /status
============

Parametros:
-----------

* ``Merchant_ID``
* ``Terminal_ID``
* ``Amount``
* ``Currency``
* ``Exchange_ID``
* ``TX_ID``
* ``Status``
* ``API_KEY``


Ejemplo con CURL:
----------------- 

.. code-block:: console

    curl --location --request POST 'http://35.192.13.236:5000/status' \
    --header 'Merchant_ID: 21' \
    --header 'Terminal_ID: 1' \
    --header 'Amount: 1.00' \
    --header 'Currency: USD' \
    --header 'Exchange_ID: 2' \
    --header 'TX_ID: 7' \
    --header 'Status: WAITING_CONFIRMATION' \
    --header 'API_KEY: a7dk20aksl3a9sn3asdb3Fas'



Ejemplo con Python:
----------------- 

.. code-block:: console

   import requests

   url = "http://35.192.13.236:5000/status"

   payload={}
   headers = {
   'Merchant_ID': '21',
   'Terminal_ID': '1',
   'Amount': '1.00',
   'Currency': 'USD',
   'Exchange_ID': '2',
   'TX_ID': '7',
   'Status': 'WAITING_CONFIRMATION',
   'API_KEY': 'a7dk20aksl3a9sn3asdb3Fas'
   }

   response = requests.request("POST", url, headers=headers, data=payload)

   print(response.text)


Response:
---------

.. code-block:: console
    {
    "Amount": "1.00",
    "Currency": "USD",
    "Exchange_ID": "2",
    "Merchant_ID": "21",
    "Status": "WAITING_CONFIRMATION",
    "TX_ID": "7",
    "Terminal_ID": "1"
    }
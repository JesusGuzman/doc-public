API Blokko
===================================

**Blokko Gateway** es una API REST .
A continuacion se describe la forma de integrar/conectarse a Blokko Gateway

Endpoints Disponibles 
=====================

* `POST` /trx
* `POST` /status
  
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
    "payment_url": "ln9552eph0yq9qyyssqvwavuh8mc9gcvp8n39xp9cs3sgm56eyg4jxeyxajn6eppskelnwsgvy7fq7llmm8jjgcq5tkjny",
    "qr_url": "https://tinyurl.com/532ashcv9"
    }

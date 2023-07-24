Samurai
===================================

**Samurai Strategy** es una estartegia de inversion.
A continuacion se describe la forma de Generar los Pesos para salir en vivo

* Codigo: https://github.com/quant-samurai/samurai_strategy

* Modulos Disponibles:

   * `0-dow_data` Obtiene los Datos OHLC hast el dia del rebalanceo
   * `1-Indicators` Calcula los Indicadores desde el OHLC
   * `2-Kalman` Calcula y filtra las senales de los indicadores
   * `3-mst` Genera arbol con los ETFs del Kalman y se queda con las hojas
   * `4-SortinoRatio` Reduce el numero de ETFs filtrando por el mejor Kalman hasta obtener el numero deseado de ETFS
   * `5-weigths` Calcula los pesos de la lista generada por el Sortino y le asigna pesos
  
* Otros modulos disponibles:
   * `filter_MarketCap` Filtra por Market Cap
   * `filter_alpaca` Filtra los ETFs por los que son fraccionables en ALPACA
   * `dataload_DB` Carga la informacion (OHLC, Indicadores, etc) a la Base de datos
   * `backtest_vectorized_MultiAssets` Genera el bcktest con las senales de alguna estrategia con multiples ETFs
   * `backtest_vectorized_individual` Genera el backtest con las senales de un solo ETF
   * `backtest_tearsheet` Genera el Tearsheet con el valor de la estrategia a lo largo del tiempo
  
0-dow_data
============
Obtiene los Datos OHLC desde una fecha a definir y el dia mas actual para el rebalanceo,
al final almacena estos datos en 

Ejecucion:  python 0-dow_data.py 

Parametros:
-----------

* ``start`` fecha inicial
* ``end`` fecha final 
* ``etfdb_screener.csv`` Archivo con el universo
 
.. note::
   El archivo ``etfdb_screener.csv`` es el universo de los 3000 ETFs



Codigo Principal
----------------- 

.. code-block:: console

   start = '2022-5-1'
   end = '2023-7-12'

   equity_list = pd.read_csv('etfdb_screener.csv').stock.tolist()

   for i in range(0, len(equity_list), 10):
      chunk_list = equity_list[i:i + 10]
      download_data(equity_list=chunk_list, start=start, end=end) 

Salida:
---------
Archivos csv en la ruta por etf:
* ``/samurai_strategy/data/external`` 


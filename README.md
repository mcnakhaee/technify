[![PyPI version](https://badge.fury.io/py/technify.svg)](https://badge.fury.io/py/technify)
## technify
Technical analysis framework using quandl, ta-lib and pandas library.   

_Technify_ provides a simple yet powerful framework to generate common technical analysis signals using [ta-lib](https://github.com/mrjbq7/ta-lib) and pandas visualization to explore trends in stocks data.   
The data can be provided as _ohlcv_ data or directly from [Quandl](https://www.quandl.com/) by means of the built-in integration.

# Features
* Integration with [Quandl](https://www.quandl.com/) data feed and API auth.
* TA-LIB algorithms API
* Pandas visualization

# Documentation
Check the most up-to-date documentation in the [wiki](https://github.com/rubenafo/technify/wiki)

# Examples

The following snippet loads the Bitcoin-USD data from [Quandl](https://www.quandl.com/data/BCHARTS/KRAKENUSD-Bitcoin-Markets-krakenUSD), calculates the Bollinger Bands and EMA(40) and displays the latest 60 data points.

### Loading from Quandl
```python
from technify import Stock
from technify import Overlap as ov

bitusd = Stock.fromQuandl("BCHARTS/KRAKENUSD") \
  .append(ov.bbands, "Close", timeperiod=40, saveas=["bblow", "bbmedium", "bbhigh"]) \
  .append(ov.ema, "Open", timeperiod=40)\
  .show("bblow", "bbmedium", "bbhigh", interval=range(-60))
```

<img src="https://github.com/rubenafo/technify/blob/master/imgs/technify_1.png" width="806">

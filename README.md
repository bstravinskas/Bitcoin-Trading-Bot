# Cryptocurrency-Trading-Bot (IN PROGRESS)
This is a bot that uses the Binance API to retrieve ohlcv data of a given crpyto symbol and executes a basic trading strategy. The data is recieved through the Binance 
websocket for crpyto data. The required packages for this code to work are listed in the requirements.txt file.

#The Strategy
This strategy involves looking at the Relative Strength Index (RSI) that is 14 bars in length. The bar timeframe used in this example uses 1min bars. If the RSI is below 30 this, 
indicates that the crypto is OVERSOLD. If the RSI is above 70, this indicates that the crypto is OVERBOUGHT. If OVERSOLD, the program sends a BUY command to the Binance API,
if OVERBOUGHT, a SELL command is sent the Binance API. The program also checks if the account already has a position open. If a position is ALREADY OPENED, then a BUY 
command will not be executed on an OVERSOLD flag, no matter how many times the crypto is flagged as OVERSOLD, the buy will not execute if there is already a position open. 
Likewise, if there is NO POSITION, the program will not send a SELL order. These conditions are to prevent holding more than 1 security and to prevent going into a SHORT 
position on a given symbol. The program continuously prints out logs when it recieves messages from Binance and when it executes orders or detects OVERSOLD or OVERBOUGHT 
conditions. On top of this, it will continuously print out an array with all of its calculated RSI's every minute as is revieves the complete bar from the websocket.

#What the files do
The requirements.txt file holds required python packages and useful terminal commands.

The config.py file holds the API key ID and the API secret key that you must insert from your Binance account, the variables have been left as empty strings in the config file
to show where they must be inserted. 

Bot.py holds the real code of the program.


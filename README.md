# PROREALTIME

//-------------------------------------------------------------------------
// Main code : RSI Buy on dips 
// Definition of code parameters
DEFPARAM CumulateOrders = TRUE // Cumulating positions deactivated

// Conditions to enter long positions
Indicator4 = AverageTrueRange[10](close)
c4 = (indicator4 < indicator4[1])
c50=((RSI[50](close)-RSI[10](close))>10)

IF c4 AND c50 THEN
BUY 1 CONTRACT AT MARKET
ENDIF

c53=((RSI[50](close)-RSI[10](close))< 5)

IF c53 THEN
SELL AT MARKET
ENDIF

// Conditions to enter short positions
indicator10 = AverageTrueRange[10](close)
c10 = (indicator10 < indicator10[1])
c51=((RSI[10](close)-RSI[50](close))>10)

IF c10 AND c51 THEN
SELLSHORT 1 CONTRACT AT MARKET
ENDIF

// Conditions to exit short positions
c54=((RSI[10](close)-RSI[50](close))<5)

IF c54 THEN
EXITSHORT AT MARKET
ENDIF![GBP](https://user-images.githubusercontent.com/67822973/103166972-2c2be080-4862-11eb-8d8e-2abbe458bedf.PNG)
![AUD](https://user-images.githubusercontent.com/67822973/103166973-2df5a400-4862-11eb-939b-40e8dfdaca5c.PNG)
![CAD](https://user-images.githubusercontent.com/67822973/103166974-2f26d100-4862-11eb-88bc-f8c3cc1342dd.PNG)
![EUR](https://user-images.githubusercontent.com/67822973/103166975-2fbf6780-4862-11eb-8ea7-9a325b65a3c6.PNG)

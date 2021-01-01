This is a simple buy on dips formula using the RSI indicator. The below codes are used on the PRO REAL TIME system which has a list of technical indicators. Basically we enter the trades when the short term RSI deviates too much from the long term RSI and we aim to exit the trade when they are closer together. An additional condition will be that we will only enter the trade when the ATR is lower than the day before, to reduce the probability of catching a falling knife. We want to enter the trade when there is reduced volatility. I tested this on four major currency pairs, the GBP, AUD, CAD and EUR. All four currencies experienced upward movements in the equity curve using this strategy, but this strategy works better in the last ten years compared to the periods before that.

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

This is when the difference is 15 and we exit at 10.
![AUD1510](https://user-images.githubusercontent.com/67822973/103436137-81e1fd80-4c53-11eb-8e5f-b5437b44a3c1.PNG)
![CAD1510](https://user-images.githubusercontent.com/67822973/103436138-83132a80-4c53-11eb-8af9-ca58092a438c.PNG)
![EUR1510](https://user-images.githubusercontent.com/67822973/103436140-84445780-4c53-11eb-9e75-eac20eaa2942.PNG)
![GBP1510](https://user-images.githubusercontent.com/67822973/103436141-84dcee00-4c53-11eb-9c0a-3b34c19bdac1.PNG)

This is when the difference is 20 and we exit at 15. With this large difference, the trades are lesser.
![EUR2015](https://user-images.githubusercontent.com/67822973/103436144-8b6b6580-4c53-11eb-8dbf-8794b5ff78eb.PNG)
![GBP2015](https://user-images.githubusercontent.com/67822973/103436146-8c9c9280-4c53-11eb-99d3-53beedaa18de.PNG)
![AUD2015](https://user-images.githubusercontent.com/67822973/103436147-8d352900-4c53-11eb-9252-2345ace8bc9f.PNG)
![CAD2015](https://user-images.githubusercontent.com/67822973/103436148-8dcdbf80-4c53-11eb-85ee-d1dcfac7ae90.PNG)


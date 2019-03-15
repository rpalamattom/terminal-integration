# terminal-integration
Experiments in POS and ATM integration
# terminal-integration
Experiments in POS and ATM integration
# ATM Initiated Cash Out

# Transaction flow
Firstly, customer will have to generate OTP through mobile application for desired ATM Initiated Cash-out amount. This OTP will be sent to customer’s mobile number. 
We intend to use the FSP simulator to simulate the Payer and Payee FSP's. An endpoint to generate and validate OTP will be implemented on the Simulator. The ATM/POS driver would be responsible for the conversion of ISO to Open API

•	Customer generates an OTP before initiating the transaction request from ATM.
•	The customer initiates withdrawal transaction on the ATM by entering their account ID and amount. 
•	Cash Out Request will be generated by ATM Driver in NDC protocol. This will be converted to OPEN API call and will be sent to Mojaloop.
•	Mojaloop will perform Account lookup and the transaction request will be sent to Payer FSP for authentication.
•	The Payer FSP validates the transaction request and also calculate the Quote for the transaction.
•	The calculated Quote will be displayed on the Terminal for confirmation by the Payee.
•	The Customer will authenticate the transaction by entering pre-generated OTP.
•	Payer FSP will authenticate the OTP. 
o	If successful, the customer’s account will be debited, and the ATM account maintained by Payee FSP will be credited.
•	Payer FSP will send response back to Mojaloop.
•	Response will be received by ATM Driver in OPEN API. This will be converted to ISO and is sent to ATM.
•	ATM will perform the actions as mentioned by the message. (Dispense and Print etc.)

# Merchant Initiated Merchant Payment Authorised on POS

# Transaction flow

•	Customer requests for an OTP ( pre-generate OTP using mobile app/CMS)
•	Merchant will initiate payment for the desired amount and Customer ID through POS device.
•	The request will be converted from ISO to OPEN API and will be sent to Mojaloop. From there account lookup will be done and the request will be send to Payer FSP for authorization.
•	The Payer FSP validates the transaction request and also calculate the Quote for the transaction.
•	The calculated Quote will be displayed on the Terminal for confirmation by the Payee. 
•	The Payer FSP will authorize the transaction with dynamic OTP (or QR Code) which is generated through mobile application and entered by the customer.
•	If Payer FSP authorizes the transaction, funds will be sent to Merchant (Payee) FSP. If Payer FSP declines, the transaction will be aborted. 
•	Response will be sent back to POS driver through Mojaloop in OPEN API. It will be converted to ISO(POS) and will send the response to POS.
•	Notification will be sent to Payer and Payee from respective FSP’s.


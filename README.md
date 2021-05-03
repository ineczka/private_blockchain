# Purpose



## What problem will you solve implementing this private Blockchain application?

Test application that allows to save  stars on a private blockchain and check to ownes stars.

### Functionality

1. The application will create a Genesis Block when we run the application.
2. The user will request the application to send a message to be signed using a Wallet and in this way verify the ownership over the wallet address. The message format will be: `<WALLET_ADRESS>:${new Date().getTime().toString().slice(0,-3)}:starRegistry`;
3. Once the user have the message the user can use a Wallet to sign the message.
4. The user will try to submit the Star object for that it will submit: `wallet address`, `message`, `signature` and the `star` object with the star information.
    The Start information will be formed in this format:
    ```json
        "star": {
            "dec": "68° 52' 56.9",
            "ra": "16h 29m 1.0s",
            "story": "Testing the story 4"
		}
    ```
5. The application will verify if the time elapsed from the request ownership (the time is contained in the message) and the time when you submit the star is less than 5 minutes.
6. If everything is okay the star information will be stored in the block and added to the `chain`
7. The application will allow us to retrieve the Star objects belong to an owner (wallet address). 


## Tools or technologies  used

- This application is using Node.js and Javascript. The architecture will use ES6 classes  to organize the code and facilitate the maintnance of the code.
- The company suggest to use Visual Studio Code as an IDE to write your code because it will help you debug the code easily
but you can choose the code editor you feel confortable with.

- Some of the libraries or npm modules you will use are:
    - "bitcoinjs-lib": "^4.0.3",
    - "bitcoinjs-message": "^2.0.0",
    - "body-parser": "^1.18.3",
    - "crypto-js": "^3.1.9-1",
    - "express": "^4.16.4",
    - "hex2ascii": "0.0.3",
    - "morgan": "^1.9.1"
   

Libraries purpose:

1. `bitcoinjs-lib` and `bitcoinjs-message`. To verify the wallet address ownership / the signature.
2. `express` The REST Api created for the purpose of this project it is being created using Express.js framework.
3. `body-parser`  library used as  a middleware module for Express and  to read the json data submitted in a POST request.
4. `crypto-js` This module contains some of the most important cryotographic methods used to create the block hash.
5. `hex2ascii` Tused to 'decode' the data saved in the body of a Block.



## How to test application functionalities?


1. Run the application using the command `node app.js`
You should see in your terminal a message indicating that the server is listening in port 8000:
> Server Listening for port: 8000

2. To make sure your application is working fine and it creates the Genesis Block you can use POSTMAN to request the Genesis block:
    Request: http://localhost:8000/block/0 
3. Make your first request of ownership sending your wallet address:
    Request: http://localhost:8000/requestValidation 
4. Sign the message with your Wallet ()   
5. Submit your Star
     Request: http://localhost:8000/submitstar
6. Retrieve Stars owned by the wallet addresss
    Request: http://localhost:8000/blocks/<WALLET_ADDRESS>
7. Request block by hash value 
    Request: http://localhost:8000/block/hash/:hash
	
	
	

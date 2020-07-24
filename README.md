![Logo](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/FuncLogo.png)
# FunctionCoin Masternode Setup Guide
This guide will assist you in setting up a FunctionCoin Masternode on a Linux Server running Ubuntu 16.04 or 18.04.

This guide will show you the safest setup for running a masternode.  This type of setup is known as a Hot/Cold wallet setup.  In this type setup you will have 2 wallets (one with the coins, and one without the coins).  It is the safest setup because your coins will reside in a "cold" wallet ("cold" means that it does not need to constantly be connected to the internet). In this setup, there is very little risk of someone hacking onto your wallet and taking your coins.

If you require further assistance contact the support team on Discord (https://discord.gg/SFc6EsX)
***
## Requirements
1) **50001 FUNC coins. (50000.01 coins will work, but it is simpler to say 50001 is required)**
2) **A VPS running Linux Ubuntu 16.04 or 18.04. (A VPS can be gotten from many companies, but this guide will show screenshots from Vultr, but the method to create the masternode should not change, only the screens when purchasing the VPS or getting the VPS IP address and password may look slightly different if you use a different provider)**
3) **A Windows, Mac, or Linux QT wallet running on a local machine (like your home computer).**
4) **An SSH client such as Bitvise (https://bitvise.com/ssh-client-download)  (if you prefer to use Putty or another SSH client, then the instructions will be the same, just that the screenshots below will look different)**
***
## Contents
* **Section A**: Creating the VPS within Vultr
* **Section B**: Downloading and installing Bitvise.
* **Section C**: Connecting to the VPS and installing the MN script via Bitvise.
* **Section D**: Preparing the local (cold) wallet
* **Section E**: Obtaining the coins to run a masternode
* **Section F**: Creating the collateral transaction
* **Section G**: Starting the masternode.
***

## Section A: Creating the VPS within Vultr
***Step 1***
* Register at Vultr (https://www.vultr.com/?ref=7409995)
*Full disclosure note: This is a referral link.  I will get a small commission if you use it. You will also get a bonus if you use it. But you will get the same bonus if you use a referral link from a friend.
***

***Step 2***
* After you have added a payment method (and funds if appropriate) to your Vultr account go here (https://my.vultr.com/deploy/) to create your VPS
***

***Step 3*** 
* Choose the `Cloud Compute` option and then choose a server location (preferably somewhere close to you)

![Create VPS Step 3](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionAStep3.jpg "Create VPS Step 3")
***

***Step 4***
* Choose a server type: Ubuntu 16.04 or 18.04 (if you plan to use this VPS for other masternode coins, it may be best to choose 16.04 for now as some may not have good setups for 18.04)
* Choose a server size: $5/month is sufficient (a smaller size may work, but you should investigate and research before using a smaller size)

![Create VPS Step 4](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionAStep4.jpg "Create VPS Step 4")
***

***Step 5*** 
* Set a Server Hostname (use any name you want to help you remember this VPS. You can use the coin's name to help you remember this server has FUNC on it, but in the future if the VPS has room, you can run masternodes of other coins to this VPS, so you may simply want to name it `Ubuntu1601_1` or something similar)
* Click `Deploy now`

![Create VPS Step 5](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionAStep5.jpg "Create VPS Step 5")
***

## Section B: Downloading and installing BitVise. 

***Step 1***
* Download Bitvise (https://bitvise.com/ssh-client-download)
* Click the button in the middle of screen to download latest version.
***

***Step 2***
* Select the correct installer depending upon your operating system. Then follow the install instructions. 
***


## Section C: Connecting to the VPS & Installing the MN script via Bitvise.

***Step 1***
* Log into Vultr (https://my.vultr.com)
* In the middle of the screen, click the link to your VPS you just created
* Here you can find your VPS IP and password for use in the following steps. To copy the IP or the password to your clipboard when needed in following steps, you would click the `copy` icon next to them.

![VPS IP and Password](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionCStep1.jpg "VPS IP and Password")
***

***Step 2***
* Open the bitvise application
***

***Step 3***
* In the bitvise application, fill in the following...
  * `Host` - paste the IP address you copied from the Vultr screen
  * `Port` - type `22`
  * `Username` - type `root`
  * `Initial method` - choose `password` in the dropdown
  * `Store encrypted password in profile` - check this box if you don't want to have to type the password each time. This is fine because you should never store coins in the wallets on this VPS, so even if someone hacked onto your VPS, they could never get to any of your coins
  * `Password` - paste the password you copied from the Vultr screen
* Click the `Save Profile` button to save this information to easily log in the next time
* Click the `Log In` button to log into the VPS
* The first time you connect, you will be alerted that Bitvise noticed this is a new computer and wants to confirm you really want to connect to it. Press the `Accept and Save` button

![Configure Bitvise](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionCStep3.jpg "Configure Bitvise")
***

***Step 4***
* Once you are connected, you may have 2 new windows appear. One window is a file transfer window, the other (the one that is mostly black screen) is the terminal window. If the file transfer window does appear, just press the "X" in the top right corner to close it as you do not need it.

![CloseFileTransferWindow](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionCStep4.jpg "Close file transfer window")
***

***Step 5***
* Paste the code below into the Bitvise terminal then press the `<enter>` key on the keyboard (it will just go to a new line because it is downloading a very small script)
 * Note: To paste in the Bitvise terminal you can simply right-click the mouse and whatever is in your clipboard will automatically paste. Do not use `<CTRL>+<V>` keyboard combination or any control keys like that while using Bitvise.

`wget -q https://raw.githubusercontent.com/Function-Coin/FUNC-MN-Setup-Guide/master/Function_coin_install.sh`

***

***Step 5***
* Paste the code below into the Bitvise terminal then press the `<enter>` key on the keyboard

`chmod +x FUNC_mn_install.sh`

***


***Step 6***
* Paste the code below into the Bitvise terminal then press the `<enter>` key on the keyboard (this will run the script from above and may take a few minutes to complete)

`bash FUNC_mn_install.sh`

***

***Step 6***
* When prompted to `Enter your FUNC Masternode Private Key`, DO NOT type or press any keys, just move this terminal window to the side and go on to the next steps. We will return to this terminal window after we get the masternode private key from your local controller wallet.
***

## Section D: Preparing the local (cold) wallet 
***Step 1***
* Download the latest "QT" wallet for your operating system
  * https://github.com/Function-Coin/FUNC/releases
***

***Step 2***
* Install the wallet and allow it to synchronize fully. If there are no connections or it is not synchronizing, go to the FUNC discord server (https://discord.gg/SFc6EsX) and search for "addnode" for a list of addnodes and instructions to get the wallet to synchronize.
***

## Section E: Obtaining the coins to run a masternode. 
Now you need to get the coins to run a masternode.  Remember, you will need a little more than 50000 coins to start a masternode.  50000.01 coins would be enough, but I would get at least 50001 coins to be safe.  You need this small amount of extra coins to pay the transaction fee to make the "collateral transaction" in a later step below.  If you already have enough coins to run the masternode in your wallet, then just skip to next section (Creating the collateral transaction).  If you do not have enough coins in your wallet yet, then follow these instructions.

***Step 1***
* Open the wallet and go to the `Receive` tab and click the `Generate Address` button to create a new receiving address.
* Click the `Edit Label` button and type a label for this address. If you are getting coins from an exchange, use a label like `From Crex24` or if you are buying OTC use a label like `From OTC Sale`.
* Click the `Save` button to save the label to the address.
* Now you can click the `Copy` button to copy the address to your clipboard so you can paste it into the the withdraw screen of the exchange or to the person you are purchasing OTC coins from (only purchase OTC coins from an official team member. If you have never purchased coins from someone in discord, or are are not sure how to do it safely, then ask for help in the discord server. And NEVER trust someone who DM's you first, you should always DM a team member first because it is extremely easy for someone to spoof to be a team member in discord. If you are even the slightest bit unsure, ask for help in the discord server on how to verify a user using the discord ID of an individual (the discord ID is an 18 digit number. The discord ID is NOT the 4 digits after someone's name, that number can also be spoofed)
  *NOTE: When withdrawing from an exchange, always send a small test transaction first.  If the test is successful, then send the full amount.  Meaning, if you are withdrawing from an exchange, just withdraw 1 coin.  If you receive that coin in your wallet, then withdraw the rest of the coins.
* Once you have at least 50000.01 coins in your wallet, you can move on the the next section.  
***

## Section F: Creating the collateral tranaction.
In this section you will be sending yourself exactly 50000 coins in one single transaction. This is known as the "collateral transaction". As long as you are running your masternode, these coins will be locked in your wallet and will not stake, they will only be used to keep your masternode running and receiving masternode rewards.

***Step 1***
* Open the wallet and go to the `MASTERNODES` tab and click the `Create Masternode Controller` button
* The next screen says you need 10000 FUNC to create a masternode, that was an older amount and the screen needs to be updated. You currently need 50000 FUNC to create a masternode. Just click the `Next` button if you have at least 50000.01 FUNC.
* The next screen asks for a name for your masternode. Something like `MN1` is usually what people use for their first masternode. Enter a name and click the `Next` button.
* Then next screen asks for an IP address and Port.  Enter your VPS IP address (the one you copied from the Vultr screen in the steps above), and leave the `Port` value set to 12280. Then click the `Next` button.

![CreateMasternodeController](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionFStep1.jpg "Create Masternode Controller")
***

***Step 2***
* The wallet will automatically send the required coins to a new address that has the same label as what you chose for the name of the masternode.
* Now click the 3 dots at the far right side of the line item for the masternode you just created and choose the `Info` item in the menu that appears.

![3Dots](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionFStep2.jpg "3Dots")
***

***Step 3***
* In the next window, click the `copy` icon on the right side of the text `Export data to run the Masternode on a remote server`

![ExportDataButton](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionFStep3.jpg "Export Data Button")
***

***Step 4***
* A new window will appear to tell you it will place some information about your masternode in your clipboard.  Just press the `OK` button
* Now you have some information in your clipboard. Open a notepad or similar type document so you can paste the information in your clipboard.
* When you paste the information into a notepad or similar document, you will see lots of information. You want to now copy the value for your `masternodeprivkey`. Do not copy the `masternodeprivkey=` portion, just copy the string of letters and numbers after it.

![Masternodekey](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionFStep4.jpg "Masternode Key")
***

***Step 5***
* Go back to your bitvise terminal and paste the private key into the window and press the `<enter>` key on the keyboard (your bitvise terminal should still be on the prompt we left it on where it is asking for you to enter the masternode private key) (remember, to paste in bitvise terminal, you just right-click the mouse and it will paste automatically)
 
![PasteKey](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionFStep5.jpg "Paste Key")
***
 
***Step 6***
* After a minute or two, the window should change and display a bunch of information regarding your masternode.
* Now you need to wait until the masternode wallet has synced.  To see how far along it is, type `func-cli getinfo` and press the `<enter>` key on the keyboard.  As soon as the "block" line item shows that it has the same number of blocks as the FUNC explorer (http://144.91.96.216:3001), then it is synced.
* Once it is synced, you can move on to the next steps
 
 ![CheckBlockCount](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionFStep6.jpg "Check Block Count")
***

## Section G: Starting the masternode.
***Step 1***
* Go to the `MASTERNODES` tab in the wallet
* Click the 3 dots at the far right side of the line item for the masternode you just created and choose the `Start` item
* It will ask if you really want to start the masternode, click the `OK` button
* It should say the masternode was succesfully started
* The local controll wallet is not always correct, so you must confirm the masternode was started on the VPS wallet. So, go back to your Bitvise terminal and type `func-cli getmasternodestatus`
* You should see a message stating status 4 and the masternode successfully started. If you do not see this, then go to the discord support channels for assistance
* You can now press the "X" button in the top right of the terminal to close it.
* You can also shut down your local wallet on your home computer if you wish and your masternode will continue to collect rewards because it is running on the VPS server which will be connected 24/7.

 ![MasternodeStatus](https://github.com/Function-Coin/FUNC-Masternode-Install/tree/master/images/SectionGStep1.jpg "Masternode Status")
***

## Last Step. (this is critical, you must do this)
***Register your masternode with the bot***
* Join the FUNC discord server (https://discord.gg/SFc6EsX)
* Go to the #mn-registration channel
* type `=register` to have the bot contact you and get walk you through the registration process.
* You MUST register your masternode with the bot to be included in lottery winnings.

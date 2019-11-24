---
title: The Ultimate Guide to ENS Names
description: ENS offers a secure & decentralized way to address resources both on and off the blockchain using simple, human-readable names.
author: Eric Conner
date: 2019.11.12
---

The Ethereum Name Service is one of the most popular projects on Ethereum right now and for good reason. As the [website state](https://ens.domains/)s, "ENS offers a secure & decentralized way to address resources both on and off the blockchain using simple, human-readable names."

In short, you are able to give your Ethereum (or [favorite chain](https://medium.com/the-ethereum-name-service/ens-launches-multi-coin-support-15-wallets-to-integrate-92518ab20599)) address a name. This is much like how the traditional web works with DNS. All websites are hosted at an IP address but no one actually puts that in their browser, instead we use names such as amazon.com, not 205.251.242.103 (try it, it works!). The ENS has many great features but I'm going to focus this guide specifically on registering and managing .eth names and their subdomains.

## Registering .eth Domain Names

The core functionality of the ENS is registering .eth domains. There are a few important rules to keep in mind when it comes to registering domains on the ENS:

1.  Minimum domain length is 3 characters.
2.  Annual renewal fees. 3 characters: $640/year, 4 characters: $160/year, 5+ characters $5/year.
3.  Emojis are valid. 👍🏼

### Creating and Managing Domains

Registering a domain is extremely easy using the [ENS app](https://app.ens.domains/). First search for the ENS name that you'd like. If it is not taken (if it is, head over to [OpenSea](https://opensea.io/assets/ens) and search for it), you will be presented with this screen.

![ENS domain registration](https://uploads-ssl.webflow.com/5dd9663ccd7d37bf25198e1c/5ddaf8b0967a3b951b359ef9_1*JmZtvp31arC9p8eMB6FI1Q.png)

Once here you can click request to register which will trigger a transaction, wait 1 minute and then you can register the name. It's now yours.

Now that you own a .eth domain, you want to enable all the cool features that it offers. This starts on the domain management screen.

![ENS domain management](https://uploads-ssl.webflow.com/5dd9663ccd7d37bf25198e1c/5ddaf8b0967a3b58d1359efa_1*smv_7Mt5aGhtNKPepSTJPg.png)

There is a lot going on so let's put all of the pieces together:

-   Registrant: can set the controller address, and transfer the registration to someone else. This is the ultimate owner.
-   Controller: essentially handles the "day to day operations" of the domain.
-   Expiration Date: when your renewal fee is due and you can pay it here as well.
-   Resolver: handles resolving (translating) the records put below such as what Ethereum address is tied to this domain. Should be set the [public resolver](https://docs.ens.domains/contract-api-reference/publicresolver) which will be the default option when clicking the Set button.
-   Records: this is where you can add the cool stuff to your domain. Put an address here so that when you put your domain name in a wallet, it points to this address. You can also put an IPFS content hash which when going to your domain in a web browser will pull up your website.

Once you set an Ethereum address in the address field, it will resolve in wallets such as MetaMask.

![](https://uploads-ssl.webflow.com/5dd9663ccd7d37bf25198e1c/5ddaf8b0cd7d3781cb237152_1*qLi1BktjCFOJ1QEb903XVQ.png)

MetaMask support for ENS names

And if you point it to an IPFS hash, you can pull up the domain at ethhub.eth/ or ethhub.eth.link for browsers that don't resolve ENS names.

## Subdomains

Subdomains offer great flexibility for building on top of .eth domains. If you are a company such as Maker and want to issue all your employees maker.eth subdomains, this is very easy to do. This section will cover both creating subdomains on a domain you own and unique ways of allowing others to buy subdomains on a domain you own.

### Creating and Managing Subdomains

If you own a .eth domain and simply want to create subdomains for your own use, the easiest way to do this is through the ENS app by clicking on the Subdomains button. This is where you can add new subdomains.

![ENS Subdomain Registration](https://uploads-ssl.webflow.com/5dd9663ccd7d37bf25198e1c/5ddaf8b0967a3b29ea359efb_1*TFAij9M1PQ6LT43_Nn-NNA.png)

Once subdomains are setup, they act very similar to domains in that the owner can control them and setup records. That means something like eric.ethhub.eth can also resolve to an address and an IPFS website.

![
ENS Subdomain Manager](https://uploads-ssl.webflow.com/5dd9663ccd7d37bf25198e1c/5ddaf8b0578babcfa2270133_1*d03OAsK3DtljwtLKSDhtIA.png)

### Allowing Anyone to Claim Subdomains on your .eth Domain

All of the above is being done by the registrant of the .eth domain. They are the one setting up the subdomains and have ultimate control over them, including being able to revoke them. This is fine for a company or someone that wants full control over the subdomains but what if you want anyone in the world to be able to claim a subdomain on your domain? You obviously don't want to have to coordinate with them and they won't want you to be able to revoke access. The good news is there is a solution that easily allows you to open up registration of subdomains on your domain. You can even set a price at which you'd like to sell them.

Doing this starts with turning control of your domain over to the [ENS Subdomain Registrar](https://github.com/ensdomains/subdomain-registrar) contract. This means that the contract is able to distribute out subdomains to people but you no longer can revoke access to those subdomains. The steps at the moment are fairly manual but also easy. Nick Johnson lays out the steps well in this [ENSNow domains post](https://medium.com/the-ethereum-name-service/migrating-your-ensnow-domains-to-the-new-registrar-c0085eaaeff2) so I'm going to just put them here:

**Warning: By doing this, you are permanently giving up use of your domain! You will be able to collect registration fees, change prices, and transfer control to another user --- but you will never be able to use your domain for anything else!**

1.  Load up the [.eth registrar contract](https://etherscan.io/address/0xfac7bea255a6990f749363002136af6556b31e04#writeContract). If you are using Etherscan, you will need to click "Connect with Metamask" and authorize the subsequent dialog box from Metamask.
2.  Find the 'approve' function.
3.  In the address field, enter '0xc32659651d137a18b79925449722855aa327231d'
4.  In the tokenId field, enter the labelhash of your name. You can look this up by searching for your name on etherscan (look for 'Label hash [foo]:').
5.  Submit the transaction.
6.  Load up the [new subdomain registrar contract](https://etherscan.io/address/0xc32659651d137a18b79925449722855aa327231d#writeContract).
7.  Find the 'configureDomain' function.
8.  In the name field, enter the name you want to list, without '.eth' (Eg, 'gimmethe', not 'gimmethe.eth').
9.  In the price field, enter the price to charge for a new domain, in wei. 1 ether is 1,000,000,000,000,000,000 wei, so for instance to charge 0.01 ether per domain, you should enter 10000000000000000. A convertor can be found [here](https://gwei.io/).
10. In the referralFeePPM field, enter the amount you want to give to any website that finds a new user for you. For instance, to keep the entire amount yourself, enter 0; to give it all to the site, enter 1000000.
11. Submit the transaction.

Your domain has now been handed over to the subdomain registrar contract. If you've set up a fee, anytime someone registers a subdomain, the funds will be directed to the original owner address. This has now opened up a lot of possibilities!

### Listing Your Subdomains on ENSNow

The ENS team has setup a [website](https://now.ens.domains/) which allows for claiming of subdomains. If you'd like your subdomains listed here the process is quite easy. Once again Nick has a [blog post](https://medium.com/@weka/how-to-list-your-domain-on-ensnow-7297808f31f5) about the steps and I'm going to put them below:

1.  Go to [this page](https://github.com/ensdomains/subdomain-registrar) and click 'fork' in the top right corner.
2.  Navigate to app -> js -> domains.json
3.  Click on the pencil icon in the top right corner of the file.
4.  Find the appropriate place to insert your entry (entries are listed alphabetically).
5.  Add a new line with your entry. If using the default registrar for steps 2 and 3, this should look like {"name": "yourdomain", "version": "1.0"}, .
6.  Commit your changes by clicking 'Commit changes' down the bottom of the page.
7.  Click on 'Pull requests', then 'New pull request'.
8.  Click on 'Create pull request'.

![ENSNow](https://uploads-ssl.webflow.com/5dd9663ccd7d37bf25198e1c/5ddaf8b0d31f0f455768944d_1*EObI7awG85GjvIIcvQa9FQ.png)

### Hosting Your Own Subdomain Sale Site

ENSNow is great and easy, but the list of domains supported there is rather long and you cannot specifically brand your own domain. So, if you'd like to setup a site that only lists your domain and allows you to customize it, that is possible as well. A good example of this is a site I'm running called [Ethmojis](https://ethmojis.com/).

The best place to start is on the [Subdomain Registrar GitHub page](https://github.com/ensdomains/subdomain-registrar). They have a "getting started" section which tells you how to run it but I'll try to summarize the steps up as best as I can below

1.  Install [node.js and NPM](https://www.npmjs.com/get-npm)
2.  Install Truffle on your computer using npm install -g truffle
3.  Download and install [Ganache](https://www.trufflesuite.com/ganache)
4.  Clone the [subdomain-registrar repo ](https://github.com/ensdomains/subdomain-registrar)to your computer.
5.  In terminal, navigate to the folder you cloned it to and run npm install
6.  Find the /app/js/domains.json file and edit the whitelist to only include your domain. Mine looks like: [{"name": "ethmojis", "version": "1.0"}]
7.  Edit the index.html file however you'd like for your site.
8.  In terminal, change directory to where you cloned the subdomain registrar.
9.  Run:ganache-cli &\
    truffle deploy\
    npm run dev
10. If everything looks goo, runnpm run build
11. A build folder should be created and files output here. This is your final site that you can upload to a web server or IPFS.

To host on [IPFS](https://docs.ipfs.io/introduction/usage/), upload the entire build folder and get your content hash. You can then put this content hash in the "records" section of any ENS domain or subdomain! Here's an example of how it will look:

![Buy Ethmojis](https://uploads-ssl.webflow.com/5dd9663ccd7d37bf25198e1c/5ddaf8b0578bab551e270134_1*w23CnIdpGZcCP-X_ORZU1w.png)

Congrats, you are now an expert on the Ethereum Name Service!

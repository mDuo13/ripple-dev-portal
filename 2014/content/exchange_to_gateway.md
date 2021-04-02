# Becoming a Ripple Gateway #

An existing online financial service, such as a payment system or digital currency exchange, can provide additional value to customers by acting as a Ripple Gateway. Users gain access to a new cross-currency payment network, and gateways gain a new revenue source for transfers into, out of, and even within Ripple.

Expanding an existing exchange system to support Ripple is a relatively simple task. This document explains the concepts necessary to set up a system, and covers the details of doing so. In this document, we use a fictional online currency exchange named "ACME" and its users as examples, to show how ACME can expand its business to include being a Ripple Gateway.

## Ripple Gateways Explained ##

A Ripple _*Gateway*_ is an entity that exchanges balances in the Ripple Network for balances in the outside world -- which is like performing deposits and withdrawals from Ripple. Typically, a Gateway holds money (or other assets of value) outside of Ripple, and creates _*issuances*_ in the Ripple Network to represent them. Within Ripple, issuances can be sent, traded, and exchanged atomically without the gateway's intervention. 

Ripple's native cryptocurrency, XRP, can also be exchanged for issuances, and sent to any Ripple account, but exists only within the Ripple Network. All Ripple accounts need a small reserve of XRP in order to pay the network costs of maintaining their accounts and sending transactions. Some users may choose to hold additional XRP to use as a means of exchange, but large holdings of XRP are not strictly necessary to operate a gateway.


### Ripple Trust Lines and Issuances ###

All assets in Ripple, except for the native cryptocurrency XRP, are represented as *issuances*, which are digital assets that reflect traditional assets held by a gateway. Within Ripple, issuances can be divided, sent, and traded with very low barrier to entry. Issuances get their value from the promise that the gateway issuing them will honor the obligation that the issuances represent; there is no computer system that can force a Ripple gateway to honor that obligation. Therefore, Ripple's *trust lines* ensure that users only hold issuances from gateways they trust to pay out when needed.

A "trust line" is link between two accounts in Ripple that represents an explicit statement of willingness to hold gateway debt obligations. When a user sends money into Ripple, a Gateway takes custody of assets in the outside world, and sends issuances within the Ripple network to the user. When a user sends money out of Ripple, she "redeems" the issuances with the Gateway's Ripple account, and the gateway sends the assets to the user in the outside world.

### XRP ###

XRP is the native [cryptocurrency](https://ripple.com/knowledge_center/math-based-currency/) of the Ripple network. Unlike issuances, XRP is not connected to a trust line, and can be sent directly from any Ripple account to any other, without going through a gateway or market maker. For this reason, XRP is a convenient bridge currency to facilitate currency exchanges.

XRP also serves other purposes in the Ripple network, in particular as [a protective measure against spamming the network](https://ripple.com/knowledge_center/abuse-protection/). 

Gateways do not need to accumulate or exchange XRP. They must only maintain a small balance of XRP to send transactions on the network. The XRP equivalent of $10 USD is enough for a busy gateway to operate for a year.

### Liquidity and Currency Exchange Within Ripple ###

The Ripple network contains a distributed financial exchange, where any user can place and fulfill bids to exchange issuances and XRP. Cross-currency payments automatically use the financial exchange to convert currency atomically at the time of sending. In this way, users who choose to become market makers provide the liquidity that makes the Ripple Network useful.

When adding a new gateway to the Ripple network, it is important to establish liquidity to other popular currencies. Since third-party market makers perform the exchanges, a gateway can provide currency-exchange services through Ripple without having to keep a large reserve of currencies or shoulder the risk of financial exchange.

Contact [partners@ripple.com](mailto:partners@ripple.com) for help establishing a market between your gateway and others.


## Suggested Business Practices ##

The value of a gateway's issuances in Ripple comes directly from users' trust that the gateway will pay withdrawals when needed. Since a gateway cannot pay out if it shuts down, it is also in users' interest that a gateway does not shut down. There are a number of precaution a gateway can take that reduce the risk of business interruptions:

* Use [Hot and Cold Wallets](#hot-and-cold-wallets) to limit your risk profile on the network.
* Comply with anti-money-laundering regulations for your jurisdiction, such as the [Bank Secrecy Act](http://en.wikipedia.org/wiki/Bank_Secrecy_Act). This usually includes requirements to collect ["Know-Your-Customer" (KYC) information](http://en.wikipedia.org/wiki/Know_your_customer).
* Read and stay up-to-date with [Gateway Bulletins](https://ripple.com/knowledge_center/gateway-bulletins/), which provide news and suggestions for Ripple gateways.
* Clearly publicize all your policies and fees.


### Hot and Cold Wallets ###

It is strongly recommended that Ripple gateways employ a "hot wallet / cold wallet" strategy. This enforces a separation of roles that promotes strong security. ("Wallets" in Ripple are equivalent to Accounts.)

The cold wallet is like a vault. It serves as the asset issuer, and should remian offline. The secret key that is used for this wallet is kept offline, accessible to only a few trusted operators. Periodically, a human operator creates and signs a transaction (preferably from an entirely offline machine) in order to refill the hot wallet's balance. Because the cold wallet is the account creating the issuances, customer accounts holding those issuances must trust the cold wallet. 

A hot wallet is like a cash register. It makes payments to the gateway's users in Ripple by sending them issuances created by the cold wallet. The secret key for a hot wallet is, by necessity, stored on a server that is connected to the outside internet, usually a configuration file for the software that performs gateway operations. Because it holds issuances created by the cold walet, each hot wallet needs a trust line to the cold wallet. Customers do not, and should not, trust hot wallet accounts.

(Unlike a cash register, the hot wallet does not have to handle incoming payments from users, because the cold wallet can receive and monitor payments without using its secret key. To make things simple for your users, we recommend treating incoming payments to the hot and cold wallets as the same.)

A gateway can use one or more "hot wallet" accounts, but each hot wallet has a limited balance of the gateway's issuances. If a hot wallet is compromised, the gateway only loses as much currency as that account holds. Customers do not need to change any configuration in order to receive funds from a new hot wallet. However, the gateway must monitor the hot wallet's balance so that it doesn't run out of funds during ordinary operation.

If a cold wallet is compromised, the attacker could create an unlimited amount of issuances, which makes it very difficult to redeem legitimately-held issuances fairly. In this case, the gateway must create a new cold wallet account, and all users with trust lines to the old gateway must create new trust lines to the new account. (Thus, it's best to keep your cold wallet as secure as possible.)

### Warm Wallets ###

Another optional step that a gateway can take to balance risk and convenience is to use "warm wallets" as an intermediate step between cold wallet and hot wallet. Frequently, the software that runs a gateway's daily operations uses a single hot wallet. The gateway can operate additional accounts as warm wallets, whose keys are entrusted to different trusted users and whose keys are also not stored for use by the gateway software. 

When the hot wallet is running low on funds, the warm wallets can be used to refill it. When the warm wallets run low on funds, the cold wallet can issue more currency to a warm wallet in a single transaction, and the warm wallets can distribute that currency among themselves if necessary. This improves security of the cold wallet, since it makes as few transactions as possible, without leaving too much money in the control of a single automated hot wallet.

As with hot wallets, warm wallets must trust the cold wallet, and should not be trusted by users. All precautions that apply to hot wallets also apply to warm wallets.


## Fees and Revenue Sources ##

There are several ways in which a gateway can seek to benefit financially from Ripple integration. These can include:

* Indirect revenue from value added. Ripple integration can provide valuable functionality for your customers that distinguishes your business from your competitors.
* Withdrawal and Deposit fees. It is typical for a gateway to charge a small fee (such as 1%) for the service of adding or removing money from Ripple. You have the power to determine the rate you credit people when they move money onto and off of Ripple through your gateway.
* Transfer fees. You can set a percentage fee to charge automatically when Ripple users send each other issuances created by your account. This amount is debited from the Ripple ledger, decreasing your obligation each time your issuances change hands. See [TransferRate](#transferrate) for details.
* Interest on Ripple-backed funds. You can keep some of your Ripple-backing currency in an external account that earns interest. Just be sure the external account's policies do not interfere with your ability to adequately serve your customer withdrawals. (For example, limits on withdrawing money, or risk of losses.)
* Market making. A gateway can also make offers to buy and sell its issuances for other issuances on Ripple, providing liquidity to cross-currency payments and possibly making a profit. (As with any market making opportunity, profits are not guaranteed.)



# Ripple Integration #

## Prior to Ripple Integration ##

Our example exchange, ACME, already accepts withdrawals and deposits from users using some existing system, and uses an internal accounting system to track how much balance each user has with the exchange. Such a system can be modeled simply with a balance sheet and tracking how much currency each user has on hand.

In the following diagram, ACME Exchange starts with €5 on hand, including €1 that belongs to Bob, €2 that belongs to Charlie, and an additional €2 of reserves. Alice deposits €4, so ACME adds her to its balance sheet and ends up with €9.

![Alice sends €4 to ACME. ACME adds her balance to its balance sheet.](img/e2g-01.gif)

**Assumptions:** To integrate with Ripple, we assume that an exchange such as ACME meets the following assumptions:

* ACME already has a system to accept deposits and withdrawals from some outside payment source. 
* ACME waits for deposits to clear before crediting them internally.
* ACME always keeps enough funds on-hand to pay withdrawals on demand, subject to their terms and conditions.
    * ACME can set fees, minimum withdrawals, and delay times for deposits and withdrawals as their business model demands.

## Sending from Gateway to Ripple ##

Sending money into Ripple means moving funds from a user's balance at a gateway into a separate record tracking Ripple-backed funds, and then sending the equivalent amount of issuances in Ripple to the user's Ripple account.

Before the first deposit (once only):

1. ACME publishes its cold wallet address to users.
2. Alice extends a trust line from her Ripple account to ACME's cold wallet, indicating that she is willing to hold ACME's issuances.

An example of a deposit flow:

1. Alice asks to deposit €2 of her ACME balance into Ripple.
2. In its internal accounting, ACME debits Alice's balance €2 and credits the Ripple-backed balance by €2.
3. ACME submits a Ripple transaction, sending €2 to Alice's Ripple address. The €2 is marked in Ripple as being "issued" by ACME (2 EUR@ACME).

![ACME issues 2 EUR@ACME to Alice on Ripple](img/e2g-02.gif)


### Requirements for Sending to Ripple ###

There are several prerequisites that ACME must meet in order for this to happen:

- ACME modifies its core accounting system to track money that is backing funds issued on the Ripple Network. This could be as simple as adding a record for Ripple. 
    - Optionally, a gateway can take additional steps to separate normal user funds from funds backing the gateway's Ripple issuances. For example, a cryptocurrency exchange can create a separate wallet to hold the funds allocated to Ripple. This provides publicly-verifiable proof to customers that the gateway is solvent.
- ACME must have a Ripple account. Our best practices recommend actually having at least two accounts: a "cold wallet" account to issue currency, and one or more "hot wallet" accounts that perform day-to-day transactions. See [Hot and Cold Wallets](#hot-and-cold-wallets) for more information.
- Alice must create a trustline from her Ripple account to ACME's issuing (cold wallet) account. She can do this from any Ripple client (such as [Ripple Trade](https://www.rippletrade.com/) as long as she knows the address or Ripple Name of ACME's cold wallet.
- ACME must create a user interface for Alice to send funds from ACME into Ripple.
    - In order to do this, ACME needs to know Alice's Ripple address. ACME can have Alice input her Ripple addresss as part of the interface, or ACME can require Alice to input and verify her Ripple address in advance.

## Sending from Ripple to Gateway ##

A withdrawal from Ripple means moving funds from the Ripple-backed balance at a gateway into a user account in response to receiving a Ripple payment.

An example of a withdrawal flow:

1. Bob sends Ripple transaction of €1 to ACME's cold wallet
2. In its internal accounting, ACME debits its Ripple-backing balance €1 and credits Bob's balance €1.


### Requirements for Receiving from Ripple ###

In addition to the [requirements for making deposits possible](#deposit-requirements), there are several prerequisites that ACME must meet in order to process payments coming from Ripple:

- ACME must monitor its Ripple accounts for incoming payments.
- ACME must know which user to credit internally for the incoming payments.
    - We recommend that ACME should [bounce any unrecognized incoming payments](#bouncing-payments) back to their sender.
    - Typically, the preferred method of recognizing incoming payments is through [destination tags](#destination-tags).


## Precautions ##

Processing payments to and from Ripple naturally comes with some risks, so a gateway should be sure to take care in implementing these processes. We recommend the following precautions:

- Protect yourself against reversible deposits. Ripple payments are irreversible, but many electronic money systems like credit cards or PayPal are not. Scammers can abuse this to take their fiat money back after receiving Ripple issuances.
- Before processing a payment out of Ripple, make sure you know the customer's identity. This is especially important because the users sending money from Ripple could be different than the ones that initially received the money in Ripple.
- Follow the guidelines for [reliable transaction submission](#reliable-transaction-submission) when sending Ripple transactions.
- [Robustly monitor for incoming payments](#robustly-monitor-for-payments), and read the correct amount. Don't be deceived by Partial Payments.
- Track your obligations and balances within the Ripple network, and compare with your assets off the network. If they do not match up, stop processing withdrawals and deposits until you resolve the discrepancy. (<span class='draft-comment'>TODO: Link to tallying bulletin when it comes out</span>)
- Proactively avoid ambiguous situations. We recommend the following:
    - Enable the [`DisallowXRP` flag](#disallowxrp) for the cold wallet account and all hot wallet accounts, so users do not accidentally send you XRP.
    - Enable the [`RequireDest` flag](#requiredest) for the cold wallet account and all hot wallet accounts, so users do not accidentally forget the destination tag on payments to make withdrawals.
    - Enable the [`RequireAuth` flag](#requireauth) on all hot wallet accounts so they cannot create their own issuances.

## Trading on Ripple ##

After the issuances have been created in Ripple, they can be freely transferred and traded by Ripple users. There are several consequences of this situation:

- Anyone can buy/sell EUR@ACME on Ripple. If ACME issues multiple currencies on Ripple, a separate trust line is necessary for each.
    - This includes users who do not have an account with ACME Exchange. In order to withdraw the funds successfully from ACME, users still have to create ACME accounts.
    - Optionally, use the [Authorized Accounts](#authorized-accounts) feature to limit who can hold EUR@ACME on Ripple.
- Ripple users trading and sending EUR@ACME to one another requires no intervention by ACME.
- All exchanges and balances on Ripple are publicly viewable in the shared, global ledger. 

## Market Makers ##

Exchanging EUR@ACME for other currencies within Ripple requires market makers who are willing to exchange other Ripple issuances for EUR@ACME. Market makers are just Ripple accounts with trust lines for EUR@ACME as well as other currencies or issuers, who create orders (called "offers" in the Ripple ledger) to exchange currency. The cost of exchanging EUR@ACME for another currency depends on the quantity and quality of orders. 

To facilitate exchanging currency, ACME may decide to become its own market maker. For various reasons, we recommend using a separate Ripple account for trading. Because market making can result in financial losses, gateways that choose to act as market makers should not use customer funds for market making.

The following diagram depicts a simple Ripple payment sending 2EUR@ACME from Alice to Charlie. Note that ACME's balance sheet and holdings do not change:

![Alice's sends 2 EUR@ACME from her trust line to Charlie's](img/e2g-03.gif)

## Freezes ##

Ripple provides the ability to freeze assets issued by the gateway in Ripple as a means of complying with regulatory requirements:

* Gateways can freeze individual account issuances, in case a user account shows suspicious activity or violates a gateway's terms of use.
* Gateways can freeze all issuances created by their cold wallet, in case of a compromised gateway account or for migrating cold wallets.
* Furthermore, gateways can permanently opt out of their ability to freeze issuances at all. This allows a gateway to assure its users that it will continue to provide "physical-money-like" services.

For more information, see the [Gateway Bulletin on Freezes](https://ripple.com/files/GB-2014-02.pdf).

## Authorized Accounts ##

Ripple's Authorized Accounts feature enables a gateway to limit who can hold that gateway's issuances, so that unknown Ripple accounts cannot hold the currency your gateway issues. We feel this is *not necessary* in most cases, since gateways have full control over the process of redeeming Ripple balances for value in the outside world. (You can collect customer information and impose limits on withdrawals at that stage without worrying about what happens within the Ripple network.)

To use the Authorized Accounts feature, a gateway first enables the `RequireAuth` flag for its cold wallet account, and then manually approves each user account's trust line before sending issuances in Ripple to that account.

You must authorize trust lines using the same cold wallet account that issues the currency, which unfortunately means an increased risk exposure for that account. The process for sending funds into Ripple with RequireAuth enabled looks like the following:

1. ACME publishes the address of its cold wallet to users.
2. Alice extends a trust line from her Ripple account to ACME's cold wallet, indicating that she is willing to hold ACME's issuances.
3. ACME's cold wallet sends a transaction authorizing Alice's trust line.

See [RequireAuth](#requireauth) for technical details on how to use authorized accounts.



# Technical Details #

## Infrastructure ##

For the gateway's own security as well as the stability of the network, we recommend that each gateway operate its own `rippled` servers, along with any other important infrastructure necessary for the gateway's operation. Ripple Labs provides detailed and individualized recommendations to businesses interested in operating a significant Ripple-based business.

Contact [partners@ripple.com](mailto:partners@ripple.com) to see how Ripple Labs can help.

### APIs and Middleware ###

There are several interfaces you can use to connect to Ripple, depending on your needs and your existing software:

* [`rippled`](rippled-apis.html) provides JSON-RPC and WebSocket APIs that can be used as a low-level interface to all core Ripple functionality.
    * The official client library to rippled, [ripple-lib](https://github.com/ripple/ripple-lib) is available for JavaScript, and provides extended convenience features.
* [Ripple-REST](ripple-rest.html) provides an easy-to-use RESTful API on top of `rippled`. In particular, Ripple-REST is designed to be easier to use from statically-typed languages.
* [Gatewayd](gatewayd.html) provides a pre-configured suite of gateway functionality.


## DisallowXRP ##

The DisallowXRP flag (`disallow_xrp` in Ripple-REST) is designed to discourage users from sending XRP to your account by accident. For accounts that are intended to process withdrawals, receiving XRP is undesirable because there is no way to "withdraw" XRP from the network.

However, the DisallowXRP flag is not strictly enforced, because doing so could allow accounts to become permanently unusable. Client applications should honor it, but it is intentionally possible to work around. We recommend enabling the DisallowXRP flag on all gateway hot and cold wallets.

The following is an example of a Ripple-REST request to enable the DisallowXRP flag:

Request:

```
POST https://api.ripple.com/v1/accounts/rf1BiGeXwwQoi8Z2ueFYTEXSwuJYfV2Jpn/settings?validated=true

{
  "secret": "ssssssssssssssssssssssssssss",
  "settings": {
    "disallow_xrp": true
  }
}
```

Response:

```
200 OK

{
  "success": true,
  "settings": {
    "hash": "AC0F7D7735CDDC6D859D0EC4E96A571F71F7481750F4C6C975FC8075801A6FB5",
    "ledger": "10560577",
    "state": "validated",
    "require_destination_tag": false,
    "require_authorization": false,
    "disallow_xrp": true
  }
}
```

## RequireDest ##

The `RequireDest` flag (`require_destination_tag` in Ripple-REST) is designed to prevent users from sending payments to your account while accidentally forgetting the [destination tag](#destination-tags) that identifies who should be credited for the payment. When enabled, the Ripple Network rejects any payment to your account that does not specify a destination tag.

We recommend enabling the RequireDest flag on all gateway hot and cold wallets.

The following is an example of a Ripple-REST request to enable the RequireDest flag.

Request:

```
POST https://api.ripple.com/v1/accounts/rf1BiGeXwwQoi8Z2ueFYTEXSwuJYfV2Jpn/settings?validated=true

{
  "secret": "ssssssssssssssssssssssssssss",
  "settings": {
    "require_destination_tag": true
  }
}
```

Response:

```
200 OK

{
  "success": true,
  "settings": {
    "hash": "F3D2EE87D597BA50EA3A94027583110925E8BAAFE41511F937D65423B18BC2A3",
    "ledger": "10560755",
    "state": "validated",
    "require_destination_tag": true,
    "require_authorization": false,
    "disallow_xrp": false
  }
}
```


## RequireAuth ##

The `RequireAuth` flag (`require_authorization` in Ripple-REST) prevents a Ripple account's issuances from being held by other users unless the issuer approves them.

We recommend enabling RequireAuth for all hot wallet (and warm wallet) accounts, as a precaution. Separately, the [Authorized Accounts](#authorized-accounts) feature involves setting the RequireAuth flag on your cold wallet.

### With Hot Wallets ###

We recommend enabling `RequireAuth` for all hot wallet accounts, and then never approving any accounts, in order to prevent hot wallets from creating issuances even by accident. This is a purely precuationary measure, and does not impede the ability of those accounts to transfer issuances created by the cold wallet, as they are intended to do.

The following is an example of a Ripple-REST request to enable the RequireDest flag. (This method works the same way regardless of whether the account is used as a hot wallet or cold wallet.)

Request:

```
POST https://api.ripple.com/v1/accounts/rsA2LpzuawewSBQXkiju3YQTMzW13pAAdW/settings?validated=true

{
  "secret": "sssssssssssssssssssssssssssss",
  "settings": {
    "require_authorization": true
  }
}
```

Response:

```
{
  "success": true,
  "settings": {
    "hash": "687702E0C3952E2227B2F7A0B34933EAADD72A572B234D31360AD83D3F193A78",
    "ledger": "10596929",
    "state": "validated",
    "require_destination_tag": false,
    "require_authorization": true,
    "disallow_xrp": false
  }
}
```

### With Cold Wallets ###

You may also enable `RequireAuth` for your cold wallet in order to use the [Authorized Accounts](#authorized-accounts) feature. Enabling the RequireAuth flag for a cold wallet is the same as [with hot wallets](#with-hot-wallets).

If ACME decides to use Authorized Accounts, ACME creates an interface for users to get their Ripple trust lines authorized by ACME's cold account. After Alice has extended a trust line to ACME from her Ripple account, she goes through the interface on ACME's website to require ACME authorize her trust line. ACME confirms that it has validated Alice's identity information, and then sends a TrustSet transaction to authorize Alice's trust line.

The following is an example of using the [Grant Trustline](ripple-rest.html#grant-trustline) method in Ripple-REST to authorize the (customer) account rf1BiGeXwwQoi8Z2ueFYTEXSwuJYfV2Jpn to hold issuances from the (cold wallet) account rsA2LpzuawewSBQXkiju3YQTMzW13pAAdW:

Request:

```
POST https://api.ripple.com/v1/accounts/rsA2LpzuawewSBQXkiju3YQTMzW13pAAdW/trustlines?validated=true
{
  "secret": "sssssssssssssssssssssssss",
  "trustline": {
    "limit": "0",
    "currency": "USD",
    "counterparty": "rf1BiGeXwwQoi8Z2ueFYTEXSwuJYfV2Jpn",
    "authorized": true
  }
}
```

Response:

```
201 Created
{
  "success": true,
  "trustline": {
    "account": "rsA2LpzuawewSBQXkiju3YQTMzW13pAAdW",
    "limit": "0",
    "currency": "USD",
    "counterparty": "rf1BiGeXwwQoi8Z2ueFYTEXSwuJYfV2Jpn",
    "account_allows_rippling": true,
    "account_trustline_frozen": false,
    "authorized": true
  },
  "hash": "4509288EE17F01C83FC7D45850EB066A795EE5DBA17BB4DC98DD4023D31EEE5B",
  "ledger": "11158585",
  "state": "validated"
}
```

<!-- Note: RLJS-154 only affects 1.3.2-rc1 and -rc2 -->

## Robustly Monitoring for Payments ##

In order to robustly monitor incoming payments, gateways should do the following:

* Keep a record of the most-recently-processed transaction. That way, if you temporarily lose connectivity, you know how far to go back.
* Check the result code of every incoming payment. Some payments go into the ledger to charge an anti-spam fee, even though they failed. Only transactions with the result code `tesSUCCESS` can change non-XRP balances. Only transactions from a validated ledger are final.
* Look out for Partial Payments. If an incoming transaction has a `destination_balance_changes` field (Ripple-REST) or a `meta.AmountDelivered` field (WebSocket/JSON-RPC), then use that to see how much money *actually* got delivered to the destination account. Payments with the partial-payment flag enabled are considered "successful" if any non-zero amount is delivered, even miniscule amounts. (The flag is called `"partial_payment": true` in REST, and `tfPartialPayment` in WebSocket/JSON-RPC) 
* Some transactions modify your balances without being payments directly to or from one of your accounts. For example, if ACME sets a nonzero [TransferRate](#transferrate), then ACME's cold wallet's outstanding obligations decrease each time Bob and Charlie exchange ACME issuances. See [TransferRate](#transferrate) for more information. 

To make things simpler for your users, we recommend monitoring for incoming payments to hot wallets and the cold wallet, and treating the two equivalently.

As an added precaution, we recommend regularly comparing the balances of your Ripple cold wallet account with the Ripple-backing funds in your internal accounting system. The cold wallet's shows all outstanding issuances as negative balances, which should be match the positive assets you hold outside the network, backing Ripple. If the two do not match up, then you should check that you have processed all transactions correctly. 

* Use the [Get Account Balances method](ripple-rest.html#get-account-balances) (Ripple-REST) or the [`account_lines` command](rippled-apis.html#account-lines) (rippled) to check your balances.


## Destination Tags ##

*Destination Tags* are 32-bit integers which identify the beneficiary or cause for a payment; for example, which customer should be credited when a Ripple withdrawal takes place. A gateway should maintain an internal mapping of destination tags to (non-Ripple) account records. 

For greater privacy and security, we recommend *not* using monotonically-incrementing numbers as destination tags that correlate 1:1 with users.

Instead, we recommend using convenient internal IDs, but mapping those to destination tags through the use of a quick hash or cipher function such as [Hasty Pudding](http://en.wikipedia.org/wiki/Hasty_Pudding_cipher). You should set aside ranges of internal numbers for different uses of destination tags:

* Direct mappings to user accounts
* Tags for outgoing payments (set the Source Tag of the payment, so that users will bounce it to that Destination Tag)
* Tags for quotes, which expire
* Other disposable destination tags that users can generate.

After passing the internal numbers through your hash function, you can use the result as a destination tag. You should check for collisions just to be safe, and do not reuse destination tags unless they have explicit expiration dates (like quotes and user-generated tags).

We recommend making a user interface to generate a destination tag on-demand when a user intends to make a deposit. This can be deterministic (through iterative uses of a hash function, for example), as long as you check for collisions. Then, consider that destination tag valid only for the expected withdrawal, and bounce any other transactions that use the same destination tag.

### Source Tags ###

When sending a payment from a hot wallet, we also recommend creating a source tag and including it in the payment, so that the receiving Ripple account can bounce the payment back, using the original Source Tag as the Destination Tag of the bounce payment.


## TransferRate ##

The *TransferRate* setting (`transfer_rate` in Ripple-REST) defines a fee to charge for transferring issuances from one Ripple account to another. The transfer fee is set by the issuing (**cold wallet**) account. For any transaction *except paying back to the issuing account*, the sending account is debited issuances at a ratio of TransferRate:1 compared to the destination amount. The transfer fee has a maximum precision of 9 digits, and cannot be less than 0% (a `transfer_rate` of 1.0) or greater than 100% (a `transfer_rate` of 2.0).

The fee represented by the TransferRate is debited from the Ripple ledger, becoming the property of the gateway. 

For example, if ACME sets the trasfer_rate of its cold wallet to 1.005, that indicates a transfer fee of 0.5% for ACME issuances. In order for Bob to receive 2 EUR@ACME, Charlie must send 2.01 EUR@ACME. After the transaction, ACME's outstanding obligations in Ripple have decreased by €0.01, which means that it is no longer obliged to hold that amount in the account backing its Ripple issuances.

The following diagram shows a Ripple payment of 3EUR@ACME from Alice to Charlie with a transfer fee of 1%:

![Alice sends €3.03, Charlie receives €3.00, and ACME holds €0.03 for Ripple](img/e2g-with_transferrate.gif)

The following is an example of a Ripple-REST request to set the TransferRate for a fee of 0.5%.

Request:

```
POST https://api.ripple.com/v1/accounts/rf1BiGeXwwQoi8Z2ueFYTEXSwuJYfV2Jpn/settings?validated=true

{
  "secret": "sssssssssssssssssssssssssssss",
  "settings": {
    "transfer_rate": 1.005
  }
}

```

Response:

```
200 OK

{
  "success": true,
  "settings": {
    "transfer_rate": 1.005,
    "require_destination_tag": false,
    "require_authorization": false,
    "disallow_xrp": false
  },
  "hash": "4D098C181DE0A21A55ACBD362E5ADBF24EA2493BD4E56F2137DBAF113327AB4E",
  "ledger": "11158720",
  "state": "validated"
}
```

All Ripple Accounts, including the hot wallet, are subject to the TransferRate. If you set a nonzero TransferRate, then you must send extra (to pay the TransferRate) when making payments to users from your hot wallet. You can accomplish this by setting the `source_amount` (Ripple-REST) or the `SendMax` (rippled) parameters higher than the destination amount.

*Note:* The TransferRate does not apply when sending issuances back to the account that created them. The account that created issuances must always accept them at face value on Ripple. This means that users don't have to pay the TransferRate if they send payments to the cold wallet directly, but they do when sending to the hot wallet. (For example, if ACME sets a TransferRate of 1%, a Ripple payment with `source_amount` and `destination_amount` of 5 USD@ACME (and `slippage` of 0) would succeed if sent to ACME's cold wallet, but it would fail if sent to ACME's hot wallet. The hot wallet payment would only succeed if the `source_amount` plus `slippage` was at least 5.05 USD@ACME.) If you accept payments to both accounts, you may want to adjust the amount you credit users in your external system accordingly. 


## Bouncing Payments ##

When your hot or cold wallet receives a payment whose purpose is unclear, we recommend that you make an attempt to return the money to its sender. While this is more work than simply pocketing the money, it demonstrates good faith towards customers.

The first requirement to bouncing payments is [robustly monitoring for incoming payments](#robustly-monitoring-for-payments). You do not want to accidentally refund a user for more than they sent you!

Second, you should send bounced payments as Partial Payments. Since other Ripple users can manipulate the cost of pathways between your accounts, Partial Payments allow you to divest yourself of the full amount without being concerned about how much you might have to pay in fees.

To send a Partial Payment in Ripple-REST, set the `partial_payment` field to true in the object returned by the [Prepare Payment method](ripple-rest.html#prepare-payment) before submitting it. Set the `source_amount` to be equal to the `destination_amount` and the `slippage` to `"0"`.

Third, it is conventional that you take the Source Tag from the incoming payment (`source_tag` in Ripple-REST) and use that value as the Destination Tag (`destination_tag` in Ripple-REST) for the return payment. 

To prevent two systems from bouncing payments back and forth indefinitely, you can set a new Source Tag for the outgoing return payment. If you receive an unexpected payment whose Destination Tag matches the Source Tag of a return you sent, then do not bounce it back again. 

The following is an example of a return payment:

```
POST /v1/accounts/{address}/payments?validated=true

{
  "secret": "sssssssssssssssssssssssssssss",
  "client_resource_id": "fc521224-bdd8-4463-94a4-b26cb760fc92",
  "last_ledger_sequence": "10968788",
  "max_fee": "1.0",
  "payment": {
    "source_account": "rBEXjfD3MuXKATePRwrk4AqgqzuD9JjQqv",
    "source_tag": "479686",
    "source_amount": {
      "value": "2",
      "currency": "EUR",
      "issuer": ""
    },
    "source_slippage": "0",
    "destination_account": "r9cZA1mLK5R5Am25ArfXFmqgNwjZgnfk59",
    "destination_tag": "803489",
    "destination_amount": {
      "value": "2",
      "currency": "EUR",
      "issuer": ""
    },
    "invoice_id": "",
    "paths": "[[{\"account\":\"rvYAfWj5gh67oV6fW32ZzP3Aw4Eubs59B\",\"type\":1,\"type_hex\":\"0000000000000001\"}]]",
    "partial_payment": true,
    "no_direct_ripple": false
  }
}
```


## Setting Trust Lines in Ripple Trade ##

Follow these steps to extend a trust line to a Gateway's issuing (cold wallet) account in the Ripple Trade client.

1. Log in and go to the **Fund** tab:
    ![Fund tab](img/connectgateway_01.png)
2. Click **Gateways** in the sidebar:
    ![Gateways](img/connectgateway_02.png)
3. Enter the Ripple Name or Ripple Address of the Gateway's **cold wallet**, and click **Save**.
    ![Enter gateway's name or address, then save](img/connectgateway_03.png)
4. Enter the Ripple Trade password, and click **Submit**. (This allows access to send a transaction to the Ripple Network to create the trust line.)
    ![Enter password and submit](img/connectgateway_04.png)
5. When the page shows a green "Gateway connected" box, the transaction to create the trust line has succeeded and the Ripple Network has validated it.
    ![Gateway connected](img/connectgateway_05.png)
    

## Reliable Transaction Submission ##

The goal of reliably submitting transactions is to achieve the following two properties in a finite amount of time:

* Idempotency - Transactions will be processed once and only once, or not at all.
* Verifiability - Applications can determine the final result of a transaction.

In order to achieve this, there are several steps you can take when submitting transactions:

* Persist details of the transaction before submitting it.
* Use the `LastLedgerSequence` parameter. (Ripple-REST and ripple-lib do this by default.)
* Resubmit a transaction if it has not appeared in a validated ledger whose sequence number is less than or equal to the transaction's `LastLedgerSequence` parameter.

For additional information, consult the guide to [Reliable Transaction Submission](reliable_tx.html)

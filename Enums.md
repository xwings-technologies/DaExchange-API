# Enums

## orderStatus

Order Status             | Description
-------------------------| ---------------------------------------
PENDING_NEW              | New order has been accepted
NEW                      | New order has been booked
PARTIAL_FILLED           | Order is partially filled
FILLED                   | Order is fully filled
PENDING_CANCEL           | Order cancel request has been accepted
CANCELLED                | Order has been cancelled and removed from book

## timeInForce
Time in Force            | Description
-------------------------| ---------------------------------------
GTC                      | Good till cancelled orders remain in the book until cancelled or filled.
IOC                      | Immediate or cancel orders must be executed instantly and any unfilled parts of the order are cancelled.
FOK                      | Fill or kill orders are rejected if the entire size can not be matched.


## side
Side                     | Description
-------------------------| --------------------------------------
BUY                      | Buy order indicator
SELL                     | Sell order indicator


## selfTradePrevention
Self Trade Prevention    | Description
-------------------------| --------------------------------------
CO                       | Cancel older order in the book
CN                       | Cancel new order
CB                       | Cancel both orders


## orderType
Order Type               | Description
-------------------------| -------------------------------------
LIMIT                    | Limit orders require specifying a price and size
MARKET                   | Market orders provide no pricing guarantees. They execute immediatly and no part of the market order will go on the orer book.
STOP_LOSS (TBA)          | A market order is placed when the last price moves to the value at or below the stop price.  The trade may happen at the worse price than stop price.
STOP_LOSS_LIMIT (TBA)    | A limit order is placed when the last price moves to the value at or below the stop price.
STOP_ENTRY (TBA)         | A market order is placed when the last price moves to the value at or above the stop price. The trade may happen at the worse price than stop price.
STOP_ENTRY_LIMIT (TBA)   | A limit order is placed when the last price moves to the value at or above the stop price.


## instrumentType
Instrument Type          | Description
-------------------------| --------------------------------------
SPOT                     | 
FUTURES (TBA)            |


## cancelReason
Order Cancel Reason                    | Description
---------------------------------------| -------------------------------------------------------------------------
USER_CANCEL                            | The order is cancelled by user.
NO_LIQUIDITY                           | Market order or IOC order cancelled remaining by system.
SELF_TRADE                             | The order is cancelled due to self trade prevention.
POST_ONLY                              | The post only order is taking liquidity, cancelled by system.
INSUFFICIENT_LIQUIDITY                 | The FOK order cannot fully trade, cancelled by system.
TOTAL_EXECUTED_SIZE_MORE_THAN_MAX_SIZE | The MARKET BUY order executed more than maxOrderSize, cancelled by system.
INSUFFICIENT_QUOTE_AMOUNT              | The MARKET BUY order quoteAmount too small, cancelled by system.
INACTIVE_INSTRUMENT                    | The instrument status is INACTIVE, cancelled by system.
EXCEED_BALANCE                         | The MARKET order exceed balance, cancelled by system.


## updateReason
Account Update Reason                  | Description
---------------------------------------| -----------------------------------------------------------
NEW_ORDER                              | The account update that is triggered by new order.
PENDING_WITHDRAW                       | The account update that is triggered by pending withdraw.
TRADE                                  | The account update that is triggered by trade.
TRANSFER                               | The account update that is triggered by completed transfer.


## transactionType
Transaction Type                       | Description
---------------------------------------| --------------------------------------------------------
TRADE                                  | The account transaction entry triggered by TRADE.
TRANSFER                               | The account transaction entry triggered by TRANSFER.
TRADE_FEE                              | The account transaction entry triggered by TRADE_FEE.
TRANSFER_FEE                           | The account transaction entry triggered by TRANSFER_FEE.


## apikeyAuthority
Apikey Authority                       | Description
---------------------------------------| --------------------------------------------------------
ACCOUNT_VIEW                           | The authority of apikey for accounts read related url access.
TRADE_VIEW                             | The authority of apikey for trades read related url access.
TRADE                                  | The authority of apikey for trades related url access.
WITHDRAW                               | The authority of apikey for withdraw url access.

## twoFactorAuthorization
Two Factor Authorization               | Description
---------------------------------------| --------------------------------------------------------
LOGIN                                  | The login url that need two factor code authentication
UPDATE_PROFILE                         | The update profile url that need two factor code authentication
TRADE                                  | The trade realted urls that need two factor code authentication
TRANSFER                               | The transfer related urls that need two factor code authentication

## loggedOutReason
Logged Out Reason                      | Description
---------------------------------------| --------------------------------------------------------
NORMAL_LOGOUT                          | User initiates the logout
NEW_SESSION_INIT                       | User starts a new login session
USER_DISABLED                          | User is disabled
SYSTEM_LOGOUT                          | System logs out the user
RESET_PASSWORD                         | User is logged out due to password reset

## withdrawalStatus
Withdrawal Status                      | Description
---------------------------------------| -------------------------------------------------------
PENDING                                | The initial withdrawal request status
IN_PROGRESS                            | Withdrawal request is being processed
UNCONFIRMED                            | Coin withdrawal request has been broadcast to network, but is not confirmed
COMPLETED                              | Coin withdrawal request has been confirmed
CANCELLED                              | Withdrawal request has been cancelled

## dataSource
Data Source                            | Description
---------------------------------------| -------------------------------------------------------
CONSOLIDATED                           | Consolidated data
COINBASE_PRO                           | Coinbase pro exchange data
BITSTAMP                               | Bitstamp exchange data
BITFINEX                               | Bitfinex exchange data
GEMINI                                 | Gemini exchange data
KRAKEN                                 | Kraken exchange data
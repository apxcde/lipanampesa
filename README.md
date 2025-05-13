# Lipa Na Mpesa Node Package.

```js
const app = require("express")();
const Mpesa = require("lipanampesa");

// create an instance
// You can have multiple instances of this e.g for production and development
const MpesaApi = new Mpesa({
  consumerKey: "<your consumer key >",
  consumerSecret: "<your consumer secret >",
  environment: "<production or sandbox>",
  shortCode: "< your business shortCode>",
  lipaNaMpesaShortCode: "< your head office number >",
  lipaNaMpesaShortPass: "<your online passKey>"
});

app.get("/test/pay", (req, res) => {
  const senderMsisdn = 2547051234567; // customer phone number
  const amount = 1000; // amount to be paid
  const callbackUrl = ""; // webhook receiveing from safaricom, callbackurl
  const accountRef = ""; // Account Ref
  const TransactionType = ""; // "CustomerBuyGoodsOnline" for till and "CustomerPayBillOnline" for paybill

  MpesaApi.lipaNaMpesaOnline(
    senderMsisdn,
    amount,
    callbackUrl,
    accountRef,
    TransactionType
  )
    .then(res => console.log(res))
    .catch(err => console.error(err));
});
```

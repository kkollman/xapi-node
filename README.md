# xapi-node

This package is make possible to get data from market, execute order or limit orders with NodeJS through WebSocket connection

It can be used for [X-Trade Brokers](https://www.xtb.com/en) xStation5 accounts

WebSocket communication documentation: http://developers.xstore.pro/documentation/

This is only source code, more details will be released later.

### Example usage
```ts
const x = new XAPI("(xStation5) accountID", "(xStation5) password", "real");

x.connect();

x.Socket.listen.getTradesHistory((history, time, transaction) => {
	console.log(history[0]);
	console.log(history.length);
});

x.onReady(() => {
	x.Socket.send.getTickPrices(["EURUSD"]).then((resolve) => {
		const { returnData, time, transaction } = resolve;
		console.log(returnData.quotations[0]);
	});

	x.Socket.send.getTradesHistory(1,0);
});
```
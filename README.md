* 1inch swap api
# Features
* Support v5 version.
* Full API coverage.
* Typescript support.
* Fully covered with annotations and comments.
***
# Installing
Using npm:
```console
npm i @normalizex/1inch-api-swap
```
Using yarn:
```console
yarn add @normalizex/1inch-api-swap
```
Using jsDelivr CDN:
```html
<script src="https://cdn.jsdelivr.net/npm/@normalizex/1inch-api-swap/dist/index.browser.min.js"></script>
```
Using unpkg CDN:
```html
<script src="https://unpkg.com/@normalizex/1inch-api-swap/dist/index.browser.min.js"></script>
```
***
# Documentation
* You can find full documentation in 1inch dev portal: [docs](https://portal.1inch.dev/documentation/swap/swagger) 
***
# Usage:
```js
import { InchV5Swap, InchV5Chains } from '@normalizex/1inch-api-swap';
const Inch = new InchV5Swap(InchV5Chains.Ethereum);
```
# Example
```js
import { InchV5Chains } from "@normalizex/1inch-api-swap";

const Inch = new InchV5Swap(InchV5Chains.Ethereum);

const BUSD = '0xe9e7cea3dedca5984780bafc599bd69add087d56';
const WETH = '0xeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee';
const WalletAddress = '0x35552CF3Ce8Cc8a0f7fdC8Aa88a89b92e9Ab5FdB';

// EXAMPLES
inch.chain();// return 1
inch.swithChain(InchV5Chains.BinanceSmartChain);
inch.chain();// return 56

Inch.allowance(BUSD, WalletAddress).then(data => {
	//return "0"
});

Inch.approveSpender().then(data => {
	//0x1111111254fb6c44bac0bed2854e76f90643097d
});

Inch.approveTransaction(BUSD).then(data => {
	/**
		{
			data: '0x095ea7b30000000000000000000000001111111254fb6c44bac0bed2854e76f90643097dffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff',
			gasPrice: '15000000000',
			to: '0xe9e7cea3dedca5984780bafc599bd69add087d56',
			value: '0'
		}
	*/
});

Inch.healtcheck().then(data => {
	// { status: 'OK' }
});

Inch.liquiditySources().then(data => {
	/**
		[
			{
				id: 'BSC_BI_SWAP',
				title: 'biswap',
				img: 'https://cdn.1inch.io/liquidity-sources-logo/biswap.png',
				img_color: 'https://cdn.1inch.io/liquidity-sources-logo/biswap_color.png'
			}
			...AND MORE ITEMS...
		]
	*/
});

Inch.presets().then(data => {
	/**
		{
			MAX_RESULT: [
				{
					complexityLevel: 2,
					mainRouteParts: 10,
					parts: 50,
					virtualParts: 50
				}
			],
			LOWEST_GAS: [
				{
					complexityLevel: 0,
					mainRouteParts: 1,
					parts: 1,
					virtualParts: 1
				},
				{
					complexityLevel: 1,
					mainRouteParts: 1,
					parts: 1,
					virtualParts: 1
				}
			]
		}
	*/
});

Inch.tokens().then(data => {
	/**
	 [
		{
			symbol: 'DOS',
			name: 'DOS Network Token BEP20',
			decimals: 18,
			address: '0xdc0f0a5719c39764b011edd02811bd228296887c',
			logoURI: 'https://tokens.1inch.io/0x0a913bead80f321e7ac35285ee10d9d922659cb7.png'
		},
		... 284 more items
	 ] 
	*/
});

Inch.quote(BUSD, WETH, 50 * 1e18).then(data => {
	/** 
	{
		fromToken: {
			symbol: 'BUSD',
			name: 'BUSD Token',
			decimals: 18,
			address: '0xe9e7cea3dedca5984780bafc599bd69add087d56',
			logoURI: 'https://tokens.1inch.io/0x4fabb145d64652a948d72533023f6e7a623c7c53.png'
		},
		toToken: {
			symbol: 'BNB',
			name: 'BNB',
			decimals: 18,
			address: '0xeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee',
			logoURI: 'https://tokens.1inch.io/0xbb4cdb9cbd36b01bd1cbaebf2de08d9173bc095c_1.png'
		},
		toTokenAmount: '125276691940480656',
		fromTokenAmount: '50000000000000000000',
		protocols: [ [ [Array] ] ],
		estimatedGas: 252364
	}
	*/
});
```
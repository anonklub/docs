[query.anonklub.xyz](https://www.query.anonklub.xyz) provides endpoints to fetch on chain "**anonymity sets**".\
It reads public ethereum data already indexed by different services ([dune](https://dune.com/), [the graph](https://thegraph.com/), google bigquery's `crypto_ethereum` dataset) to aggregate lists of addresses that match different requirements.

For instance, you can get the list of addresses that own at least **3000** of the **ENS** ERC20 with address **`0xc18360217d8f7ab5e7c516566761ea12ce7f9d72`** as of the latest block:\
[`GET www.query.anonklub.xyz/asset/ERC20?tokenAddress=0xc18360217d8f7ab5e7c516566761ea12ce7f9d72&min=3000`](https://www.query.anonklub.xyz/asset/ERC20?tokenAddress=0xc18360217d8f7ab5e7c516566761ea12ce7f9d72&min=3000)

```javascript
const tokenAddress = '0xc18360217d8f7ab5e7c516566761ea12ce7f9d72';
const min = 3000;
const ANON_SET_API = 'https://www.query.anonklub.xyz';

const params = new URLSearchParams({ min, tokenAddress });

const addresses = await fetch(
  `${ANON_SET_API}/asset/ERC20?${params.toString()}`,
).then((res) => res.json());
```

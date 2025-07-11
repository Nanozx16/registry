# registry

Installation
With Node.js Installed:

yarn install eth-method-registry -S

Usage
const { MethodRegistry } = require('eth-method-registry')
const Eth = require('@metamask/ethjs')

const provider = new Eth.HttpProvider('https://mainnet.infura.io/v3/YOUR-PROJECT-ID')
const registry = new MethodRegistry({ provider })

// Uses promises, pass the 4byte prefix to the lookup method:
registry.lookup('0xa9059cbb')
  .then((result) => {
   console.log(result) // prints 'transfer(address,uint256)'
  })

// Also includes a method for parsing the resulting sig
// into something more useful for rendering:
const sig = 'transferFrom(address,uint256)'
const parsed = registry.parse(sig)
/* Parsed value:
   {
    name :'Transfer From',
    args: [
      { type: 'address' },
      { type: 'uint256' }
    ]
   }
*/
Development
The unit tests of this package run against Infura's v3 API. After cloning this repository, run cp .infurarc.template .infurarc and add your Infura project ID to the file.

Running Tests
yarn test

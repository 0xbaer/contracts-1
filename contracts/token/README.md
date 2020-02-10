# Token

This is an Ethereum project that enhances some of the popular implementations of token standards.

## IERC20Mintable

It is an interface that adds to the `IERC20` interface the `mint` function from the `ERC20Mintable` OpenZeppelin contract.


## IERC20Detailed

It is an interface that adds to the `IERC20` interface the `name`, `symbol` and `decimals` functions from the `ERC20Detailed` OpenZeppelin contract.


## IERC20MintableDetailed

It is an interface that adds to the `IERC20` interface the `mint`, `name`, `symbol` and `decimals` functions from the `ERC20Mintable` and `ERC20Detailed` OpenZeppelin contracts.

## ERC20MintableDetailed

It is a contract that implements the `IERC20MintableDetailed` interface.

## ERC20DividendableEth

It is a `ERC20` token contract that is endowed with some rather dividendable qualities. 

1. Anyone can send `ether` to the contract at any time using `increasePool`. That amount of `ether` will be added to a dividend pool.

2. Any token holder can draw their fair share of `ether` from the dividend pool according to the amount of tokens they hold. To do this they must call the `updateAccount` function.

#### Notes 
1. Changes in the token supply will affect any dividend distribution events. Any ongoing distribution events for which the contract has received the `ether` before the total supply change are unaffected.

2. In order to be useful in practice, the contract has to be customized by inheriting from a mintable standard implementation, for example, openzeppelin's `ERC20Mintable` contract, in this way:

```
contract MyERC20DividendableEth is ERC20DividendableEth, ERC20Mintable {
    // here goes your fantasy
}
```

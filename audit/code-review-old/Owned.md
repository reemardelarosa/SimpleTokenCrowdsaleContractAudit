# Ownable

Source file [../../contracts/Owned.sol](../../contracts/Owned.sol).

<br />

<hr />

```javascript
// BK Ok
pragma solidity ^0.4.15;


/**
 * @title Ownable
 * @dev The Ownable contract has an owner address, and provides basic authorization control
 * functions, this simplifies the implementation of "user permissions".
 */
// BK Ok
contract Ownable {
  // BK Ok
  address public owner;


  // BK Ok - Event
  event OwnershipTransferred(address indexed previousOwner, address indexed newOwner);


  /**
   * @dev The Ownable constructor sets the original `owner` of the contract to the sender
   * account.
   */
  // BK Ok - Constructor
  function Ownable() {
    // BK Ok
    owner = msg.sender;
  }


  /**
   * @dev Throws if called by any account other than the owner.
   */
  // BK Ok
  modifier onlyOwner() {
    // BK Ok
    require(msg.sender == owner);
    // BK Ok
    _;
  }


  /**
   * @dev Allows the current owner to transfer control of the contract to a newOwner.
   * @param newOwner The address to transfer ownership to.
   */
  // BK Ok - Only owner can execute
  function transferOwnership(address newOwner) onlyOwner {
    // BK Ok
    require(newOwner != address(0));      
    // BK Ok - Log event
    OwnershipTransferred(owner, newOwner);
    // BK Ok
    owner = newOwner;
  }

}

```

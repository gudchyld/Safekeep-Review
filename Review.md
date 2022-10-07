## SafeKeep VaultSpawnerFacet

Vaults are smart contracts that help users find the best yield on their crypto tokens through the execution of different strategies. These vaults can accept various token protocols whether fungible or non-fungible as designed.

In the Context of Safekeep, the safekeep vault is a form of onchain will where user can store assets such as ERC20, ERC721 and ERC1155 variants. Safekeep utilizes a register of inheritors that can become beneficiaries in the situation where a user passes on.

The Safekeep VaultSpawnerFacet is a factory for the safekeep vault that simply deploys safekeep vaults

##### Line 1

`pragma solidity 0.8.4`
This defines the version of compiler to use for this project

##### Line 3-9

```
import "../../Vault/VaultDiamond.sol";
import "../libraries/LibAppStorage.sol";
import "../../Vault/libraries/LibKeep.sol";
import "../../interfaces/IVaultDiamond.sol";

import "../../interfaces/IDiamondCut.sol";
import "../../interfaces/IVaultFacet.sol";
```

This defines imports of libraries, interfaces, storage, and the VaultDiamond to be used in this contract

##### Line 11

```
contract VaultSpawnerFacet is StorageLayout {
```

The contract keyword defines a contract VaultSpawnerFacet which inherits from an abstract contract called StorageLayout that declares a pointer to a FactoryAppStorage which is a container that houses the variables to be used in this contract

##### Line 12

```
event VaultCreated(
    address indexed owner,
    address indexed backup,
    uint256 indexed startingBalance,
    uint256 vaultID
  );
```

This declares an event to be emitted when a new vault is created, emitting the owner of the vaults address, his backup address, his starting balance and the id of the created vault

##### Line 19

```
error BackupAddressError()
```

This defines a custom error message BackupAddressError()

##### Line 21

```
  function createVault(
    address[] calldata _inheritors,
    uint256[] calldata _weiShare,
    uint256 _startingBal,
    address _backupAddress
  ) external payable returns (address addr) {
```

The

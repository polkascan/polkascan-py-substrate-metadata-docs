
# Assets

---------
## Calls

---------
### approve_transfer
Approve an amount of asset for transfer by a delegated third-party account.

Origin must be Signed.

Ensures that `ApprovalDeposit` worth of `Currency` is reserved from signing account
for the purpose of holding the approval. If some non-zero amount of assets is already
approved from signing account to `delegate`, then it is topped up or unreserved to
meet the right value.

NOTE: The signing account does not need to own `amount` of assets at the point of
making this call.

- `id`: The identifier of the asset.
- `delegate`: The account to delegate permission to transfer asset.
- `amount`: The amount of asset that may be transferred by `delegate`. If there is
already an approval in place, then this acts additively.

Emits `ApprovedTransfer` on success.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| delegate | `AccountIdLookupOf<T>` | 
| amount | `T::Balance` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'approve_transfer', {
    'amount': 'u128',
    'delegate': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'id': 'u128',
}
)
```

---------
### block
Disallow further unprivileged transfers of an asset `id` to and from an account `who`.

Origin must be Signed and the sender should be the Freezer of the asset `id`.

- `id`: The identifier of the account&\#x27;s asset.
- `who`: The account to be unblocked.

Emits `Blocked`.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| who | `AccountIdLookupOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'block', {
    'id': 'u128',
    'who': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### burn
Reduce the balance of `who` by as much as possible up to `amount` assets of `id`.

Origin must be Signed and the sender should be the Manager of the asset `id`.

Bails with `NoAccount` if the `who` is already dead.

- `id`: The identifier of the asset to have some amount burned.
- `who`: The account to be debited from.
- `amount`: The maximum amount by which `who`&\#x27;s balance should be reduced.

Emits `Burned` with the actual amount burned. If this takes the balance to below the
minimum for the asset, then the amount burned is increased to take it to zero.

Weight: `O(1)`
Modes: Post-existence of `who`; Pre &amp; post Zombie-status of `who`.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| who | `AccountIdLookupOf<T>` | 
| amount | `T::Balance` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'burn', {
    'amount': 'u128',
    'id': 'u128',
    'who': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### cancel_approval
Cancel all of some asset approved for delegated transfer by a third-party account.

Origin must be Signed and there must be an approval in place between signer and
`delegate`.

Unreserves any deposit previously reserved by `approve_transfer` for the approval.

- `id`: The identifier of the asset.
- `delegate`: The account delegated permission to transfer asset.

Emits `ApprovalCancelled` on success.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| delegate | `AccountIdLookupOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'cancel_approval', {
    'delegate': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'id': 'u128',
}
)
```

---------
### clear_metadata
Clear the metadata for an asset.

Origin must be Signed and the sender should be the Owner of the asset `id`.

Any deposit is freed for the asset owner.

- `id`: The identifier of the asset to clear.

Emits `MetadataCleared`.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'clear_metadata', {'id': 'u128'}
)
```

---------
### create
Issue a new class of fungible assets from a public origin.

This new asset class has no assets initially and its owner is the origin.

The origin must conform to the configured `CreateOrigin` and have sufficient funds free.

Funds of sender are reserved by `AssetDeposit`.

Parameters:
- `id`: The identifier of the new asset. This must not be currently in use to identify
an existing asset.
- `admin`: The admin of this class of assets. The admin is the initial address of each
member of the asset class&\#x27;s admin team.
- `min_balance`: The minimum balance of this new asset that any single account must
have. If an account&\#x27;s balance is reduced below this, then it collapses to zero.

Emits `Created` event when successful.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| admin | `AccountIdLookupOf<T>` | 
| min_balance | `T::Balance` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'create', {
    'admin': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'id': 'u128',
    'min_balance': 'u128',
}
)
```

---------
### destroy_accounts
Destroy all accounts associated with a given asset.

`destroy_accounts` should only be called after `start_destroy` has been called, and the
asset is in a `Destroying` state.

Due to weight restrictions, this function may need to be called multiple times to fully
destroy all accounts. It will destroy `RemoveItemsLimit` accounts at a time.

- `id`: The identifier of the asset to be destroyed. This must identify an existing
  asset.

Each call emits the `Event::DestroyedAccounts` event.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'destroy_accounts', {'id': 'u128'}
)
```

---------
### destroy_approvals
Destroy all approvals associated with a given asset up to the max (T::RemoveItemsLimit).

`destroy_approvals` should only be called after `start_destroy` has been called, and the
asset is in a `Destroying` state.

Due to weight restrictions, this function may need to be called multiple times to fully
destroy all approvals. It will destroy `RemoveItemsLimit` approvals at a time.

- `id`: The identifier of the asset to be destroyed. This must identify an existing
  asset.

Each call emits the `Event::DestroyedApprovals` event.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'destroy_approvals', {'id': 'u128'}
)
```

---------
### finish_destroy
Complete destroying asset and unreserve currency.

`finish_destroy` should only be called after `start_destroy` has been called, and the
asset is in a `Destroying` state. All accounts or approvals should be destroyed before
hand.

- `id`: The identifier of the asset to be destroyed. This must identify an existing
  asset.

Each successful call emits the `Event::Destroyed` event.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'finish_destroy', {'id': 'u128'}
)
```

---------
### force_asset_status
Alter the attributes of a given asset.

Origin must be `ForceOrigin`.

- `id`: The identifier of the asset.
- `owner`: The new Owner of this asset.
- `issuer`: The new Issuer of this asset.
- `admin`: The new Admin of this asset.
- `freezer`: The new Freezer of this asset.
- `min_balance`: The minimum balance of this new asset that any single account must
have. If an account&\#x27;s balance is reduced below this, then it collapses to zero.
- `is_sufficient`: Whether a non-zero balance of this asset is deposit of sufficient
value to account for the state bloat associated with its balance storage. If set to
`true`, then non-zero balances may be stored without a `consumer` reference (and thus
an ED in the Balances pallet or whatever else is used to control user-account state
growth).
- `is_frozen`: Whether this asset class is frozen except for permissioned/admin
instructions.

Emits `AssetStatusChanged` with the identity of the asset.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| owner | `AccountIdLookupOf<T>` | 
| issuer | `AccountIdLookupOf<T>` | 
| admin | `AccountIdLookupOf<T>` | 
| freezer | `AccountIdLookupOf<T>` | 
| min_balance | `T::Balance` | 
| is_sufficient | `bool` | 
| is_frozen | `bool` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'force_asset_status', {
    'admin': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'freezer': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'id': 'u128',
    'is_frozen': 'bool',
    'is_sufficient': 'bool',
    'issuer': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'min_balance': 'u128',
    'owner': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### force_cancel_approval
Cancel all of some asset approved for delegated transfer by a third-party account.

Origin must be either ForceOrigin or Signed origin with the signer being the Admin
account of the asset `id`.

Unreserves any deposit previously reserved by `approve_transfer` for the approval.

- `id`: The identifier of the asset.
- `delegate`: The account delegated permission to transfer asset.

Emits `ApprovalCancelled` on success.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| owner | `AccountIdLookupOf<T>` | 
| delegate | `AccountIdLookupOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'force_cancel_approval', {
    'delegate': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'id': 'u128',
    'owner': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### force_clear_metadata
Clear the metadata for an asset.

Origin must be ForceOrigin.

Any deposit is returned.

- `id`: The identifier of the asset to clear.

Emits `MetadataCleared`.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'force_clear_metadata', {'id': 'u128'}
)
```

---------
### force_create
Issue a new class of fungible assets from a privileged origin.

This new asset class has no assets initially.

The origin must conform to `ForceOrigin`.

Unlike `create`, no funds are reserved.

- `id`: The identifier of the new asset. This must not be currently in use to identify
an existing asset.
- `owner`: The owner of this class of assets. The owner has full superuser permissions
over this asset, but may later change and configure the permissions using
`transfer_ownership` and `set_team`.
- `min_balance`: The minimum balance of this new asset that any single account must
have. If an account&\#x27;s balance is reduced below this, then it collapses to zero.

Emits `ForceCreated` event when successful.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| owner | `AccountIdLookupOf<T>` | 
| is_sufficient | `bool` | 
| min_balance | `T::Balance` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'force_create', {
    'id': 'u128',
    'is_sufficient': 'bool',
    'min_balance': 'u128',
    'owner': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### force_set_metadata
Force the metadata for an asset to some value.

Origin must be ForceOrigin.

Any deposit is left alone.

- `id`: The identifier of the asset to update.
- `name`: The user friendly name of this asset. Limited in length by `StringLimit`.
- `symbol`: The exchange symbol for this asset. Limited in length by `StringLimit`.
- `decimals`: The number of decimals this asset uses to represent one unit.

Emits `MetadataSet`.

Weight: `O(N + S)` where N and S are the length of the name and symbol respectively.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| name | `Vec<u8>` | 
| symbol | `Vec<u8>` | 
| decimals | `u8` | 
| is_frozen | `bool` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'force_set_metadata', {
    'decimals': 'u8',
    'id': 'u128',
    'is_frozen': 'bool',
    'name': 'Bytes',
    'symbol': 'Bytes',
}
)
```

---------
### force_transfer
Move some assets from one account to another.

Origin must be Signed and the sender should be the Admin of the asset `id`.

- `id`: The identifier of the asset to have some amount transferred.
- `source`: The account to be debited.
- `dest`: The account to be credited.
- `amount`: The amount by which the `source`&\#x27;s balance of assets should be reduced and
`dest`&\#x27;s balance increased. The amount actually transferred may be slightly greater in
the case that the transfer would otherwise take the `source` balance above zero but
below the minimum balance. Must be greater than zero.

Emits `Transferred` with the actual amount transferred. If this takes the source balance
to below the minimum for the asset, then the amount transferred is increased to take it
to zero.

Weight: `O(1)`
Modes: Pre-existence of `dest`; Post-existence of `source`; Account pre-existence of
`dest`.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| source | `AccountIdLookupOf<T>` | 
| dest | `AccountIdLookupOf<T>` | 
| amount | `T::Balance` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'force_transfer', {
    'amount': 'u128',
    'dest': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'id': 'u128',
    'source': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### freeze
Disallow further unprivileged transfers of an asset `id` from an account `who`. `who`
must already exist as an entry in `Account`s of the asset. If you want to freeze an
account that does not have an entry, use `touch_other` first.

Origin must be Signed and the sender should be the Freezer of the asset `id`.

- `id`: The identifier of the asset to be frozen.
- `who`: The account to be frozen.

Emits `Frozen`.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| who | `AccountIdLookupOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'freeze', {
    'id': 'u128',
    'who': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### freeze_asset
Disallow further unprivileged transfers for the asset class.

Origin must be Signed and the sender should be the Freezer of the asset `id`.

- `id`: The identifier of the asset to be frozen.

Emits `Frozen`.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'freeze_asset', {'id': 'u128'}
)
```

---------
### mint
Mint assets of a particular class.

The origin must be Signed and the sender must be the Issuer of the asset `id`.

- `id`: The identifier of the asset to have some amount minted.
- `beneficiary`: The account to be credited with the minted assets.
- `amount`: The amount of the asset to be minted.

Emits `Issued` event when successful.

Weight: `O(1)`
Modes: Pre-existing balance of `beneficiary`; Account pre-existence of `beneficiary`.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| beneficiary | `AccountIdLookupOf<T>` | 
| amount | `T::Balance` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'mint', {
    'amount': 'u128',
    'beneficiary': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'id': 'u128',
}
)
```

---------
### refund
Return the deposit (if any) of an asset account or a consumer reference (if any) of an
account.

The origin must be Signed.

- `id`: The identifier of the asset for which the caller would like the deposit
  refunded.
- `allow_burn`: If `true` then assets may be destroyed in order to complete the refund.

Emits `Refunded` event when successful.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| allow_burn | `bool` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'refund', {'allow_burn': 'bool', 'id': 'u128'}
)
```

---------
### refund_other
Return the deposit (if any) of a target asset account. Useful if you are the depositor.

The origin must be Signed and either the account owner, depositor, or asset `Admin`. In
order to burn a non-zero balance of the asset, the caller must be the account and should
use `refund`.

- `id`: The identifier of the asset for the account holding a deposit.
- `who`: The account to refund.

Emits `Refunded` event when successful.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| who | `AccountIdLookupOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'refund_other', {
    'id': 'u128',
    'who': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### set_metadata
Set the metadata for an asset.

Origin must be Signed and the sender should be the Owner of the asset `id`.

Funds of sender are reserved according to the formula:
`MetadataDepositBase + MetadataDepositPerByte * (name.len + symbol.len)` taking into
account any already reserved funds.

- `id`: The identifier of the asset to update.
- `name`: The user friendly name of this asset. Limited in length by `StringLimit`.
- `symbol`: The exchange symbol for this asset. Limited in length by `StringLimit`.
- `decimals`: The number of decimals this asset uses to represent one unit.

Emits `MetadataSet`.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| name | `Vec<u8>` | 
| symbol | `Vec<u8>` | 
| decimals | `u8` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'set_metadata', {
    'decimals': 'u8',
    'id': 'u128',
    'name': 'Bytes',
    'symbol': 'Bytes',
}
)
```

---------
### set_min_balance
Sets the minimum balance of an asset.

Only works if there aren&\#x27;t any accounts that are holding the asset or if
the new value of `min_balance` is less than the old one.

Origin must be Signed and the sender has to be the Owner of the
asset `id`.

- `id`: The identifier of the asset.
- `min_balance`: The new value of `min_balance`.

Emits `AssetMinBalanceChanged` event when successful.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| min_balance | `T::Balance` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'set_min_balance', {'id': 'u128', 'min_balance': 'u128'}
)
```

---------
### set_team
Change the Issuer, Admin and Freezer of an asset.

Origin must be Signed and the sender should be the Owner of the asset `id`.

- `id`: The identifier of the asset to be frozen.
- `issuer`: The new Issuer of this asset.
- `admin`: The new Admin of this asset.
- `freezer`: The new Freezer of this asset.

Emits `TeamChanged`.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| issuer | `AccountIdLookupOf<T>` | 
| admin | `AccountIdLookupOf<T>` | 
| freezer | `AccountIdLookupOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'set_team', {
    'admin': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'freezer': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'id': 'u128',
    'issuer': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### start_destroy
Start the process of destroying a fungible asset class.

`start_destroy` is the first in a series of extrinsics that should be called, to allow
destruction of an asset class.

The origin must conform to `ForceOrigin` or must be `Signed` by the asset&\#x27;s `owner`.

- `id`: The identifier of the asset to be destroyed. This must identify an existing
  asset.

The asset class must be frozen before calling `start_destroy`.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'start_destroy', {'id': 'u128'}
)
```

---------
### thaw
Allow unprivileged transfers to and from an account again.

Origin must be Signed and the sender should be the Admin of the asset `id`.

- `id`: The identifier of the asset to be frozen.
- `who`: The account to be unfrozen.

Emits `Thawed`.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| who | `AccountIdLookupOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'thaw', {
    'id': 'u128',
    'who': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### thaw_asset
Allow unprivileged transfers for the asset again.

Origin must be Signed and the sender should be the Admin of the asset `id`.

- `id`: The identifier of the asset to be thawed.

Emits `Thawed`.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'thaw_asset', {'id': 'u128'}
)
```

---------
### touch
Create an asset account for non-provider assets.

A deposit will be taken from the signer account.

- `origin`: Must be Signed; the signer account must have sufficient funds for a deposit
  to be taken.
- `id`: The identifier of the asset for the account to be created.

Emits `Touched` event when successful.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'touch', {'id': 'u128'}
)
```

---------
### touch_other
Create an asset account for `who`.

A deposit will be taken from the signer account.

- `origin`: Must be Signed by `Freezer` or `Admin` of the asset `id`; the signer account
  must have sufficient funds for a deposit to be taken.
- `id`: The identifier of the asset for the account to be created.
- `who`: The account to be created.

Emits `Touched` event when successful.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| who | `AccountIdLookupOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'touch_other', {
    'id': 'u128',
    'who': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### transfer
Move some assets from the sender account to another.

Origin must be Signed.

- `id`: The identifier of the asset to have some amount transferred.
- `target`: The account to be credited.
- `amount`: The amount by which the sender&\#x27;s balance of assets should be reduced and
`target`&\#x27;s balance increased. The amount actually transferred may be slightly greater in
the case that the transfer would otherwise take the sender balance above zero but below
the minimum balance. Must be greater than zero.

Emits `Transferred` with the actual amount transferred. If this takes the source balance
to below the minimum for the asset, then the amount transferred is increased to take it
to zero.

Weight: `O(1)`
Modes: Pre-existence of `target`; Post-existence of sender; Account pre-existence of
`target`.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| target | `AccountIdLookupOf<T>` | 
| amount | `T::Balance` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'transfer', {
    'amount': 'u128',
    'id': 'u128',
    'target': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### transfer_approved
Transfer some asset balance from a previously delegated account to some third-party
account.

Origin must be Signed and there must be an approval in place by the `owner` to the
signer.

If the entire amount approved for transfer is transferred, then any deposit previously
reserved by `approve_transfer` is unreserved.

- `id`: The identifier of the asset.
- `owner`: The account which previously approved for a transfer of at least `amount` and
from which the asset balance will be withdrawn.
- `destination`: The account to which the asset balance of `amount` will be transferred.
- `amount`: The amount of assets to transfer.

Emits `TransferredApproved` on success.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| owner | `AccountIdLookupOf<T>` | 
| destination | `AccountIdLookupOf<T>` | 
| amount | `T::Balance` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'transfer_approved', {
    'amount': 'u128',
    'destination': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'id': 'u128',
    'owner': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### transfer_keep_alive
Move some assets from the sender account to another, keeping the sender account alive.

Origin must be Signed.

- `id`: The identifier of the asset to have some amount transferred.
- `target`: The account to be credited.
- `amount`: The amount by which the sender&\#x27;s balance of assets should be reduced and
`target`&\#x27;s balance increased. The amount actually transferred may be slightly greater in
the case that the transfer would otherwise take the sender balance above zero but below
the minimum balance. Must be greater than zero.

Emits `Transferred` with the actual amount transferred. If this takes the source balance
to below the minimum for the asset, then the amount transferred is increased to take it
to zero.

Weight: `O(1)`
Modes: Pre-existence of `target`; Post-existence of sender; Account pre-existence of
`target`.
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| target | `AccountIdLookupOf<T>` | 
| amount | `T::Balance` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'transfer_keep_alive', {
    'amount': 'u128',
    'id': 'u128',
    'target': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
### transfer_ownership
Change the Owner of an asset.

Origin must be Signed and the sender should be the Owner of the asset `id`.

- `id`: The identifier of the asset.
- `owner`: The new Owner of this asset.

Emits `OwnerChanged`.

Weight: `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| id | `T::AssetIdParameter` | 
| owner | `AccountIdLookupOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Assets', 'transfer_ownership', {
    'id': 'u128',
    'owner': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
}
)
```

---------
## Events

---------
### AccountsDestroyed
Accounts were destroyed for given asset.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| accounts_destroyed | `u32` | ```u32```
| accounts_remaining | `u32` | ```u32```

---------
### ApprovalCancelled
An approval for account `delegate` was cancelled by `owner`.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| owner | `T::AccountId` | ```AccountId```
| delegate | `T::AccountId` | ```AccountId```

---------
### ApprovalsDestroyed
Approvals were destroyed for given asset.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| approvals_destroyed | `u32` | ```u32```
| approvals_remaining | `u32` | ```u32```

---------
### ApprovedTransfer
(Additional) funds have been approved for transfer to a destination account.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| source | `T::AccountId` | ```AccountId```
| delegate | `T::AccountId` | ```AccountId```
| amount | `T::Balance` | ```u128```

---------
### AssetFrozen
Some asset `asset_id` was frozen.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```

---------
### AssetMinBalanceChanged
The min_balance of an asset has been updated by the asset owner.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| new_min_balance | `T::Balance` | ```u128```

---------
### AssetStatusChanged
An asset has had its attributes changed by the `Force` origin.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```

---------
### AssetThawed
Some asset `asset_id` was thawed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```

---------
### Blocked
Some account `who` was blocked.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| who | `T::AccountId` | ```AccountId```

---------
### Burned
Some assets were destroyed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| owner | `T::AccountId` | ```AccountId```
| balance | `T::Balance` | ```u128```

---------
### Created
Some asset class was created.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| creator | `T::AccountId` | ```AccountId```
| owner | `T::AccountId` | ```AccountId```

---------
### Destroyed
An asset class was destroyed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```

---------
### DestructionStarted
An asset class is in the process of being destroyed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```

---------
### ForceCreated
Some asset class was force-created.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| owner | `T::AccountId` | ```AccountId```

---------
### Frozen
Some account `who` was frozen.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| who | `T::AccountId` | ```AccountId```

---------
### Issued
Some assets were issued.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| owner | `T::AccountId` | ```AccountId```
| amount | `T::Balance` | ```u128```

---------
### MetadataCleared
Metadata has been cleared for an asset.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```

---------
### MetadataSet
New metadata has been set for an asset.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| name | `Vec<u8>` | ```Bytes```
| symbol | `Vec<u8>` | ```Bytes```
| decimals | `u8` | ```u8```
| is_frozen | `bool` | ```bool```

---------
### OwnerChanged
The owner changed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| owner | `T::AccountId` | ```AccountId```

---------
### TeamChanged
The management team changed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| issuer | `T::AccountId` | ```AccountId```
| admin | `T::AccountId` | ```AccountId```
| freezer | `T::AccountId` | ```AccountId```

---------
### Thawed
Some account `who` was thawed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| who | `T::AccountId` | ```AccountId```

---------
### Touched
Some account `who` was created with a deposit from `depositor`.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| who | `T::AccountId` | ```AccountId```
| depositor | `T::AccountId` | ```AccountId```

---------
### Transferred
Some assets were transferred.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| from | `T::AccountId` | ```AccountId```
| to | `T::AccountId` | ```AccountId```
| amount | `T::Balance` | ```u128```

---------
### TransferredApproved
An `amount` was transferred in its entirety from `owner` to `destination` by
the approved `delegate`.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| asset_id | `T::AssetId` | ```u128```
| owner | `T::AccountId` | ```AccountId```
| delegate | `T::AccountId` | ```AccountId```
| destination | `T::AccountId` | ```AccountId```
| amount | `T::Balance` | ```u128```

---------
## Storage functions

---------
### Account
 The holdings of a specific account for a specific asset.

#### Python
```python
result = substrate.query(
    'Assets', 'Account', ['u128', 'AccountId']
)
```

#### Return value
```python
{
    'balance': 'u128',
    'extra': (),
    'reason': {
        'Consumer': None,
        'DepositFrom': ('AccountId', 'u128'),
        'DepositHeld': 'u128',
        'DepositRefunded': None,
        'Sufficient': None,
    },
    'status': ('Liquid', 'Frozen', 'Blocked'),
}
```
---------
### Approvals
 Approved balance transfers. First balance is the amount approved for transfer. Second
 is the amount of `T::Currency` reserved for storing this.
 First key is the asset ID, second key is the owner and third key is the delegate.

#### Python
```python
result = substrate.query(
    'Assets', 'Approvals', ['u128', 'AccountId', 'AccountId']
)
```

#### Return value
```python
{'amount': 'u128', 'deposit': 'u128'}
```
---------
### Asset
 Details of an asset.

#### Python
```python
result = substrate.query(
    'Assets', 'Asset', ['u128']
)
```

#### Return value
```python
{
    'accounts': 'u32',
    'admin': 'AccountId',
    'approvals': 'u32',
    'deposit': 'u128',
    'freezer': 'AccountId',
    'is_sufficient': 'bool',
    'issuer': 'AccountId',
    'min_balance': 'u128',
    'owner': 'AccountId',
    'status': ('Live', 'Frozen', 'Destroying'),
    'sufficients': 'u32',
    'supply': 'u128',
}
```
---------
### Metadata
 Metadata of an asset.

#### Python
```python
result = substrate.query(
    'Assets', 'Metadata', ['u128']
)
```

#### Return value
```python
{
    'decimals': 'u8',
    'deposit': 'u128',
    'is_frozen': 'bool',
    'name': 'Bytes',
    'symbol': 'Bytes',
}
```
---------
## Constants

---------
### ApprovalDeposit
 The amount of funds that must be reserved when creating a new approval.
#### Value
```python
0
```
#### Python
```python
constant = substrate.get_constant('Assets', 'ApprovalDeposit')
```
---------
### AssetAccountDeposit
 The amount of funds that must be reserved for a non-provider asset account to be
 maintained.
#### Value
```python
1
```
#### Python
```python
constant = substrate.get_constant('Assets', 'AssetAccountDeposit')
```
---------
### AssetDeposit
 The basic amount of funds that must be reserved for an asset.
#### Value
```python
0
```
#### Python
```python
constant = substrate.get_constant('Assets', 'AssetDeposit')
```
---------
### MetadataDepositBase
 The basic amount of funds that must be reserved when adding metadata to your asset.
#### Value
```python
0
```
#### Python
```python
constant = substrate.get_constant('Assets', 'MetadataDepositBase')
```
---------
### MetadataDepositPerByte
 The additional funds that must be reserved for the number of bytes you store in your
 metadata.
#### Value
```python
0
```
#### Python
```python
constant = substrate.get_constant('Assets', 'MetadataDepositPerByte')
```
---------
### RemoveItemsLimit
 Max number of items to destroy per `destroy_accounts` and `destroy_approvals` call.

 Must be configured to result in a weight that makes each call fit in a block.
#### Value
```python
1000
```
#### Python
```python
constant = substrate.get_constant('Assets', 'RemoveItemsLimit')
```
---------
### StringLimit
 The maximum length of a name or symbol stored on-chain.
#### Value
```python
50
```
#### Python
```python
constant = substrate.get_constant('Assets', 'StringLimit')
```
---------
## Errors

---------
### AlreadyExists
The asset-account already exists.

---------
### AssetNotLive
The asset is not live, and likely being destroyed.

---------
### BadMetadata
Invalid metadata given.

---------
### BadWitness
Invalid witness data given.

---------
### BalanceLow
Account balance must be greater than or equal to the transfer amount.

---------
### CallbackFailed
Callback action resulted in error

---------
### Frozen
The origin account is frozen.

---------
### InUse
The asset ID is already taken.

---------
### IncorrectStatus
The asset status is not the expected status.

---------
### LiveAsset
The asset is a live asset and is actively being used. Usually emit for operations such
as `start_destroy` which require the asset to be in a destroying state.

---------
### MinBalanceZero
Minimum balance should be non-zero.

---------
### NoAccount
The account to alter does not exist.

---------
### NoDeposit
The asset-account doesn&\#x27;t have an associated deposit.

---------
### NoPermission
The signing account has no permission to do the operation.

---------
### NotFrozen
The asset should be frozen before the given operation.

---------
### Unapproved
No approval exists that would allow the transfer.

---------
### UnavailableConsumer
Unable to increment the consumer reference counters on the account. Either no provider
reference exists to allow a non-zero balance of a non-self-sufficient asset, or one
fewer then the maximum number of consumers has been reached.

---------
### Unknown
The given asset ID is unknown.

---------
### WouldBurn
The operation would result in funds being burned.

---------
### WouldDie
The source account would not survive the transfer and it needs to stay alive.

---------
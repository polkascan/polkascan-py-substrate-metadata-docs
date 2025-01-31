
# Crowdloans

---------
## Calls

---------
### auction_failed
If a `crowdloan` failed, get the coins back and mark the vault as ready
for distribution
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'auction_failed', {'crowdloan': 'u32'}
)
```

---------
### auction_succeeded
Mark the associated vault as `Succeed` if vault is `Closed`
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'auction_succeeded', {'crowdloan': 'u32'}
)
```

---------
### claim
If a `crowdloan` succeeded, claim the liquid derivatives of the
contributed assets
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 
| lease_start | `LeasePeriod` | 
| lease_end | `LeasePeriod` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'claim', {
    'crowdloan': 'u32',
    'lease_end': 'u32',
    'lease_start': 'u32',
}
)
```

---------
### claim_for
If a `crowdloan` succeeded, claim the liquid derivatives of the
contributed assets for others
#### Attributes
| Name | Type |
| -------- | -------- | 
| dest | `<T::Lookup as StaticLookup>::Source` | 
| crowdloan | `ParaId` | 
| lease_start | `LeasePeriod` | 
| lease_end | `LeasePeriod` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'claim_for', {
    'crowdloan': 'u32',
    'dest': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'lease_end': 'u32',
    'lease_start': 'u32',
}
)
```

---------
### close
Mark the associated vault as `Closed` and stop accepting contributions
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'close', {'crowdloan': 'u32'}
)
```

---------
### contribute
Contribute `amount` to the vault of `crowdloan` and receive some
shares from it
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 
| amount | `BalanceOf<T>` | 
| referral_code | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'contribute', {
    'amount': 'u128',
    'crowdloan': 'u32',
    'referral_code': 'Bytes',
}
)
```

---------
### create_vault
Create a new vault via a governance decision

- `crowdloan`: parachain id of the crowdloan, should be consistent with relaychain
- `ctoken`: ctoken is used for the vault, should be unique
- `lease_start`: lease start index
- `lease_end`: lease end index
- `contribution_strategy`: currently, only XCM strategy is supported.
- `cap`: the capacity limit for the vault
- `end_block`: the crowdloan end block for the vault
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 
| ctoken | `AssetIdOf<T>` | 
| lease_start | `LeasePeriod` | 
| lease_end | `LeasePeriod` | 
| contribution_strategy | `ContributionStrategy` | 
| cap | `BalanceOf<T>` | 
| end_block | `BlockNumberFor<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'create_vault', {
    'cap': 'u128',
    'contribution_strategy': (
        'XCM',
        'XCMPROXY',
    ),
    'crowdloan': 'u32',
    'ctoken': 'u32',
    'end_block': 'u32',
    'lease_end': 'u32',
    'lease_start': 'u32',
}
)
```

---------
### dissolve_vault
Dissolve vault
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 
| lease_start | `LeasePeriod` | 
| lease_end | `LeasePeriod` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'dissolve_vault', {
    'crowdloan': 'u32',
    'lease_end': 'u32',
    'lease_start': 'u32',
}
)
```

---------
### force_claim_for
If a `crowdloan` expired, force claim the liquid derivatives for users
who didn&\#x27;t claim it during succeed phase
#### Attributes
| Name | Type |
| -------- | -------- | 
| dest | `<T::Lookup as StaticLookup>::Source` | 
| crowdloan | `ParaId` | 
| lease_start | `LeasePeriod` | 
| lease_end | `LeasePeriod` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'force_claim_for', {
    'crowdloan': 'u32',
    'dest': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'lease_end': 'u32',
    'lease_start': 'u32',
}
)
```

---------
### migrate_pending
Migrate pending contribution by sending xcm
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'migrate_pending', {'crowdloan': 'u32'}
)
```

---------
### notification_received
#### Attributes
| Name | Type |
| -------- | -------- | 
| query_id | `QueryId` | 
| response | `Response` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'notification_received', {
    'query_id': 'u64',
    'response': {
        'Assets': [
            {
                'fun': {
                    'Fungible': 'u128',
                    'NonFungible': {
                        'Array16': '[u8; 16]',
                        'Array32': '[u8; 32]',
                        'Array4': '[u8; 4]',
                        'Array8': '[u8; 8]',
                        'Index': 'u128',
                        'Undefined': None,
                    },
                },
                'id': {
                    'Abstract': '[u8; 32]',
                    'Concrete': {
                        'interior': 'scale_info::61',
                        'parents': 'u8',
                    },
                },
            },
        ],
        'DispatchResult': {
            'Error': 'Bytes',
            'Success': None,
            'TruncatedError': 'Bytes',
        },
        'ExecutionResult': (
            None,
            (
                'u32',
                {
                    'AssetNotFound': None,
                    'BadOrigin': None,
                    'Barrier': None,
                    'DestinationUnsupported': None,
                    'ExceedsMaxMessageSize': None,
                    'ExceedsStackLimit': None,
                    'ExpectationFalse': None,
                    'ExportError': None,
                    'FailedToDecode': None,
                    'FailedToTransactAsset': None,
                    'FeesNotMet': None,
                    'HoldingWouldOverflow': None,
                    'InvalidLocation': None,
                    'LocationCannotHold': None,
                    'LocationFull': None,
                    'LocationNotInvertible': None,
                    'LockError': None,
                    'MaxWeightInvalid': None,
                    'NameMismatch': None,
                    'NoDeal': None,
                    'NoPermission': None,
                    'NotDepositable': None,
                    'NotHoldingFees': None,
                    'NotWithdrawable': None,
                    'Overflow': None,
                    'PalletNotFound': None,
                    'ReanchorFailed': None,
                    'TooExpensive': None,
                    'Transport': None,
                    'Trap': 'u64',
                    'Unanchored': None,
                    'UnhandledXcmVersion': None,
                    'Unimplemented': None,
                    'UnknownClaim': None,
                    'Unroutable': None,
                    'UntrustedReserveLocation': None,
                    'UntrustedTeleportLocation': None,
                    'VersionIncompatible': None,
                    'WeightLimitReached': {
                        'proof_size': 'u64',
                        'ref_time': 'u64',
                    },
                    'WeightNotComputable': None,
                },
            ),
        ),
        'Null': None,
        'PalletsInfo': [
            {
                'index': 'u32',
                'major': 'u32',
                'minor': 'u32',
                'module_name': 'Bytes',
                'name': 'Bytes',
                'patch': 'u32',
            },
        ],
        'Version': 'u32',
    },
}
)
```

---------
### open
Mark the associated vault as ready for real contributions on the relaychain
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'open', {'crowdloan': 'u32'}
)
```

---------
### redeem
If a `crowdloan` expired, redeem the contributed assets
using ctoken
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 
| lease_start | `LeasePeriod` | 
| lease_end | `LeasePeriod` | 
| amount | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'redeem', {
    'amount': 'u128',
    'crowdloan': 'u32',
    'lease_end': 'u32',
    'lease_start': 'u32',
}
)
```

---------
### redeem_and_lend_for
If a `crowdloan` expired, redeem the contributed assets
and lend it to Money market
#### Attributes
| Name | Type |
| -------- | -------- | 
| dest | `<T::Lookup as StaticLookup>::Source` | 
| crowdloan | `ParaId` | 
| lease_start | `LeasePeriod` | 
| lease_end | `LeasePeriod` | 
| amount | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'redeem_and_lend_for', {
    'amount': 'u128',
    'crowdloan': 'u32',
    'dest': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'lease_end': 'u32',
    'lease_start': 'u32',
}
)
```

---------
### refund
Refund contributions
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 
| lease_start | `LeasePeriod` | 
| lease_end | `LeasePeriod` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'refund', {
    'crowdloan': 'u32',
    'lease_end': 'u32',
    'lease_start': 'u32',
}
)
```

---------
### refund_for
Refund contributions for single user

Once relaychain is in vrf but parachain didn&\#x27;t update vrf in time.
Contributions received during this period should be refund to users,
especially for those succeeded parachains.
#### Attributes
| Name | Type |
| -------- | -------- | 
| dest | `<T::Lookup as StaticLookup>::Source` | 
| crowdloan | `ParaId` | 
| kind | `ChildStorageKind` | 
| amount | `BalanceOf<T>` | 
| lease_start | `LeasePeriod` | 
| lease_end | `LeasePeriod` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'refund_for', {
    'amount': 'u128',
    'crowdloan': 'u32',
    'dest': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'kind': (
        'Pending',
        'Flying',
        'Contributed',
    ),
    'lease_end': 'u32',
    'lease_start': 'u32',
}
)
```

---------
### reopen
Mark the associated vault as `Contributing` and continue to accept contributions
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'reopen', {'crowdloan': 'u32'}
)
```

---------
### set_vrf
Set crowdloans which entered vrf period
#### Attributes
| Name | Type |
| -------- | -------- | 
| flag | `bool` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'set_vrf', {'flag': 'bool'}
)
```

---------
### slot_expired
If a `crowdloan` succeeded and its slot expired, use `call` to
claim back the funds lent to the parachain
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'slot_expired', {'crowdloan': 'u32'}
)
```

---------
### update_leases_bonus
Update crowdloans proxy address in relaychain
#### Attributes
| Name | Type |
| -------- | -------- | 
| lease_start | `LeasePeriod` | 
| lease_end | `LeasePeriod` | 
| bonus_config | `BonusConfig<BalanceOf<T>>` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'update_leases_bonus', {
    'bonus_config': {
        'bonus_per_token': 'u128',
        'end_time': 'u64',
        'start_time': 'u64',
    },
    'lease_end': 'u32',
    'lease_start': 'u32',
}
)
```

---------
### update_proxy
Update crowdloans proxy address in relaychain
#### Attributes
| Name | Type |
| -------- | -------- | 
| proxy_address | `AccountIdOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'update_proxy', {'proxy_address': 'AccountId'}
)
```

---------
### update_vault
Update an existing vault via a governance decision
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 
| cap | `Option<BalanceOf<T>>` | 
| end_block | `Option<BlockNumberFor<T>>` | 
| contribution_strategy | `Option<ContributionStrategy>` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'update_vault', {
    'cap': (None, 'u128'),
    'contribution_strategy': (
        None,
        ('XCM', 'XCMPROXY'),
    ),
    'crowdloan': 'u32',
    'end_block': (None, 'u32'),
}
)
```

---------
### withdraw
If a `crowdloan` failed, withdraw the contributed assets
#### Attributes
| Name | Type |
| -------- | -------- | 
| crowdloan | `ParaId` | 
| lease_start | `LeasePeriod` | 
| lease_end | `LeasePeriod` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'withdraw', {
    'crowdloan': 'u32',
    'lease_end': 'u32',
    'lease_start': 'u32',
}
)
```

---------
### withdraw_for
If a `crowdloan` failed, withdraw the contributed assets for others
#### Attributes
| Name | Type |
| -------- | -------- | 
| dest | `<T::Lookup as StaticLookup>::Source` | 
| crowdloan | `ParaId` | 
| lease_start | `LeasePeriod` | 
| lease_end | `LeasePeriod` | 

#### Python
```python
call = substrate.compose_call(
    'Crowdloans', 'withdraw_for', {
    'crowdloan': 'u32',
    'dest': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': (),
        'Raw': 'Bytes',
    },
    'lease_end': 'u32',
    'lease_start': 'u32',
}
)
```

---------
## Events

---------
### AllMigrated
All contributions migrated
[para_id, vault_id]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```

---------
### AllRefunded
Partially Refunded
[para_id, vault_id]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```

---------
### LeasesBonusUpdated
Update leases bonus
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `VaultId` | ```('u32', 'u32')```
| None | `BonusConfig<BalanceOf<T>>` | ```{'bonus_per_token': 'u128', 'start_time': 'u64', 'end_time': 'u64'}```

---------
### NotificationReceived
Notification received
[multi_location, query_id, res]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `Box<MultiLocation>` | ```{'parents': 'u8', 'interior': {'Here': None, 'X1': {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': {'Unit': None, 'Moniker': '[u8; 4]', 'Index': 'u32', 'Executive': None, 'Technical': None, 'Legislative': None, 'Judicial': None, 'Defense': None, 'Administration': None, 'Treasury': None}, 'part': {'Voice': None, 'Members': 'InnerStruct', 'Fraction': 'InnerStruct', 'AtLeastProportion': 'InnerStruct', 'MoreThanProportion': 'InnerStruct'}}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': {'block_number': 'u64', 'block_hash': '[u8; 32]'}, 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': {'chain_id': 'u64'}, 'BitcoinCore': None, 'BitcoinCash': None}}, 'X2': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}), 'X3': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}), 'X4': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}), 'X5': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}), 'X6': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}), 'X7': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}), 'X8': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::65'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::65'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::65'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::68', 'part': 'scale_info::69'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}})}}```
| None | `QueryId` | ```u64```
| None | `Option<(u32, XcmError)>` | ```(None, ('u32', {'Overflow': None, 'Unimplemented': None, 'UntrustedReserveLocation': None, 'UntrustedTeleportLocation': None, 'LocationFull': None, 'LocationNotInvertible': None, 'BadOrigin': None, 'InvalidLocation': None, 'AssetNotFound': None, 'FailedToTransactAsset': None, 'NotWithdrawable': None, 'LocationCannotHold': None, 'ExceedsMaxMessageSize': None, 'DestinationUnsupported': None, 'Transport': None, 'Unroutable': None, 'UnknownClaim': None, 'FailedToDecode': None, 'MaxWeightInvalid': None, 'NotHoldingFees': None, 'TooExpensive': None, 'Trap': 'u64', 'ExpectationFalse': None, 'PalletNotFound': None, 'NameMismatch': None, 'VersionIncompatible': None, 'HoldingWouldOverflow': None, 'ExportError': None, 'ReanchorFailed': None, 'NoDeal': None, 'FeesNotMet': None, 'LockError': None, 'NoPermission': None, 'Unanchored': None, 'NotDepositable': None, 'UnhandledXcmVersion': None, 'WeightLimitReached': {'ref_time': 'u64', 'proof_size': 'u64'}, 'Barrier': None, 'WeightNotComputable': None, 'ExceedsStackLimit': None}))```

---------
### PartiallyMigrated
Partially contributions migrated
[para_id, vault_id]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```

---------
### PartiallyRefunded
Partially Refunded
[para_id, vault_id]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```

---------
### ProxyUpdated
Update proxy address
[account]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `T::AccountId` | ```AccountId```

---------
### UserRefunded
Refunded
[para_id, vault_id, account, child_storage_kind, amount]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```
| None | `T::AccountId` | ```AccountId```
| None | `ChildStorageKind` | ```('Pending', 'Flying', 'Contributed')```
| None | `BalanceOf<T>` | ```u128```

---------
### VaultClaimed
A user claimed CToken from vault
[para_id, vault_id, ctoken_id, account, amount, phase]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```
| None | `AssetIdOf<T>` | ```u32```
| None | `T::AccountId` | ```AccountId```
| None | `BalanceOf<T>` | ```u128```
| None | `VaultPhase` | ```('Pending', 'Contributing', 'Closed', 'Failed', 'Succeeded', 'Expired')```

---------
### VaultContributed
Vault successfully contributed
[para_id, vault_id, contributor, amount, referral_code]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```
| None | `T::AccountId` | ```AccountId```
| None | `BalanceOf<T>` | ```u128```
| None | `Vec<u8>` | ```Bytes```

---------
### VaultCreated
New vault was created
[para_id, vault_id, ctoken_id, phase, contribution_strategy, cap, end_block, trie_index]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```
| None | `AssetIdOf<T>` | ```u32```
| None | `VaultPhase` | ```('Pending', 'Contributing', 'Closed', 'Failed', 'Succeeded', 'Expired')```
| None | `ContributionStrategy` | ```('XCM', 'XCMPROXY')```
| None | `BalanceOf<T>` | ```u128```
| None | `BlockNumberFor<T>` | ```u32```
| None | `TrieIndex` | ```u32```

---------
### VaultDissolved
Vault has been dissolved
[para_id, vault_id]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```

---------
### VaultDoContributing
Vault is trying to do contributing
[para_id, vault_id, contributor, amount, referral_code]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```
| None | `T::AccountId` | ```AccountId```
| None | `BalanceOf<T>` | ```u128```
| None | `Vec<u8>` | ```Bytes```

---------
### VaultDoWithdrawing
Vault is trying to do withdrawing
[para_id, vault_id, amount, target_phase]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```
| None | `BalanceOf<T>` | ```u128```
| None | `VaultPhase` | ```('Pending', 'Contributing', 'Closed', 'Failed', 'Succeeded', 'Expired')```

---------
### VaultPhaseUpdated
Vault was opened
[para_id, vault_id, pre_phase, now_phase]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```
| None | `VaultPhase` | ```('Pending', 'Contributing', 'Closed', 'Failed', 'Succeeded', 'Expired')```
| None | `VaultPhase` | ```('Pending', 'Contributing', 'Closed', 'Failed', 'Succeeded', 'Expired')```

---------
### VaultRedeemed
A user redeemed contributed assets using CToken
[para_id, vault_id, ctoken_id, account, amount, phase]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```
| None | `AssetIdOf<T>` | ```u32```
| None | `T::AccountId` | ```AccountId```
| None | `BalanceOf<T>` | ```u128```
| None | `VaultPhase` | ```('Pending', 'Contributing', 'Closed', 'Failed', 'Succeeded', 'Expired')```

---------
### VaultUpdated
Existing vault was updated
[para_id, vault_id, contribution_strategy, cap, end_block]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```
| None | `ContributionStrategy` | ```('XCM', 'XCMPROXY')```
| None | `BalanceOf<T>` | ```u128```
| None | `BlockNumberFor<T>` | ```u32```

---------
### VaultWithdrew
A user withdrew contributed assets from vault
[para_id, vault_id, account, amount, phase]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `ParaId` | ```u32```
| None | `VaultId` | ```('u32', 'u32')```
| None | `T::AccountId` | ```AccountId```
| None | `BalanceOf<T>` | ```u128```
| None | `VaultPhase` | ```('Pending', 'Contributing', 'Closed', 'Failed', 'Succeeded', 'Expired')```

---------
### VrfUpdated
Vrfs updated
[vrf_flag]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `bool` | ```bool```

---------
## Storage functions

---------
### CTokensRegistry

#### Python
```python
result = substrate.query(
    'Crowdloans', 'CTokensRegistry', ['u32', 'u32']
)
```

#### Return value
```python
'u32'
```
---------
### IsVrf

#### Python
```python
result = substrate.query(
    'Crowdloans', 'IsVrf', []
)
```

#### Return value
```python
'bool'
```
---------
### LeasesBonus

#### Python
```python
result = substrate.query(
    'Crowdloans', 'LeasesBonus', ['u32', 'u32']
)
```

#### Return value
```python
{'bonus_per_token': 'u128', 'end_time': 'u64', 'start_time': 'u64'}
```
---------
### LeasesRegistry

#### Python
```python
result = substrate.query(
    'Crowdloans', 'LeasesRegistry', ['u32']
)
```

#### Return value
```python
('u32', 'u32')
```
---------
### NextTrieIndex

#### Python
```python
result = substrate.query(
    'Crowdloans', 'NextTrieIndex', []
)
```

#### Return value
```python
'u32'
```
---------
### ProxyAddress

#### Python
```python
result = substrate.query(
    'Crowdloans', 'ProxyAddress', []
)
```

#### Return value
```python
'AccountId'
```
---------
### StorageVersion
 Storage version of the pallet.

#### Python
```python
result = substrate.query(
    'Crowdloans', 'StorageVersion', []
)
```

#### Return value
```python
('V0_0_0', 'V1_0_0', 'V2_0_0')
```
---------
### Vaults

#### Python
```python
result = substrate.query(
    'Crowdloans', 'Vaults', ['u32', 'u32', 'u32']
)
```

#### Return value
```python
{
    'cap': 'u128',
    'contributed': 'u128',
    'contribution_strategy': ('XCM', 'XCMPROXY'),
    'ctoken': 'u32',
    'end_block': 'u32',
    'flying': 'u128',
    'lease_end': 'u32',
    'lease_start': 'u32',
    'pending': 'u128',
    'phase': (
        'Pending',
        'Contributing',
        'Closed',
        'Failed',
        'Succeeded',
        'Expired',
    ),
    'trie_index': 'u32',
}
```
---------
### XcmRequests

#### Python
```python
result = substrate.query(
    'Crowdloans', 'XcmRequests', ['u64']
)
```

#### Return value
```python
{
    'Contribute': {
        'amount': 'u128',
        'crowdloan': 'u32',
        'referral_code': 'Bytes',
        'vault_id': ('u32', 'u32'),
        'who': 'AccountId',
    },
    'Withdraw': {
        'amount': 'u128',
        'crowdloan': 'u32',
        'target_phase': (
            'Pending',
            'Contributing',
            'Closed',
            'Failed',
            'Succeeded',
            'Expired',
        ),
        'vault_id': ('u32', 'u32'),
    },
}
```
---------
## Constants

---------
### GetNativeCurrencyId
 The asset id for native currency.
#### Value
```python
1
```
#### Python
```python
constant = substrate.get_constant('Crowdloans', 'GetNativeCurrencyId')
```
---------
### LeaseOffset
 LeaseOffset from relaychain
#### Value
```python
921600
```
#### Python
```python
constant = substrate.get_constant('Crowdloans', 'LeaseOffset')
```
---------
### LeasePerYear
 LeaseOffset from relaychain
#### Value
```python
4
```
#### Python
```python
constant = substrate.get_constant('Crowdloans', 'LeasePerYear')
```
---------
### LeasePeriod
 LeasePeriod from relaychain
#### Value
```python
1209600
```
#### Python
```python
constant = substrate.get_constant('Crowdloans', 'LeasePeriod')
```
---------
### MigrateKeysLimit
 Maximum keys to be migrated in one extrinsic
#### Value
```python
5
```
#### Python
```python
constant = substrate.get_constant('Crowdloans', 'MigrateKeysLimit')
```
---------
### MinContribution
 Minimum contribute amount
#### Value
```python
50000000000
```
#### Python
```python
constant = substrate.get_constant('Crowdloans', 'MinContribution')
```
---------
### PalletId
 Pallet account for collecting contributions
#### Value
```python
'0x6372776c6f616e73'
```
#### Python
```python
constant = substrate.get_constant('Crowdloans', 'PalletId')
```
---------
### RelayCurrency
 Relay currency
#### Value
```python
101
```
#### Python
```python
constant = substrate.get_constant('Crowdloans', 'RelayCurrency')
```
---------
### RemoveKeysLimit
#### Value
```python
1000
```
#### Python
```python
constant = substrate.get_constant('Crowdloans', 'RemoveKeysLimit')
```
---------
### SelfParaId
 Returns the parachain ID we are running with.
#### Value
```python
2012
```
#### Python
```python
constant = substrate.get_constant('Crowdloans', 'SelfParaId')
```
---------
## Errors

---------
### CTokenDoesNotExist
CToken does not exist

---------
### CapExceeded
Attempted contribution violates contribution cap

---------
### CrowdloanAlreadyExists
Crowdloan ParaId already exists

---------
### EmptyProxyAddress
Proxy address is empty

---------
### EndBlockExceeded
Current relay block is greater than vault end block

---------
### IncorrectVaultPhase
Vault is not in correct phase

---------
### InsufficientBalance
Balance is not enough

---------
### InsufficientContribution
Contribution is not enough

---------
### InvalidCToken
CToken for provided (leaseStart, leaseEnd) is different with what has been created previously

---------
### InvalidCap
Capacity cannot be zero value

---------
### InvalidParams
Invalid params input

---------
### LastPeriodBeforeFirstPeriod
Last lease period must be greater than first lease period.

---------
### NoContributions
There are no contributions stored in contributed childstorage

---------
### NotReadyToDissolve
Vault is not ready to be dissolved

---------
### VaultAlreadyExists
Vault already exists

---------
### VaultDoesNotExist
Vault does not exist

---------
### VaultNotEnded
Vault for provided ParaId not ended

---------
### VrfDelayInProgress
No contributions allowed during the VRF delay

---------
### WrongBonusConfig
BonusConfig is wrong

---------
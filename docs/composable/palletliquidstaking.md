
# PalletLiquidStaking

---------
## Calls

---------
### bond
Bond on relaychain via xcm.transact
#### Attributes
| Name | Type |
| -------- | -------- | 
| derivative_index | `DerivativeIndex` | 
| amount | `BalanceOf<T>` | 
| payee | `RewardDestination<T::AccountId>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'bond', {
    'amount': 'u128',
    'derivative_index': 'u16',
    'payee': {
        'Account': 'AccountId',
        'Controller': None,
        'None': None,
        'Staked': None,
        'Stash': None,
    },
}
)
```

---------
### bond_extra
Bond_extra on relaychain via xcm.transact
#### Attributes
| Name | Type |
| -------- | -------- | 
| derivative_index | `DerivativeIndex` | 
| amount | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'bond_extra', {
    'amount': 'u128',
    'derivative_index': 'u16',
}
)
```

---------
### cancel_unstake
Cancel unstake
#### Attributes
| Name | Type |
| -------- | -------- | 
| amount | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'cancel_unstake', {'amount': 'u128'}
)
```

---------
### claim_for
Claim assets back when current era index arrived
at target era
#### Attributes
| Name | Type |
| -------- | -------- | 
| dest | `<T::Lookup as StaticLookup>::Source` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'claim_for', {
    'dest': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': 'u32',
        'Raw': 'Bytes',
    },
}
)
```

---------
### fast_match_unstake
Fast match unstake through matching pool
#### Attributes
| Name | Type |
| -------- | -------- | 
| unstaker_list | `Vec<T::AccountId>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'fast_match_unstake', {'unstaker_list': ['AccountId']}
)
```

---------
### force_advance_era
Force advance era
#### Attributes
| Name | Type |
| -------- | -------- | 
| offset | `EraIndex` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'force_advance_era', {'offset': 'u32'}
)
```

---------
### force_matching
Force matching
#### Attributes
No attributes

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'force_matching', {}
)
```

---------
### force_set_current_era
Force set current era
#### Attributes
| Name | Type |
| -------- | -------- | 
| era | `EraIndex` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'force_set_current_era', {'era': 'u32'}
)
```

---------
### force_set_era_start_block
Force set era start block
#### Attributes
| Name | Type |
| -------- | -------- | 
| block_number | `BlockNumberFor<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'force_set_era_start_block', {'block_number': 'u32'}
)
```

---------
### force_set_staking_ledger
Force set staking_ledger
#### Attributes
| Name | Type |
| -------- | -------- | 
| derivative_index | `DerivativeIndex` | 
| staking_ledger | `StakingLedger<T::AccountId, BalanceOf<T>>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'force_set_staking_ledger', {
    'derivative_index': 'u16',
    'staking_ledger': {
        'active': 'u128',
        'claimed_rewards': ['u32'],
        'stash': 'AccountId',
        'total': 'u128',
        'unlocking': [
            {
                'era': 'u32',
                'value': 'u128',
            },
        ],
    },
}
)
```

---------
### initiate_exchange_rate
#### Attributes
No attributes

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'initiate_exchange_rate', {}
)
```

---------
### nominate
Nominate on relaychain via xcm.transact
#### Attributes
| Name | Type |
| -------- | -------- | 
| derivative_index | `DerivativeIndex` | 
| targets | `Vec<T::AccountId>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'nominate', {
    'derivative_index': 'u16',
    'targets': ['AccountId'],
}
)
```

---------
### notification_received
Internal call which is expected to be triggered only by xcm instruction
#### Attributes
| Name | Type |
| -------- | -------- | 
| query_id | `QueryId` | 
| response | `Response` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'notification_received', {
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
                        'interior': 'scale_info::71',
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
### rebond
Rebond on relaychain via xcm.transact
#### Attributes
| Name | Type |
| -------- | -------- | 
| derivative_index | `DerivativeIndex` | 
| amount | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'rebond', {
    'amount': 'u128',
    'derivative_index': 'u16',
}
)
```

---------
### reduce_reserves
Reduces reserves by transferring to receiver.
#### Attributes
| Name | Type |
| -------- | -------- | 
| receiver | `<T::Lookup as StaticLookup>::Source` | 
| reduce_amount | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'reduce_reserves', {
    'receiver': {
        'Address20': '[u8; 20]',
        'Address32': '[u8; 32]',
        'Id': 'AccountId',
        'Index': 'u32',
        'Raw': 'Bytes',
    },
    'reduce_amount': 'u128',
}
)
```

---------
### relaychain_storage_proof_key
#### Attributes
| Name | Type |
| -------- | -------- | 
| derivative_index | `DerivativeIndex` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'relaychain_storage_proof_key', {'derivative_index': 'u16'}
)
```

---------
### set_current_era
Set current era by providing storage proof
#### Attributes
| Name | Type |
| -------- | -------- | 
| era | `EraIndex` | 
| proof | `Vec<Vec<u8>>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'set_current_era', {'era': 'u32', 'proof': ['Bytes']}
)
```

---------
### set_members
#### Attributes
| Name | Type |
| -------- | -------- | 
| members | `Vec<T::AccountId>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'set_members', {'members': ['AccountId']}
)
```

---------
### set_staking_ledger
Set staking_ledger by providing storage proof
#### Attributes
| Name | Type |
| -------- | -------- | 
| derivative_index | `DerivativeIndex` | 
| staking_ledger | `StakingLedger<T::AccountId, BalanceOf<T>>` | 
| proof | `Vec<Vec<u8>>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'set_staking_ledger', {
    'derivative_index': 'u16',
    'proof': ['Bytes'],
    'staking_ledger': {
        'active': 'u128',
        'claimed_rewards': ['u32'],
        'stash': 'AccountId',
        'total': 'u128',
        'unlocking': [
            {
                'era': 'u32',
                'value': 'u128',
            },
        ],
    },
}
)
```

---------
### stake
Put assets under staking, the native assets will be transferred to the account
owned by the pallet, user receive derivative in return, such derivative can be
further used as collateral for lending.

- `amount`: the amount of staking assets
#### Attributes
| Name | Type |
| -------- | -------- | 
| amount | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'stake', {'amount': 'u128'}
)
```

---------
### unbond
Unbond on relaychain via xcm.transact
#### Attributes
| Name | Type |
| -------- | -------- | 
| derivative_index | `DerivativeIndex` | 
| amount | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'unbond', {
    'amount': 'u128',
    'derivative_index': 'u16',
}
)
```

---------
### unstake
Unstake by exchange derivative for assets, the assets will not be available immediately.
Instead, the request is recorded and pending for the nomination accounts on relaychain
chain to do the `unbond` operation.

- `amount`: the amount of derivative
#### Attributes
| Name | Type |
| -------- | -------- | 
| liquid_amount | `BalanceOf<T>` | 
| unstake_provider | `UnstakeProvider` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'unstake', {
    'liquid_amount': 'u128',
    'unstake_provider': (
        'RelayChain',
        'Loans',
        'MatchingPool',
    ),
}
)
```

---------
### update_commission_rate
Update commission rate
#### Attributes
| Name | Type |
| -------- | -------- | 
| commission_rate | `Rate` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'update_commission_rate', {'commission_rate': 'u128'}
)
```

---------
### update_incentive
Update incentive amount
#### Attributes
| Name | Type |
| -------- | -------- | 
| amount | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'update_incentive', {'amount': 'u128'}
)
```

---------
### update_reserve_factor
Update insurance pool&\#x27;s reserve_factor
#### Attributes
| Name | Type |
| -------- | -------- | 
| reserve_factor | `Ratio` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'update_reserve_factor', {'reserve_factor': 'u32'}
)
```

---------
### update_staking_ledger_cap
Update ledger&\#x27;s max bonded cap
#### Attributes
| Name | Type |
| -------- | -------- | 
| cap | `BalanceOf<T>` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'update_staking_ledger_cap', {'cap': 'u128'}
)
```

---------
### withdraw_unbonded
Withdraw unbonded on relaychain via xcm.transact
#### Attributes
| Name | Type |
| -------- | -------- | 
| derivative_index | `DerivativeIndex` | 
| num_slashing_spans | `u32` | 

#### Python
```python
call = substrate.compose_call(
    'PalletLiquidStaking', 'withdraw_unbonded', {
    'derivative_index': 'u16',
    'num_slashing_spans': 'u32',
}
)
```

---------
## Events

---------
### Bonding
Sent staking.bond call to relaychain
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `DerivativeIndex` | ```u16```
| None | `T::AccountId` | ```AccountId```
| None | `BalanceOf<T>` | ```u128```
| None | `RewardDestination<T::AccountId>` | ```{'Staked': None, 'Stash': None, 'Controller': None, 'Account': 'AccountId', 'None': None}```

---------
### BondingExtra
Sent staking.bond_extra call to relaychain
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `DerivativeIndex` | ```u16```
| None | `BalanceOf<T>` | ```u128```

---------
### ClaimedFor
Claim user&\#x27;s unbonded staking assets
[account_id, amount]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `T::AccountId` | ```AccountId```
| None | `BalanceOf<T>` | ```u128```

---------
### CommissionRateUpdated
Commission rate was updated
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `Rate` | ```u128```

---------
### ExchangeRateUpdated
Exchange rate was updated
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `Rate` | ```u128```

---------
### FastUnstakeMatched
Fast Unstake Matched
[unstaker, received_staking_amount, matched_liquid_amount, fee_in_liquid_currency]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `T::AccountId` | ```AccountId```
| None | `BalanceOf<T>` | ```u128```
| None | `BalanceOf<T>` | ```u128```
| None | `BalanceOf<T>` | ```u128```

---------
### IncentiveUpdated
Incentive amount was updated
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `BalanceOf<T>` | ```u128```

---------
### Matching
Matching stakes &amp; unstakes for optimizing operations to be done
on relay chain
[bond_amount, rebond_amount, unbond_amount]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `BalanceOf<T>` | ```u128```
| None | `BalanceOf<T>` | ```u128```
| None | `BalanceOf<T>` | ```u128```

---------
### NewEra
New era
[era_index]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `EraIndex` | ```u32```

---------
### Nominating
Sent staking.nominate call to relaychain
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `DerivativeIndex` | ```u16```
| None | `Vec<T::AccountId>` | ```['AccountId']```

---------
### NonIdealStakingLedger
Not the ideal staking ledger
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `DerivativeIndex` | ```u16```

---------
### NotificationReceived
Notification received
[multi_location, query_id, res]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `Box<MultiLocation>` | ```{'parents': 'u8', 'interior': {'Here': None, 'X1': {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': {'Unit': None, 'Moniker': '[u8; 4]', 'Index': 'u32', 'Executive': None, 'Technical': None, 'Legislative': None, 'Judicial': None, 'Defense': None, 'Administration': None, 'Treasury': None}, 'part': {'Voice': None, 'Members': 'InnerStruct', 'Fraction': 'InnerStruct', 'AtLeastProportion': 'InnerStruct', 'MoreThanProportion': 'InnerStruct'}}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': {'block_number': 'u64', 'block_hash': '[u8; 32]'}, 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': {'chain_id': 'u64'}, 'BitcoinCore': None, 'BitcoinCash': None}}, 'X2': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}), 'X3': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}), 'X4': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}), 'X5': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}), 'X6': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}), 'X7': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}), 'X8': ({'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}}, {'Parachain': 'u32', 'AccountId32': {'network': (None, 'scale_info::75'), 'id': '[u8; 32]'}, 'AccountIndex64': {'network': (None, 'scale_info::75'), 'index': 'u64'}, 'AccountKey20': {'network': (None, 'scale_info::75'), 'key': '[u8; 20]'}, 'PalletInstance': 'u8', 'GeneralIndex': 'u128', 'GeneralKey': {'length': 'u8', 'data': '[u8; 32]'}, 'OnlyChild': None, 'Plurality': {'id': 'scale_info::78', 'part': 'scale_info::79'}, 'GlobalConsensus': {'ByGenesis': '[u8; 32]', 'ByFork': 'InnerStruct', 'Polkadot': None, 'Kusama': None, 'Westend': None, 'Rococo': None, 'Wococo': None, 'Ethereum': 'InnerStruct', 'BitcoinCore': None, 'BitcoinCash': None}})}}```
| None | `QueryId` | ```u64```
| None | `Option<(u32, XcmError)>` | ```(None, ('u32', {'Overflow': None, 'Unimplemented': None, 'UntrustedReserveLocation': None, 'UntrustedTeleportLocation': None, 'LocationFull': None, 'LocationNotInvertible': None, 'BadOrigin': None, 'InvalidLocation': None, 'AssetNotFound': None, 'FailedToTransactAsset': None, 'NotWithdrawable': None, 'LocationCannotHold': None, 'ExceedsMaxMessageSize': None, 'DestinationUnsupported': None, 'Transport': None, 'Unroutable': None, 'UnknownClaim': None, 'FailedToDecode': None, 'MaxWeightInvalid': None, 'NotHoldingFees': None, 'TooExpensive': None, 'Trap': 'u64', 'ExpectationFalse': None, 'PalletNotFound': None, 'NameMismatch': None, 'VersionIncompatible': None, 'HoldingWouldOverflow': None, 'ExportError': None, 'ReanchorFailed': None, 'NoDeal': None, 'FeesNotMet': None, 'LockError': None, 'NoPermission': None, 'Unanchored': None, 'NotDepositable': None, 'UnhandledXcmVersion': None, 'WeightLimitReached': {'ref_time': 'u64', 'proof_size': 'u64'}, 'Barrier': None, 'WeightNotComputable': None, 'ExceedsStackLimit': None}))```

---------
### OnInitializeHook
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| relay_block_number | `BlockNumberFor<T>` | ```u32```
| era | `u32` | ```u32```

---------
### Rebonding
Sent staking.rebond call to relaychain
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `DerivativeIndex` | ```u16```
| None | `BalanceOf<T>` | ```u128```

---------
### RelaychainStorageProofKey
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `DerivativeIndex` | ```u16```
| None | `Vec<u8>` | ```Bytes```
| None | `T::AccountId` | ```AccountId```

---------
### ReserveFactorUpdated
Reserve_factor was updated
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `Ratio` | ```u32```

---------
### ReservesReduced
Event emitted when the reserves are reduced
[receiver, reduced_amount]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `T::AccountId` | ```AccountId```
| None | `BalanceOf<T>` | ```u128```

---------
### SetMembers
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| members | `Vec<T::AccountId>` | ```['AccountId']```

---------
### SetStakingLedgerTry
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| origin | `T::AccountId` | ```AccountId```
| derivative_index | `DerivativeIndex` | ```u16```
| staking_ledger | `StakingLedger<T::AccountId, BalanceOf<T>>` | ```{'stash': 'AccountId', 'total': 'u128', 'active': 'u128', 'unlocking': [{'value': 'u128', 'era': 'u32'}], 'claimed_rewards': ['u32']}```
| proof | `Vec<Vec<u8>>` | ```['Bytes']```

---------
### Staked
The assets get staked successfully
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `T::AccountId` | ```AccountId```
| None | `BalanceOf<T>` | ```u128```

---------
### StakingLedgerCapUpdated
Staking ledger&\#x27;s cap was updated
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `BalanceOf<T>` | ```u128```

---------
### StakingLedgerUpdated
Staking ledger updated
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `DerivativeIndex` | ```u16```
| None | `StakingLedger<T::AccountId, BalanceOf<T>>` | ```{'stash': 'AccountId', 'total': 'u128', 'active': 'u128', 'unlocking': [{'value': 'u128', 'era': 'u32'}], 'claimed_rewards': ['u32']}```

---------
### Unbonding
Sent staking.unbond call to relaychain
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `DerivativeIndex` | ```u16```
| None | `BalanceOf<T>` | ```u128```

---------
### UnstakeCancelled
Unstake cancelled
[account_id, amount, liquid_amount]
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `T::AccountId` | ```AccountId```
| None | `BalanceOf<T>` | ```u128```
| None | `BalanceOf<T>` | ```u128```

---------
### Unstaked
The derivative get unstaked successfully
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `T::AccountId` | ```AccountId```
| None | `BalanceOf<T>` | ```u128```
| None | `BalanceOf<T>` | ```u128```

---------
### WithdrawingUnbonded
Sent staking.withdraw_unbonded call to relaychain
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| None | `DerivativeIndex` | ```u16```
| None | `u32` | ```u32```

---------
## Storage functions

---------
### CommissionRate
 The commission rate charge for staking total rewards.

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'CommissionRate', []
)
```

#### Return value
```python
'u128'
```
---------
### CurrentEra
 Current era index
 Users can come to claim their unbonded staking assets back once this value arrived
 at certain height decided by `BondingDuration` and `EraLength`

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'CurrentEra', []
)
```

#### Return value
```python
'u32'
```
---------
### EraStartBlock
 Current era&#x27;s start relaychain block

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'EraStartBlock', []
)
```

#### Return value
```python
'u32'
```
---------
### ExchangeRate
 The exchange rate between relaychain native asset and the voucher.

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'ExchangeRate', []
)
```

#### Return value
```python
'u128'
```
---------
### FastUnstakeRequests
 Users&#x27; fast unstake requests in liquid currency

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'FastUnstakeRequests', ['AccountId']
)
```

#### Return value
```python
'u128'
```
---------
### Incentive
 Incentive for users who successfully update era/ledger

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'Incentive', []
)
```

#### Return value
```python
'u128'
```
---------
### IsMatched
 Set to true if already do matching in current era
 clear after arriving at next era

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'IsMatched', []
)
```

#### Return value
```python
'bool'
```
---------
### IsUpdated
 Set to true if staking ledger has been modified in this block

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'IsUpdated', ['u16']
)
```

#### Return value
```python
'bool'
```
---------
### MatchingPool
 Store total stake amount and unstake amount in each era,
 And will update when stake/unstake occurred.

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'MatchingPool', []
)
```

#### Return value
```python
{
    'total_stake_amount': {'reserved': 'u128', 'total': 'u128'},
    'total_unstake_amount': {'reserved': 'u128', 'total': 'u128'},
}
```
---------
### Members

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'Members', []
)
```

#### Return value
```python
['AccountId']
```
---------
### ReserveFactor
 Fraction of reward currently set aside for reserves.

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'ReserveFactor', []
)
```

#### Return value
```python
'u32'
```
---------
### StakingLedgerCap
 Staking ledger&#x27;s cap

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'StakingLedgerCap', []
)
```

#### Return value
```python
'u128'
```
---------
### StakingLedgers
 Platform&#x27;s staking ledgers

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'StakingLedgers', ['u16']
)
```

#### Return value
```python
{
    'active': 'u128',
    'claimed_rewards': ['u32'],
    'stash': 'AccountId',
    'total': 'u128',
    'unlocking': [{'era': 'u32', 'value': 'u128'}],
}
```
---------
### StorageVersion
 Storage version of the pallet.

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'StorageVersion', []
)
```

#### Return value
```python
('V1', 'V2', 'V3')
```
---------
### TotalReserves

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'TotalReserves', []
)
```

#### Return value
```python
'u128'
```
---------
### Unlockings
 Unbonding requests to be handled after arriving at target era

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'Unlockings', ['AccountId']
)
```

#### Return value
```python
[{'era': 'u32', 'value': 'u128'}]
```
---------
### ValidationData
 ValidationData of previous block

 This is needed since validation data from cumulus_pallet_parachain_system
 will be updated in set_validation_data Inherent which happens before external
 extrinsics

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'ValidationData', []
)
```

#### Return value
```python
{
    'max_pov_size': 'u32',
    'parent_head': 'Bytes',
    'relay_parent_number': 'u32',
    'relay_parent_storage_root': 'scale_info::12',
}
```
---------
### XcmRequests
 Flying &amp; failed xcm requests

#### Python
```python
result = substrate.query(
    'PalletLiquidStaking', 'XcmRequests', ['u64']
)
```

#### Return value
```python
{
    'Bond': {'amount': 'u128', 'index': 'u16'},
    'BondExtra': {'amount': 'u128', 'index': 'u16'},
    'Nominate': {'index': 'u16', 'targets': ['AccountId']},
    'Rebond': {'amount': 'u128', 'index': 'u16'},
    'Unbond': {'amount': 'u128', 'index': 'u16'},
    'WithdrawUnbonded': {'index': 'u16', 'num_slashing_spans': 'u32'},
}
```
---------
## Constants

---------
### BondingDuration
 Number of unbond indexes for unlocking.
#### Value
```python
28
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'BondingDuration')
```
---------
### DerivativeIndexList
 Derivative index list
#### Value
```python
[0]
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'DerivativeIndexList')
```
---------
### ElectionSolutionStoredOffset
 Number of blocknumbers that do_matching after each era updated.
 Need to do_bond before relaychain store npos solution
#### Value
```python
12600
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'ElectionSolutionStoredOffset')
```
---------
### EraLength
 Number of blocknumbers that each period contains.
 SessionsPerEra * EpochDuration / MILLISECS_PER_BLOCK
#### Value
```python
14400
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'EraLength')
```
---------
### LiquidCurrency
 Liquid currency
#### Value
```python
79228162514264337593543950351
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'LiquidCurrency')
```
---------
### MatchingPoolFastUnstakeFee
 MatchingPool fast unstake fee
#### Value
```python
10000000000000000
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'MatchingPoolFastUnstakeFee')
```
---------
### MinNominatorBond
 The minimum active bond to become and maintain the role of a nominator.
#### Value
```python
100000000000
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'MinNominatorBond')
```
---------
### MinStake
 Minimum stake amount
#### Value
```python
10000000000
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'MinStake')
```
---------
### MinUnstake
 Minimum unstake amount
#### Value
```python
5000000000
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'MinUnstake')
```
---------
### NativeCurrency
 The asset id for native currency.
#### Value
```python
79228162514264337593543950338
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'NativeCurrency')
```
---------
### NumSlashingSpans
#### Value
```python
0
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'NumSlashingSpans')
```
---------
### PalletId
 The pallet id of liquid staking, keeps all the staking assets
#### Value
```python
'0x636f6d2f6c71736b'
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'PalletId')
```
---------
### ProtocolFeeReceiver
 Who/where to send the protocol fees
#### Value
```python
'644rjzDzYYvYs2o83m7VdHhHtxudjq1JnzMnCRRGXwBKyPVq'
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'ProtocolFeeReceiver')
```
---------
### SelfParaId
 Returns the parachain ID we are running with.
#### Value
```python
2019
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'SelfParaId')
```
---------
### StakingCurrency
 Staking currency
#### Value
```python
79228162514264337593543950342
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'StakingCurrency')
```
---------
### XcmFees
 Xcm fees
#### Value
```python
500000000
```
#### Python
```python
constant = substrate.get_constant('PalletLiquidStaking', 'XcmFees')
```
---------
## Errors

---------
### AlreadyBonded
Stash is already bonded.

---------
### CapExceeded
Exceeded liquid currency&\#x27;s market cap

---------
### InsufficientBond
Cannot have a nominator role with value less than the minimum defined by
`MinNominatorBond`

---------
### InvalidCap
Invalid market cap

---------
### InvalidCommissionRate
Invalid commission rate

---------
### InvalidDerivativeIndex
Invalid derivative index

---------
### InvalidExchangeRate
Exchange rate is invalid.

---------
### InvalidFactor
The factor should be bigger than 0% and smaller than 100%

---------
### InvalidLiquidCurrency
Invalid liquid currency

---------
### InvalidOrigin

---------
### InvalidProof
The merkle proof is invalid

---------
### InvalidStakingCurrency
Invalid staking currency

---------
### InvalidStakingLedger
Invalid staking ledger

---------
### NoMoreChunks
Can not schedule more unlock chunks.

---------
### NoUnlockings
No unlocking items

---------
### NotBonded
Stash wasn&\#x27;t bonded yet

---------
### NotWithdrawn
Not withdrawn unbonded yet

---------
### NothingToClaim
Nothing to claim yet

---------
### StakeTooSmall
The stake was below the minimum, `MinStake`.

---------
### StakingLedgerLocked
Staking ledger is locked due to mutation in notification_received

---------
### UnstakeTooSmall
The unstake was below the minimum, `MinUnstake`.

---------
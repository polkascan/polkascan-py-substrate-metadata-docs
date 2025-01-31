
# System

---------
## Calls

---------
### kill_prefix
Kill all storage items with a key that starts with the given prefix.

**NOTE:** We rely on the Root origin to provide us the number of subkeys under
the prefix we are removing to accurately calculate the weight of this function.
#### Attributes
| Name | Type |
| -------- | -------- | 
| prefix | `Key` | 
| subkeys | `u32` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'kill_prefix', {'prefix': 'Bytes', 'subkeys': 'u32'}
)
```

---------
### kill_storage
Kill some items from storage.
#### Attributes
| Name | Type |
| -------- | -------- | 
| keys | `Vec<Key>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'kill_storage', {'keys': ['Bytes']}
)
```

---------
### remark
Make some on-chain remark.

\#\# Complexity
- `O(1)`
#### Attributes
| Name | Type |
| -------- | -------- | 
| remark | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'remark', {'remark': 'Bytes'}
)
```

---------
### remark_with_event
Make some on-chain remark and emit event.
#### Attributes
| Name | Type |
| -------- | -------- | 
| remark | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'remark_with_event', {'remark': 'Bytes'}
)
```

---------
### set_code
Set the new runtime code.

\#\# Complexity
- `O(C + S)` where `C` length of `code` and `S` complexity of `can_set_code`
#### Attributes
| Name | Type |
| -------- | -------- | 
| code | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'set_code', {'code': 'Bytes'}
)
```

---------
### set_code_without_checks
Set the new runtime code without doing any checks of the given `code`.

\#\# Complexity
- `O(C)` where `C` length of `code`
#### Attributes
| Name | Type |
| -------- | -------- | 
| code | `Vec<u8>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'set_code_without_checks', {'code': 'Bytes'}
)
```

---------
### set_heap_pages
Set the number of pages in the WebAssembly environment&\#x27;s heap.
#### Attributes
| Name | Type |
| -------- | -------- | 
| pages | `u64` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'set_heap_pages', {'pages': 'u64'}
)
```

---------
### set_storage
Set some items of storage.
#### Attributes
| Name | Type |
| -------- | -------- | 
| items | `Vec<KeyValue>` | 

#### Python
```python
call = substrate.compose_call(
    'System', 'set_storage', {'items': [('Bytes', 'Bytes')]}
)
```

---------
## Events

---------
### CodeUpdated
`:code` was updated.
#### Attributes
No attributes

---------
### ExtrinsicFailed
An extrinsic failed.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| dispatch_error | `DispatchError` | ```{'Other': None, 'CannotLookup': None, 'BadOrigin': None, 'Module': {'index': 'u8', 'error': '[u8; 4]'}, 'ConsumerRemaining': None, 'NoProviders': None, 'TooManyConsumers': None, 'Token': ('NoFunds', 'WouldDie', 'BelowMinimum', 'CannotCreate', 'UnknownAsset', 'Frozen', 'Unsupported'), 'Arithmetic': ('Underflow', 'Overflow', 'DivisionByZero'), 'Transactional': ('LimitReached', 'NoLayer'), 'Exhausted': None, 'Corruption': None, 'Unavailable': None}```
| dispatch_info | `DispatchInfo` | ```{'weight': {'ref_time': 'u64', 'proof_size': 'u64'}, 'class': ('Normal', 'Operational', 'Mandatory'), 'pays_fee': ('Yes', 'No')}```

---------
### ExtrinsicSuccess
An extrinsic completed successfully.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| dispatch_info | `DispatchInfo` | ```{'weight': {'ref_time': 'u64', 'proof_size': 'u64'}, 'class': ('Normal', 'Operational', 'Mandatory'), 'pays_fee': ('Yes', 'No')}```

---------
### KilledAccount
An account was reaped.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| account | `T::AccountId` | ```AccountId```

---------
### NewAccount
A new account was created.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| account | `T::AccountId` | ```AccountId```

---------
### Remarked
On on-chain remark happened.
#### Attributes
| Name | Type | Composition
| -------- | -------- | -------- |
| sender | `T::AccountId` | ```AccountId```
| hash | `T::Hash` | ```scale_info::11```

---------
## Storage functions

---------
### Account
 The full account information for a particular account ID.

#### Python
```python
result = substrate.query(
    'System', 'Account', ['AccountId']
)
```

#### Return value
```python
{
    'consumers': 'u32',
    'data': {
        'fee_frozen': 'u128',
        'free': 'u128',
        'misc_frozen': 'u128',
        'reserved': 'u128',
    },
    'nonce': 'u32',
    'providers': 'u32',
    'sufficients': 'u32',
}
```
---------
### AllExtrinsicsLen
 Total length (in bytes) for all extrinsics put together, for the current block.

#### Python
```python
result = substrate.query(
    'System', 'AllExtrinsicsLen', []
)
```

#### Return value
```python
'u32'
```
---------
### BlockHash
 Map of block numbers to block hashes.

#### Python
```python
result = substrate.query(
    'System', 'BlockHash', ['u32']
)
```

#### Return value
```python
'scale_info::11'
```
---------
### BlockWeight
 The current weight for the block.

#### Python
```python
result = substrate.query(
    'System', 'BlockWeight', []
)
```

#### Return value
```python
{
    'mandatory': {'proof_size': 'u64', 'ref_time': 'u64'},
    'normal': {'proof_size': 'u64', 'ref_time': 'u64'},
    'operational': {'proof_size': 'u64', 'ref_time': 'u64'},
}
```
---------
### Digest
 Digest of the current block, also part of the block header.

#### Python
```python
result = substrate.query(
    'System', 'Digest', []
)
```

#### Return value
```python
{
    'logs': [
        {
            'Other': 'Bytes',
            None: None,
            'Consensus': ('[u8; 4]', 'Bytes'),
            'PreRuntime': ('[u8; 4]', 'Bytes'),
            'RuntimeEnvironmentUpdated': None,
            'Seal': ('[u8; 4]', 'Bytes'),
        },
    ],
}
```
---------
### EventCount
 The number of events in the `Events&lt;T&gt;` list.

#### Python
```python
result = substrate.query(
    'System', 'EventCount', []
)
```

#### Return value
```python
'u32'
```
---------
### EventTopics
 Mapping between a topic (represented by T::Hash) and a vector of indexes
 of events in the `&lt;Events&lt;T&gt;&gt;` list.

 All topic vectors have deterministic storage locations depending on the topic. This
 allows light-clients to leverage the changes trie storage tracking mechanism and
 in case of changes fetch the list of events of interest.

 The value has the type `(T::BlockNumber, EventIndex)` because if we used only just
 the `EventIndex` then in case if the topic has the same contents on the next block
 no notification will be triggered thus the event might be lost.

#### Python
```python
result = substrate.query(
    'System', 'EventTopics', ['scale_info::11']
)
```

#### Return value
```python
[('u32', 'u32')]
```
---------
### Events
 Events deposited for the current block.

 NOTE: The item is unbound and should therefore never be read on chain.
 It could otherwise inflate the PoV size of a block.

 Events have a large in-memory size. Box the events to not go out-of-memory
 just in case someone still reads them from within the runtime.

#### Python
```python
result = substrate.query(
    'System', 'Events', []
)
```

#### Return value
```python
[
    {
        'event': {
            'System': {
                'CodeUpdated': None,
                'ExtrinsicFailed': {
                    'dispatch_error': 'scale_info::24',
                    'dispatch_info': 'scale_info::21',
                },
                'ExtrinsicSuccess': {'dispatch_info': 'scale_info::21'},
                'KilledAccount': {'account': 'AccountId'},
                'NewAccount': {'account': 'AccountId'},
                'Remarked': {'hash': 'scale_info::11', 'sender': 'AccountId'},
            },
            None: None,
            'Asset': {
                'AssetAffirmationExemption': '[u8; 12]',
                'AssetBalanceUpdated': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'u128',
                    (None, 'scale_info::56'),
                    (None, 'scale_info::56'),
                    'scale_info::160',
                ),
                'AssetCreated': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'bool',
                    'scale_info::123',
                    '[u8; 32]',
                    'Bytes',
                    ['scale_info::128'],
                    (None, 'Bytes'),
                ),
                'AssetFrozen': ('[u8; 32]', '[u8; 12]'),
                'AssetOwnershipTransferred': (
                    '[u8; 32]',
                    '[u8; 12]',
                    '[u8; 32]',
                ),
                'AssetRenamed': ('[u8; 32]', '[u8; 12]', 'Bytes'),
                'AssetTypeChanged': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'scale_info::123',
                ),
                'AssetUnfrozen': ('[u8; 32]', '[u8; 12]'),
                'ControllerTransfer': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'scale_info::56',
                    'u128',
                ),
                'CustomAssetTypeExists': ('[u8; 32]', 'u32', 'Bytes'),
                'CustomAssetTypeRegistered': ('[u8; 32]', 'u32', 'Bytes'),
                'DivisibilityChanged': ('[u8; 32]', '[u8; 12]', 'bool'),
                'DocumentAdded': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'u32',
                    'scale_info::134',
                ),
                'DocumentRemoved': ('[u8; 32]', '[u8; 12]', 'u32'),
                'ExtensionRemoved': ('[u8; 32]', '[u8; 12]', 'AccountId'),
                'FundingRoundSet': ('[u8; 32]', '[u8; 12]', 'Bytes'),
                'IdentifiersUpdated': (
                    '[u8; 32]',
                    '[u8; 12]',
                    ['scale_info::128'],
                ),
                'IsIssuable': ('[u8; 12]', 'bool'),
                'LocalMetadataKeyDeleted': ('[u8; 32]', '[u8; 12]', 'u64'),
                'MetadataValueDeleted': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'scale_info::158',
                ),
                'PreApprovedAsset': ('[u8; 32]', '[u8; 12]'),
                'RegisterAssetMetadataGlobalType': (
                    'Bytes',
                    'u64',
                    'scale_info::151',
                ),
                'RegisterAssetMetadataLocalType': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'Bytes',
                    'u64',
                    'scale_info::151',
                ),
                'RemoveAssetAffirmationExemption': '[u8; 12]',
                'RemovePreApprovedAsset': ('[u8; 32]', '[u8; 12]'),
                'SetAssetMetadataValue': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'Bytes',
                    (None, 'scale_info::147'),
                ),
                'SetAssetMetadataValueDetails': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'scale_info::147',
                ),
                'TickerRegistered': ('[u8; 32]', '[u8; 12]', (None, 'u64')),
                'TickerTransferred': ('[u8; 32]', '[u8; 12]', '[u8; 32]'),
                'TransferWithData': (
                    '[u8; 32]',
                    '[u8; 12]',
                    '[u8; 32]',
                    '[u8; 32]',
                    'u128',
                    'Bytes',
                ),
            },
            'Balances': {
                'AccountBalanceBurned': ('[u8; 32]', 'AccountId', 'u128'),
                'BalanceSet': ('[u8; 32]', 'AccountId', 'u128', 'u128'),
                'Endowed': ((None, '[u8; 32]'), 'AccountId', 'u128'),
                'ReserveRepatriated': (
                    'AccountId',
                    'AccountId',
                    'u128',
                    'scale_info::35',
                ),
                'Reserved': ('AccountId', 'u128'),
                'Transfer': (
                    (None, '[u8; 32]'),
                    'AccountId',
                    (None, '[u8; 32]'),
                    'AccountId',
                    'u128',
                    (None, '[u8; 32]'),
                ),
                'Unreserved': ('AccountId', 'u128'),
            },
            'Base': {'UnexpectedError': (None, 'scale_info::24')},
            'Bridge': {
                'AdminChanged': ('[u8; 32]', 'AccountId'),
                'BridgeLimitUpdated': ('[u8; 32]', 'u128', 'u32'),
                'BridgeTxFailed': (
                    '[u8; 32]',
                    'scale_info::97',
                    'scale_info::24',
                ),
                'BridgeTxScheduleFailed': (
                    '[u8; 32]',
                    'scale_info::97',
                    'Bytes',
                ),
                'BridgeTxScheduled': ('[u8; 32]', 'scale_info::97', 'u32'),
                'Bridged': ('[u8; 32]', 'scale_info::97'),
                'ControllerChanged': ('[u8; 32]', 'AccountId'),
                'ExemptedUpdated': ('[u8; 32]', '[u8; 32]', 'bool'),
                'FreezeAdminAdded': ('[u8; 32]', 'AccountId'),
                'FreezeAdminRemoved': ('[u8; 32]', 'AccountId'),
                'Frozen': '[u8; 32]',
                'FrozenTx': ('[u8; 32]', 'scale_info::97'),
                'TimelockChanged': ('[u8; 32]', 'u32'),
                'TxRemoved': ('[u8; 32]', 'scale_info::97'),
                'TxsHandled': [('AccountId', 'u32', 'scale_info::100')],
                'Unfrozen': '[u8; 32]',
                'UnfrozenTx': ('[u8; 32]', 'scale_info::97'),
            },
            'CapitalDistribution': {
                'BenefitClaimed': (
                    '[u8; 32]',
                    '[u8; 32]',
                    'scale_info::165',
                    'scale_info::167',
                    'u128',
                    'u32',
                ),
                'Created': ('[u8; 32]', 'scale_info::165', 'scale_info::167'),
                'Reclaimed': ('[u8; 32]', 'scale_info::165', 'u128'),
                'Removed': ('[u8; 32]', 'scale_info::165'),
            },
            'CddServiceProviders': {
                'ActiveLimitChanged': ('[u8; 32]', 'u32', 'u32'),
                'Dummy': None,
                'MemberAdded': ('[u8; 32]', '[u8; 32]'),
                'MemberRemoved': ('[u8; 32]', '[u8; 32]'),
                'MemberRevoked': ('[u8; 32]', '[u8; 32]'),
                'MembersReset': ('[u8; 32]', ['[u8; 32]']),
                'MembersSwapped': ('[u8; 32]', '[u8; 32]', '[u8; 32]'),
            },
            'Checkpoint': {
                'CheckpointCreated': ((None, '[u8; 32]'), '[u8; 12]', 'u64', 'u128', 'u64'),
                'MaximumSchedulesComplexityChanged': ('[u8; 32]', 'u64'),
                'ScheduleCreated': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'u64',
                    'scale_info::172',
                ),
                'ScheduleRemoved': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'u64',
                    'scale_info::172',
                ),
            },
            'CommitteeMembership': {
                'ActiveLimitChanged': ('[u8; 32]', 'u32', 'u32'),
                'Dummy': None,
                'MemberAdded': ('[u8; 32]', '[u8; 32]'),
                'MemberRemoved': ('[u8; 32]', '[u8; 32]'),
                'MemberRevoked': ('[u8; 32]', '[u8; 32]'),
                'MembersReset': ('[u8; 32]', ['[u8; 32]']),
                'MembersSwapped': ('[u8; 32]', '[u8; 32]', '[u8; 32]'),
            },
            'ComplianceManager': {
                'AssetCompliancePaused': ('[u8; 32]', '[u8; 12]'),
                'AssetComplianceReplaced': (
                    '[u8; 32]',
                    '[u8; 12]',
                    ['scale_info::176'],
                ),
                'AssetComplianceReset': ('[u8; 32]', '[u8; 12]'),
                'AssetComplianceResumed': ('[u8; 32]', '[u8; 12]'),
                'ComplianceRequirementChanged': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'scale_info::176',
                ),
                'ComplianceRequirementCreated': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'scale_info::176',
                ),
                'ComplianceRequirementRemoved': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'u32',
                ),
                'TrustedDefaultClaimIssuerAdded': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'scale_info::183',
                ),
                'TrustedDefaultClaimIssuerRemoved': (
                    '[u8; 32]',
                    '[u8; 12]',
                    '[u8; 32]',
                ),
            },
            'Contracts': {
                'Called': {'caller': 'AccountId', 'contract': 'AccountId'},
                'CodeRemoved': {'code_hash': 'scale_info::11'},
                'CodeStored': {'code_hash': 'scale_info::11'},
                'ContractCodeUpdated': {
                    'contract': 'AccountId',
                    'new_code_hash': 'scale_info::11',
                    'old_code_hash': 'scale_info::11',
                },
                'ContractEmitted': {'contract': 'AccountId', 'data': 'Bytes'},
                'DelegateCalled': {
                    'code_hash': 'scale_info::11',
                    'contract': 'AccountId',
                },
                'Instantiated': {
                    'contract': 'AccountId',
                    'deployer': 'AccountId',
                },
                'Terminated': {
                    'beneficiary': 'AccountId',
                    'contract': 'AccountId',
                },
            },
            'CorporateAction': {
                'CAInitiated': (
                    '[u8; 32]',
                    'scale_info::165',
                    'scale_info::192',
                    'Bytes',
                ),
                'CALinkedToDoc': ('[u8; 32]', 'scale_info::165', ['u32']),
                'CARemoved': ('[u8; 32]', 'scale_info::165'),
                'DefaultTargetIdentitiesChanged': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'scale_info::189',
                ),
                'DefaultWithholdingTaxChanged': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'u32',
                ),
                'DidWithholdingTaxChanged': (
                    '[u8; 32]',
                    '[u8; 12]',
                    '[u8; 32]',
                    (None, 'u32'),
                ),
                'MaxDetailsLengthChanged': ('[u8; 32]', 'u32'),
                'RecordDateChanged': (
                    '[u8; 32]',
                    'scale_info::165',
                    'scale_info::192',
                ),
            },
            'CorporateBallot': {
                'Created': (
                    '[u8; 32]',
                    'scale_info::165',
                    'scale_info::202',
                    'scale_info::203',
                    'bool',
                ),
                'MetaChanged': (
                    '[u8; 32]',
                    'scale_info::165',
                    'scale_info::203',
                ),
                'RCVChanged': ('[u8; 32]', 'scale_info::165', 'bool'),
                'RangeChanged': (
                    '[u8; 32]',
                    'scale_info::165',
                    'scale_info::202',
                ),
                'Removed': ('[u8; 32]', 'scale_info::165'),
                'VoteCast': (
                    '[u8; 32]',
                    'scale_info::165',
                    ['scale_info::212'],
                ),
            },
            'ExternalAgents': {
                'AgentAdded': ('[u8; 32]', '[u8; 12]', 'scale_info::72'),
                'AgentRemoved': ('[u8; 32]', '[u8; 12]', '[u8; 32]'),
                'GroupChanged': (
                    '[u8; 32]',
                    '[u8; 12]',
                    '[u8; 32]',
                    'scale_info::72',
                ),
                'GroupCreated': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'u32',
                    'scale_info::46',
                ),
                'GroupPermissionsUpdated': (
                    '[u8; 32]',
                    '[u8; 12]',
                    'u32',
                    'scale_info::46',
                ),
            },
            'Grandpa': {
                'NewAuthorities': {'authority_set': [('[u8; 32]', 'u64')]},
                'Paused': None,
                'Resumed': None,
            },
            'Identity': {
                'AssetDidRegistered': ('[u8; 32]', '[u8; 12]'),
                'AuthorizationAdded': (
                    '[u8; 32]',
                    (None, '[u8; 32]'),
                    (None, 'AccountId'),
                    'u64',
                    'scale_info::71',
                    (None, 'u64'),
                ),
                'AuthorizationConsumed': (
                    (None, '[u8; 32]'),
                    (None, 'AccountId'),
                    'u64',
                ),
                'AuthorizationRejected': (
                    (None, '[u8; 32]'),
                    (None, 'AccountId'),
                    'u64',
                ),
                'AuthorizationRetryLimitReached': (
                    (None, '[u8; 32]'),
                    (None, 'AccountId'),
                    'u64',
                ),
                'AuthorizationRevoked': (
                    (None, '[u8; 32]'),
                    (None, 'AccountId'),
                    'u64',
                ),
                'CddClaimsInvalidated': ('[u8; 32]', 'u64'),
                'CddRequirementForPrimaryKeyUpdated': 'bool',
                'ChildDidCreated': ('[u8; 32]', '[u8; 32]', 'AccountId'),
                'ChildDidUnlinked': ('[u8; 32]', '[u8; 32]', '[u8; 32]'),
                'ClaimAdded': ('[u8; 32]', 'scale_info::62'),
                'ClaimRevoked': ('[u8; 32]', 'scale_info::62'),
                'CustomClaimTypeAdded': ('[u8; 32]', 'u32', 'Bytes'),
                'DidCreated': ('[u8; 32]', 'AccountId', ['scale_info::39']),
                'PrimaryKeyUpdated': ('[u8; 32]', 'AccountId', 'AccountId'),
                'SecondaryKeyLeftIdentity': ('[u8; 32]', 'AccountId'),
                'SecondaryKeyPermissionsUpdated': (
                    '[u8; 32]',
                    'AccountId',
                    'scale_info::40',
                    'scale_info::40',
                ),
                'SecondaryKeysAdded': ('[u8; 32]', ['scale_info::39']),
                'SecondaryKeysFrozen': '[u8; 32]',
                'SecondaryKeysRemoved': ('[u8; 32]', ['AccountId']),
                'SecondaryKeysUnfrozen': '[u8; 32]',
            },
            'ImOnline': {
                'AllGood': None,
                'HeartbeatReceived': {'authority_id': '[u8; 32]'},
                'SomeOffline': {'offline': [('AccountId', 'scale_info::118')]},
            },
            'Indices': {
                'IndexAssigned': {'index': 'u32', 'who': 'AccountId'},
                'IndexFreed': {'index': 'u32'},
                'IndexFrozen': {'index': 'u32', 'who': 'AccountId'},
            },
            'MultiSig': {
                'MultiSigCreated': (
                    '[u8; 32]',
                    'AccountId',
                    'AccountId',
                    ['scale_info::95'],
                    'u64',
                ),
                'MultiSigSignaturesRequiredChanged': (
                    '[u8; 32]',
                    'AccountId',
                    'u64',
                ),
                'MultiSigSignerAdded': (
                    '[u8; 32]',
                    'AccountId',
                    'scale_info::95',
                ),
                'MultiSigSignerAuthorized': (
                    '[u8; 32]',
                    'AccountId',
                    'scale_info::95',
                ),
                'MultiSigSignerRemoved': (
                    '[u8; 32]',
                    'AccountId',
                    'scale_info::95',
                ),
                'ProposalAdded': ('[u8; 32]', 'AccountId', 'u64'),
                'ProposalApproved': (
                    '[u8; 32]',
                    'AccountId',
                    'scale_info::95',
                    'u64',
                ),
                'ProposalExecuted': ('[u8; 32]', 'AccountId', 'u64', 'bool'),
                'ProposalExecutionFailed': {
                    'Arithmetic': 'scale_info::27',
                    'BadOrigin': None,
                    'CannotLookup': None,
                    'ConsumerRemaining': None,
                    'Corruption': None,
                    'Exhausted': None,
                    'Module': 'scale_info::25',
                    'NoProviders': None,
                    'Other': None,
                    'Token': 'scale_info::26',
                    'TooManyConsumers': None,
                    'Transactional': 'scale_info::28',
                    'Unavailable': None,
                },
                'ProposalRejected': ('[u8; 32]', 'AccountId', 'u64'),
                'ProposalRejectionVote': (
                    '[u8; 32]',
                    'AccountId',
                    'scale_info::95',
                    'u64',
                ),
                'SchedulingFailed': {
                    'Arithmetic': 'scale_info::27',
                    'BadOrigin': None,
                    'CannotLookup': None,
                    'ConsumerRemaining': None,
                    'Corruption': None,
                    'Exhausted': None,
                    'Module': 'scale_info::25',
                    'NoProviders': None,
                    'Other': None,
                    'Token': 'scale_info::26',
                    'TooManyConsumers': None,
                    'Transactional': 'scale_info::28',
                    'Unavailable': None,
                },
            },
            'Nft': {
                'NFTPortfolioUpdated': (
                    '[u8; 32]',
                    'scale_info::236',
                    (None, 'scale_info::56'),
                    (None, 'scale_info::56'),
                    'scale_info::160',
                ),
                'NftCollectionCreated': ('[u8; 32]', '[u8; 12]', 'u64'),
            },
            'Offences': {'Offence': {'kind': '[u8; 16]', 'timeslot': 'Bytes'}},
            'Pips': {
                'ActivePipLimitChanged': ('[u8; 32]', 'u32', 'u32'),
                'DefaultEnactmentPeriodChanged': ('[u8; 32]', 'u32', 'u32'),
                'ExecutionCancellingFailed': 'u32',
                'ExecutionScheduled': ('[u8; 32]', 'u32', 'u32'),
                'ExecutionSchedulingFailed': ('[u8; 32]', 'u32', 'u32'),
                'ExpiryScheduled': ('[u8; 32]', 'u32', 'u32'),
                'ExpirySchedulingFailed': ('[u8; 32]', 'u32', 'u32'),
                'HistoricalPipsPruned': ('[u8; 32]', 'bool', 'bool'),
                'MaxPipSkipCountChanged': ('[u8; 32]', 'u8', 'u8'),
                'MinimumProposalDepositChanged': ('[u8; 32]', 'u128', 'u128'),
                'PendingPipExpiryChanged': (
                    '[u8; 32]',
                    'scale_info::82',
                    'scale_info::82',
                ),
                'PipClosed': ('[u8; 32]', 'u32', 'bool'),
                'PipSkipped': ('[u8; 32]', 'u32', 'u8'),
                'ProposalCreated': (
                    '[u8; 32]',
                    'scale_info::216',
                    'u32',
                    'u128',
                    (None, 'Bytes'),
                    (None, 'Bytes'),
                    'scale_info::82',
                    'scale_info::221',
                ),
                'ProposalRefund': ('[u8; 32]', 'u32', 'u128'),
                'ProposalStateUpdated': ('[u8; 32]', 'u32', 'scale_info::222'),
                'SnapshotCleared': ('[u8; 32]', 'u32'),
                'SnapshotResultsEnacted': (
                    '[u8; 32]',
                    (None, 'u32'),
                    [('u32', 'u8')],
                    ['u32'],
                    ['u32'],
                ),
                'SnapshotTaken': ('[u8; 32]', 'u32', ['scale_info::225']),
                'Voted': ('[u8; 32]', 'AccountId', 'u32', 'bool', 'u128'),
            },
            'PolymeshCommittee': {
                'Approved': (
                    '[u8; 32]',
                    'scale_info::11',
                    'u32',
                    'u32',
                    'u32',
                ),
                'Executed': ('[u8; 32]', 'scale_info::11', 'scale_info::80'),
                'ExpiresAfterUpdated': ('[u8; 32]', 'scale_info::82'),
                'FinalVotes': (
                    '[u8; 32]',
                    'u32',
                    'scale_info::11',
                    ['[u8; 32]'],
                    ['[u8; 32]'],
                ),
                'Proposed': ('[u8; 32]', 'u32', 'scale_info::11'),
                'Rejected': (
                    '[u8; 32]',
                    'scale_info::11',
                    'u32',
                    'u32',
                    'u32',
                ),
                'ReleaseCoordinatorUpdated': ('[u8; 32]', (None, '[u8; 32]')),
                'VoteRetracted': ('[u8; 32]', 'u32', 'scale_info::11', 'bool'),
                'VoteThresholdUpdated': ('[u8; 32]', 'u32', 'u32'),
                'Voted': (
                    '[u8; 32]',
                    'u32',
                    'scale_info::11',
                    'bool',
                    'u32',
                    'u32',
                    'u32',
                ),
            },
            'PolymeshContracts': {
                'ApiHashUpdated': (
                    'scale_info::290',
                    'scale_info::291',
                    'scale_info::11',
                ),
                'SCRuntimeCall': ('AccountId', ('u8', 'u8')),
            },
            'Portfolio': {
                'FundsMovedBetweenPortfolios': (
                    '[u8; 32]',
                    'scale_info::56',
                    'scale_info::56',
                    'scale_info::235',
                    (None, '[u8; 32]'),
                ),
                'PortfolioCreated': ('[u8; 32]', 'u64', 'Bytes'),
                'PortfolioCustodianChanged': (
                    '[u8; 32]',
                    'scale_info::56',
                    '[u8; 32]',
                ),
                'PortfolioDeleted': ('[u8; 32]', 'u64'),
                'PortfolioRenamed': ('[u8; 32]', 'u64', 'Bytes'),
                'PreApprovedPortfolio': (
                    '[u8; 32]',
                    'scale_info::56',
                    '[u8; 12]',
                ),
                'RevokePreApprovedPortfolio': (
                    '[u8; 32]',
                    'scale_info::56',
                    '[u8; 12]',
                ),
                'UserPortfolios': ('[u8; 32]', [('u64', 'Bytes')]),
            },
            'Preimage': {
                'Cleared': {'hash': 'scale_info::11'},
                'Noted': {'hash': 'scale_info::11'},
                'Requested': {'hash': 'scale_info::11'},
            },
            'ProtocolFee': {
                'CoefficientSet': ('[u8; 32]', ('u32', 'u32')),
                'FeeCharged': ('AccountId', 'u128'),
                'FeeSet': ('[u8; 32]', 'u128'),
            },
            'Relayer': {
                'AcceptedPayingKey': ('[u8; 32]', 'AccountId', 'AccountId'),
                'AuthorizedPayingKey': (
                    '[u8; 32]',
                    'AccountId',
                    'AccountId',
                    'u128',
                    'u64',
                ),
                'RemovedPayingKey': ('[u8; 32]', 'AccountId', 'AccountId'),
                'UpdatedPolyxLimit': (
                    '[u8; 32]',
                    'AccountId',
                    'AccountId',
                    'u128',
                    'u128',
                ),
            },
            'Scheduler': {
                'CallUnavailable': {
                    'id': (None, '[u8; 32]'),
                    'task': ('u32', 'u32'),
                },
                'Canceled': {'index': 'u32', 'when': 'u32'},
                'Dispatched': {
                    'id': (None, '[u8; 32]'),
                    'result': 'scale_info::80',
                    'task': ('u32', 'u32'),
                },
                'PeriodicFailed': {
                    'id': (None, '[u8; 32]'),
                    'task': ('u32', 'u32'),
                },
                'PermanentlyOverweight': {
                    'id': (None, '[u8; 32]'),
                    'task': ('u32', 'u32'),
                },
                'Scheduled': {'index': 'u32', 'when': 'u32'},
            },
            'Session': {'NewSession': {'session_index': 'u32'}},
            'Settlement': {
                'AffirmationWithdrawn': ('[u8; 32]', 'scale_info::56', 'u64'),
                'FailedToExecuteInstruction': ('u64', 'scale_info::24'),
                'InstructionAffirmed': ('[u8; 32]', 'scale_info::56', 'u64'),
                'InstructionAutomaticallyAffirmed': (
                    '[u8; 32]',
                    'scale_info::56',
                    'u64',
                ),
                'InstructionCreated': (
                    '[u8; 32]',
                    'u64',
                    'u64',
                    'scale_info::252',
                    (None, 'u64'),
                    (None, 'u64'),
                    ['scale_info::254'],
                    (None, '[u8; 32]'),
                ),
                'InstructionExecuted': ('[u8; 32]', 'u64'),
                'InstructionFailed': ('[u8; 32]', 'u64'),
                'InstructionRejected': ('[u8; 32]', 'u64'),
                'InstructionRescheduled': ('[u8; 32]', 'u64'),
                'LegFailedExecution': ('[u8; 32]', 'u64', 'u64'),
                'ReceiptClaimed': (
                    '[u8; 32]',
                    'u64',
                    'u64',
                    'u64',
                    'AccountId',
                    (None, '[u8; 32]'),
                ),
                'SchedulingFailed': {
                    'Arithmetic': 'scale_info::27',
                    'BadOrigin': None,
                    'CannotLookup': None,
                    'ConsumerRemaining': None,
                    'Corruption': None,
                    'Exhausted': None,
                    'Module': 'scale_info::25',
                    'NoProviders': None,
                    'Other': None,
                    'Token': 'scale_info::26',
                    'TooManyConsumers': None,
                    'Transactional': 'scale_info::28',
                    'Unavailable': None,
                },
                'SettlementManuallyExecuted': ('[u8; 32]', 'u64'),
                'VenueCreated': (
                    '[u8; 32]',
                    'u64',
                    'Bytes',
                    'scale_info::247',
                ),
                'VenueDetailsUpdated': ('[u8; 32]', 'u64', 'Bytes'),
                'VenueFiltering': ('[u8; 32]', '[u8; 12]', 'bool'),
                'VenueSignersUpdated': ('[u8; 32]', 'u64', ['AccountId'], 'bool'),
                'VenueTypeUpdated': ('[u8; 32]', 'u64', 'scale_info::247'),
                'VenueUnauthorized': ('[u8; 32]', '[u8; 12]', 'u64'),
                'VenuesAllowed': ('[u8; 32]', '[u8; 12]', ['u64']),
                'VenuesBlocked': ('[u8; 32]', '[u8; 12]', ['u64']),
            },
            'Staking': {
                'Bonded': ('[u8; 32]', 'AccountId', 'u128'),
                'CommissionCapUpdated': ('[u8; 32]', 'u32', 'u32'),
                'EraPayout': ('u32', 'u128', 'u128'),
                'InvalidatedNominators': (
                    '[u8; 32]',
                    'AccountId',
                    ['AccountId'],
                ),
                'MinimumBondThresholdUpdated': ((None, '[u8; 32]'), 'u128'),
                'Nominated': ('[u8; 32]', 'AccountId', ['AccountId']),
                'OldSlashingReportDiscarded': 'u32',
                'PermissionedIdentityAdded': ('[u8; 32]', '[u8; 32]'),
                'PermissionedIdentityRemoved': ('[u8; 32]', '[u8; 32]'),
                'Reward': ('[u8; 32]', 'AccountId', 'u128'),
                'RewardPaymentSchedulingInterrupted': (
                    'AccountId',
                    'u32',
                    'scale_info::24',
                ),
                'Slash': ('AccountId', 'u128'),
                'SlashingAllowedForChanged': (
                    'Validator',
                    'ValidatorAndNominator',
                    'None',
                ),
                'SolutionStored': ('OnChain', 'Signed', 'Unsigned'),
                'StakingElection': ('OnChain', 'Signed', 'Unsigned'),
                'Unbonded': ('[u8; 32]', 'AccountId', 'u128'),
                'Withdrawn': ('AccountId', 'u128'),
            },
            'Statistics': {
                'AssetStatsUpdated': (
                    '[u8; 32]',
                    'scale_info::256',
                    'scale_info::258',
                    ['scale_info::263'],
                ),
                'SetAssetTransferCompliance': (
                    '[u8; 32]',
                    'scale_info::256',
                    ['scale_info::269'],
                ),
                'StatTypesAdded': (
                    '[u8; 32]',
                    'scale_info::256',
                    ['scale_info::258'],
                ),
                'StatTypesRemoved': (
                    '[u8; 32]',
                    'scale_info::256',
                    ['scale_info::258'],
                ),
                'TransferConditionExemptionsAdded': (
                    '[u8; 32]',
                    'scale_info::270',
                    ['[u8; 32]'],
                ),
                'TransferConditionExemptionsRemoved': (
                    '[u8; 32]',
                    'scale_info::270',
                    ['[u8; 32]'],
                ),
            },
            'Sto': {
                'FundraiserClosed': ('[u8; 32]', 'u64'),
                'FundraiserCreated': (
                    '[u8; 32]',
                    'u64',
                    'Bytes',
                    'scale_info::275',
                ),
                'FundraiserFrozen': ('[u8; 32]', 'u64'),
                'FundraiserUnfrozen': ('[u8; 32]', 'u64'),
                'FundraiserWindowModified': (
                    '[u8; 32]',
                    'u64',
                    'u64',
                    (None, 'u64'),
                    'u64',
                    (None, 'u64'),
                ),
                'Invested': (
                    '[u8; 32]',
                    'u64',
                    '[u8; 12]',
                    '[u8; 12]',
                    'u128',
                    'u128',
                ),
            },
            'TechnicalCommittee': {
                'Approved': (
                    '[u8; 32]',
                    'scale_info::11',
                    'u32',
                    'u32',
                    'u32',
                ),
                'Executed': ('[u8; 32]', 'scale_info::11', 'scale_info::80'),
                'ExpiresAfterUpdated': ('[u8; 32]', 'scale_info::82'),
                'FinalVotes': (
                    '[u8; 32]',
                    'u32',
                    'scale_info::11',
                    ['[u8; 32]'],
                    ['[u8; 32]'],
                ),
                'Proposed': ('[u8; 32]', 'u32', 'scale_info::11'),
                'Rejected': (
                    '[u8; 32]',
                    'scale_info::11',
                    'u32',
                    'u32',
                    'u32',
                ),
                'ReleaseCoordinatorUpdated': ('[u8; 32]', (None, '[u8; 32]')),
                'VoteRetracted': ('[u8; 32]', 'u32', 'scale_info::11', 'bool'),
                'VoteThresholdUpdated': ('[u8; 32]', 'u32', 'u32'),
                'Voted': (
                    '[u8; 32]',
                    'u32',
                    'scale_info::11',
                    'bool',
                    'u32',
                    'u32',
                    'u32',
                ),
            },
            'TechnicalCommitteeMembership': {
                'ActiveLimitChanged': ('[u8; 32]', 'u32', 'u32'),
                'Dummy': None,
                'MemberAdded': ('[u8; 32]', '[u8; 32]'),
                'MemberRemoved': ('[u8; 32]', '[u8; 32]'),
                'MemberRevoked': ('[u8; 32]', '[u8; 32]'),
                'MembersReset': ('[u8; 32]', ['[u8; 32]']),
                'MembersSwapped': ('[u8; 32]', '[u8; 32]', '[u8; 32]'),
            },
            'TransactionPayment': {
                'TransactionFeePaid': {
                    'actual_fee': 'u128',
                    'tip': 'u128',
                    'who': 'AccountId',
                },
            },
            'Treasury': {
                'TreasuryDisbursement': (
                    '[u8; 32]',
                    '[u8; 32]',
                    'AccountId',
                    'u128',
                ),
                'TreasuryDisbursementFailed': (
                    '[u8; 32]',
                    '[u8; 32]',
                    'AccountId',
                    'u128',
                ),
                'TreasuryReimbursement': ('[u8; 32]', 'u128'),
            },
            'UpgradeCommittee': {
                'Approved': (
                    '[u8; 32]',
                    'scale_info::11',
                    'u32',
                    'u32',
                    'u32',
                ),
                'Executed': ('[u8; 32]', 'scale_info::11', 'scale_info::80'),
                'ExpiresAfterUpdated': ('[u8; 32]', 'scale_info::82'),
                'FinalVotes': (
                    '[u8; 32]',
                    'u32',
                    'scale_info::11',
                    ['[u8; 32]'],
                    ['[u8; 32]'],
                ),
                'Proposed': ('[u8; 32]', 'u32', 'scale_info::11'),
                'Rejected': (
                    '[u8; 32]',
                    'scale_info::11',
                    'u32',
                    'u32',
                    'u32',
                ),
                'ReleaseCoordinatorUpdated': ('[u8; 32]', (None, '[u8; 32]')),
                'VoteRetracted': ('[u8; 32]', 'u32', 'scale_info::11', 'bool'),
                'VoteThresholdUpdated': ('[u8; 32]', 'u32', 'u32'),
                'Voted': (
                    '[u8; 32]',
                    'u32',
                    'scale_info::11',
                    'bool',
                    'u32',
                    'u32',
                    'u32',
                ),
            },
            'UpgradeCommitteeMembership': {
                'ActiveLimitChanged': ('[u8; 32]', 'u32', 'u32'),
                'Dummy': None,
                'MemberAdded': ('[u8; 32]', '[u8; 32]'),
                'MemberRemoved': ('[u8; 32]', '[u8; 32]'),
                'MemberRevoked': ('[u8; 32]', '[u8; 32]'),
                'MembersReset': ('[u8; 32]', ['[u8; 32]']),
                'MembersSwapped': ('[u8; 32]', '[u8; 32]', '[u8; 32]'),
            },
            'Utility': {
                'BatchCompleted': None,
                'BatchCompletedOld': ['u32'],
                'BatchCompletedWithErrors': None,
                'BatchInterrupted': {
                    'error': 'scale_info::24',
                    'index': 'u32',
                },
                'BatchInterruptedOld': (['u32'], ('u32', 'scale_info::24')),
                'BatchOptimisticFailed': (['u32'], [('u32', 'scale_info::24')]),
                'DispatchedAs': {'result': 'scale_info::80'},
                'ItemCompleted': None,
                'ItemFailed': {'error': 'scale_info::24'},
                'RelayedTx': {
                    'caller_did': '[u8; 32]',
                    'result': 'scale_info::80',
                    'target': 'AccountId',
                },
            },
        },
        'phase': {
            'ApplyExtrinsic': 'u32',
            'Finalization': None,
            'Initialization': None,
        },
        'topics': ['scale_info::11'],
    },
]
```
---------
### ExecutionPhase
 The execution phase of the block.

#### Python
```python
result = substrate.query(
    'System', 'ExecutionPhase', []
)
```

#### Return value
```python
{'ApplyExtrinsic': 'u32', 'Finalization': None, 'Initialization': None}
```
---------
### ExtrinsicCount
 Total extrinsics count for the current block.

#### Python
```python
result = substrate.query(
    'System', 'ExtrinsicCount', []
)
```

#### Return value
```python
'u32'
```
---------
### ExtrinsicData
 Extrinsics data for the current block (maps an extrinsic&#x27;s index to its data).

#### Python
```python
result = substrate.query(
    'System', 'ExtrinsicData', ['u32']
)
```

#### Return value
```python
'Bytes'
```
---------
### LastRuntimeUpgrade
 Stores the `spec_version` and `spec_name` of when the last runtime upgrade happened.

#### Python
```python
result = substrate.query(
    'System', 'LastRuntimeUpgrade', []
)
```

#### Return value
```python
{'spec_name': 'Str', 'spec_version': 'u32'}
```
---------
### Number
 The current block number being processed. Set by `execute_block`.

#### Python
```python
result = substrate.query(
    'System', 'Number', []
)
```

#### Return value
```python
'u32'
```
---------
### ParentHash
 Hash of the previous block.

#### Python
```python
result = substrate.query(
    'System', 'ParentHash', []
)
```

#### Return value
```python
'scale_info::11'
```
---------
### UpgradedToTripleRefCount
 True if we have upgraded so that AccountInfo contains three types of `RefCount`. False
 (default) if not.

#### Python
```python
result = substrate.query(
    'System', 'UpgradedToTripleRefCount', []
)
```

#### Return value
```python
'bool'
```
---------
### UpgradedToU32RefCount
 True if we have upgraded so that `type RefCount` is `u32`. False (default) if not.

#### Python
```python
result = substrate.query(
    'System', 'UpgradedToU32RefCount', []
)
```

#### Return value
```python
'bool'
```
---------
## Constants

---------
### BlockHashCount
 Maximum number of block number to block hash mappings to keep (oldest pruned first).
#### Value
```python
4096
```
#### Python
```python
constant = substrate.get_constant('System', 'BlockHashCount')
```
---------
### BlockLength
 The maximum length of a block (in bytes).
#### Value
```python
{'max': {'mandatory': 10485760, 'normal': 7864320, 'operational': 10485760}}
```
#### Python
```python
constant = substrate.get_constant('System', 'BlockLength')
```
---------
### BlockWeights
 Block &amp; extrinsics weights: base values and limits.
#### Value
```python
{
    'base_block': {'proof_size': 0, 'ref_time': 20000000000},
    'max_block': {
        'proof_size': 18446744073709551615,
        'ref_time': 2000000000000,
    },
    'per_class': {
        'mandatory': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 650000000},
            'max_extrinsic': None,
            'max_total': None,
            'reserved': None,
        },
        'normal': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 650000000},
            'max_extrinsic': {
                'proof_size': 11990383647911208550,
                'ref_time': 1299350000000,
            },
            'max_total': {
                'proof_size': 13835058055282163711,
                'ref_time': 1500000000000,
            },
            'reserved': {'proof_size': 0, 'ref_time': 0},
        },
        'operational': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 650000000},
            'max_extrinsic': {
                'proof_size': 16602069666338596454,
                'ref_time': 1799350000000,
            },
            'max_total': {
                'proof_size': 18446744073709551615,
                'ref_time': 2000000000000,
            },
            'reserved': {
                'proof_size': 4611686018427387904,
                'ref_time': 500000000000,
            },
        },
    },
}
```
#### Python
```python
constant = substrate.get_constant('System', 'BlockWeights')
```
---------
### DbWeight
 The weight of runtime database operations the runtime can invoke.
#### Value
```python
{'read': 50000000, 'write': 200000000}
```
#### Python
```python
constant = substrate.get_constant('System', 'DbWeight')
```
---------
### SS58Prefix
 The designated SS58 prefix of this chain.

 This replaces the &quot;ss58Format&quot; property declared in the chain spec. Reason is
 that the runtime should know about the prefix in order to make use of it as
 an identifier of the chain.
#### Value
```python
12
```
#### Python
```python
constant = substrate.get_constant('System', 'SS58Prefix')
```
---------
### Version
 Get the chain&#x27;s current version.
#### Value
```python
{
    'apis': [
        ('0xdf6acb689907609b', 4),
        ('0x37e397fc7c91f5e4', 1),
        ('0x40fe3ad401f8959a', 6),
        ('0xd2bc9897eed08f15', 3),
        ('0xf78b278be53f454c', 2),
        ('0xed99c5acb25eedf5', 3),
        ('0xcbca25e39f142387', 2),
        ('0x687ad44ad37f03c2', 1),
        ('0xbc9d89904f5b923f', 1),
        ('0x68b66ba122c93fa7', 2),
        ('0x37c8bb1350a9a2a8', 2),
        ('0xf3ff14d5ab527059', 2),
        ('0xab3c0572291feb8b', 1),
        ('0x18ef58a3b67ba770', 1),
        ('0x329342994773047f', 1),
        ('0x001a0b29f17d01f4', 1),
        ('0xf28e8080b6e2dfd0', 3),
        ('0xbb6ba9053c5c9d78', 3),
        ('0x595ac34c5ea1f5fe', 1),
        ('0x9ea061a615cee2fe', 1),
        ('0x53df5001418f3b46', 1),
    ],
    'authoring_version': 1,
    'impl_name': 'polymesh_mainnet',
    'impl_version': 0,
    'spec_name': 'polymesh_mainnet',
    'spec_version': 6001031,
    'state_version': 1,
    'transaction_version': 4,
}
```
#### Python
```python
constant = substrate.get_constant('System', 'Version')
```
---------
## Errors

---------
### CallFiltered
The origin filter prevent the call to be dispatched.

---------
### FailedToExtractRuntimeVersion
Failed to extract the runtime version from the new runtime.

Either calling `Core_version` or decoding `RuntimeVersion` failed.

---------
### InvalidSpecName
The name of specification does not match between the current runtime
and the new runtime.

---------
### NonDefaultComposite
Suicide called when the account has non-default composite data.

---------
### NonZeroRefCount
There is a non-zero reference count preventing the account from being purged.

---------
### SpecVersionNeedsToIncrease
The specification version is not allowed to decrease between the current runtime
and the new runtime.

---------
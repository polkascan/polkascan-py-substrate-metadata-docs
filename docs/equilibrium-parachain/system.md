
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
| dispatch_error | `DispatchError` | ```{'Other': None, 'CannotLookup': None, 'BadOrigin': None, 'Module': {'index': 'u8', 'error': '[u8; 4]'}, 'ConsumerRemaining': None, 'NoProviders': None, 'TooManyConsumers': None, 'Token': ('FundsUnavailable', 'OnlyProvider', 'BelowMinimum', 'CannotCreate', 'UnknownAsset', 'Frozen', 'Unsupported', 'CannotCreateHold', 'NotExpendable'), 'Arithmetic': ('Underflow', 'Overflow', 'DivisionByZero'), 'Transactional': ('LimitReached', 'NoLayer'), 'Exhausted': None, 'Corruption': None, 'Unavailable': None}```
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
| hash | `T::Hash` | ```scale_info::16```

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
    'data': {'V0': {'balance': [('u64', 'scale_info::10')], 'lock': 'u128'}},
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
'scale_info::16'
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
            'Consensus': ('[u8; 4]', 'Bytes'),
            'Other': 'Bytes',
            None: None,
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
    'System', 'EventTopics', ['scale_info::16']
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
            'Bailsman': {'UnregisteredBailsman': 'AccountId'},
            'ChainBridge': {
                'ChainToggled': ('u8', 'bool'),
                'ChainWhitelisted': 'u8',
                'FeeChanged': ('u8', 'u128'),
                'FungibleTransfer': (
                    'u8',
                    'u64',
                    '[u8; 32]',
                    'scale_info::72',
                    'Bytes',
                ),
                'GenericTransfer': ('u8', 'u64', '[u8; 32]', 'Bytes'),
                'NonFungibleTransfer': (
                    'u8',
                    'u64',
                    '[u8; 32]',
                    'Bytes',
                    'Bytes',
                    'Bytes',
                ),
                'ProposalApproved': ('u8', 'u64'),
                'ProposalFailed': ('u8', 'u64'),
                'ProposalLifetimeChanged': 'u32',
                'ProposalRejected': ('u8', 'u64'),
                'ProposalSucceeded': ('u8', 'u64'),
                'RelayerAdded': 'AccountId',
                'RelayerRemoved': 'AccountId',
                'RelayerThresholdChanged': 'u32',
                'VoteAgainst': ('u8', 'u64', 'AccountId'),
                'VoteFor': ('u8', 'u64', 'AccountId'),
            },
            'Claims': {'Claimed': ('AccountId', '[u8; 20]', 'u128')},
            'Council': {
                'Approved': {'proposal_hash': 'scale_info::16'},
                'Closed': {
                    'no': 'u32',
                    'proposal_hash': 'scale_info::16',
                    'yes': 'u32',
                },
                'Disapproved': {'proposal_hash': 'scale_info::16'},
                'Executed': {
                    'proposal_hash': 'scale_info::16',
                    'result': 'scale_info::37',
                },
                'MemberExecuted': {
                    'proposal_hash': 'scale_info::16',
                    'result': 'scale_info::37',
                },
                'Proposed': {
                    'account': 'AccountId',
                    'proposal_hash': 'scale_info::16',
                    'proposal_index': 'u32',
                    'threshold': 'u32',
                },
                'Voted': {
                    'account': 'AccountId',
                    'no': 'u32',
                    'proposal_hash': 'scale_info::16',
                    'voted': 'bool',
                    'yes': 'u32',
                },
            },
            'CouncilMembership': (
                'MemberAdded',
                'MemberRemoved',
                'MembersSwapped',
                'MembersReset',
                'KeyChanged',
                'Dummy',
            ),
            'CurveAmm': {
                'AddLiquidity': (
                    'AccountId',
                    'u32',
                    ['u128'],
                    ['u128'],
                    'u128',
                    'u128',
                    'u128',
                ),
                'CreatePool': ('AccountId', 'u32'),
                'PoolEnableStateChanged': ('u32', 'bool'),
                'RemoveLiquidity': (
                    'AccountId',
                    'u32',
                    ['u128'],
                    ['u128'],
                    'u128',
                    'u128',
                ),
                'RemoveLiquidityImbalance': (
                    'AccountId',
                    'u32',
                    ['u128'],
                    ['u128'],
                    'u128',
                    'u128',
                    'u128',
                ),
                'RemoveLiquidityOne': (
                    'AccountId',
                    'u32',
                    'u128',
                    'u32',
                    'u128',
                    'u128',
                    'u128',
                ),
                'TokenExchange': (
                    'AccountId',
                    'u32',
                    'u32',
                    'u128',
                    'u32',
                    'u128',
                    'u128',
                ),
                'WithdrawAdminFees': ('AccountId', 'u32', ['u128']),
            },
            'Democracy': {
                'Blacklisted': {'proposal_hash': 'scale_info::16'},
                'Cancelled': {'ref_index': 'u32'},
                'Delegated': {'target': 'AccountId', 'who': 'AccountId'},
                'ExternalTabled': None,
                'MetadataCleared': {
                    'hash': 'scale_info::16',
                    'owner': 'scale_info::156',
                },
                'MetadataSet': {
                    'hash': 'scale_info::16',
                    'owner': 'scale_info::156',
                },
                'MetadataTransferred': {
                    'hash': 'scale_info::16',
                    'owner': 'scale_info::156',
                    'prev_owner': 'scale_info::156',
                },
                'NotPassed': {'ref_index': 'u32'},
                'Passed': {'ref_index': 'u32'},
                'ProposalCanceled': {'prop_index': 'u32'},
                'Proposed': {'deposit': 'u128', 'proposal_index': 'u32'},
                'Seconded': {'prop_index': 'u32', 'seconder': 'AccountId'},
                'Started': {
                    'ref_index': 'u32',
                    'threshold': 'scale_info::153',
                },
                'Tabled': {'deposit': 'u128', 'proposal_index': 'u32'},
                'Undelegated': {'account': 'AccountId'},
                'Vetoed': {
                    'proposal_hash': 'scale_info::16',
                    'until': 'u32',
                    'who': 'AccountId',
                },
                'Voted': {
                    'ref_index': 'u32',
                    'vote': 'scale_info::154',
                    'voter': 'AccountId',
                },
            },
            'DmpQueue': {
                'ExecutedDownward': {
                    'message_id': '[u8; 32]',
                    'outcome': 'scale_info::97',
                },
                'InvalidFormat': {'message_id': '[u8; 32]'},
                'MaxMessagesExhausted': {'message_id': '[u8; 32]'},
                'OverweightEnqueued': {
                    'message_id': '[u8; 32]',
                    'overweight_index': 'u64',
                    'required_weight': 'scale_info::14',
                },
                'OverweightServiced': {
                    'overweight_index': 'u64',
                    'weight_used': 'scale_info::14',
                },
                'UnsupportedVersion': {'message_id': '[u8; 32]'},
                'WeightExhausted': {
                    'message_id': '[u8; 32]',
                    'remaining_weight': 'scale_info::14',
                    'required_weight': 'scale_info::14',
                },
            },
            'EqAssets': {
                'DeleteAsset': ('u64', 'Bytes'),
                'NewAsset': ('u64', 'Bytes'),
                'UpdateAsset': ('u64', 'Bytes'),
            },
            'EqBalances': {
                'DeleteAccount': 'AccountId',
                'Deposit': ('AccountId', 'u64', 'u128', 'scale_info::48'),
                'Exchange': (
                    'AccountId',
                    'u64',
                    'u128',
                    'AccountId',
                    'u64',
                    'u128',
                ),
                'MigrationComplete': None,
                'Transfer': (
                    'AccountId',
                    'AccountId',
                    'u64',
                    'u128',
                    'scale_info::47',
                ),
                'Withdraw': ('AccountId', 'u64', 'u128', 'scale_info::49'),
                'XcmMessageSendError': (
                    'NotApplicable',
                    'Transport',
                    'Unroutable',
                    'DestinationUnsupported',
                    'ExceedsMaxMessageSize',
                    'MissingArgument',
                    'Fees',
                ),
                'XcmTransfer': ('scale_info::50', 'scale_info::50'),
            },
            'EqBridge': {
                'ChainAddressTypeChanged': ('u8', (None, 'scale_info::76')),
                'FromBridgeTransfer': ('AccountId', 'u64', 'u128'),
                'FromBridgeTransferNext': ('Bytes', 'u64', 'u128'),
                'MinimumTransferAmountChanged': ('u8', '[u8; 32]', 'u128'),
                'Remark': 'scale_info::16',
                'ToBridgeTransfer': ('AccountId', 'u64', 'u128'),
                'WithdrawalsToggled': ('[u8; 32]', 'u8', 'bool'),
            },
            'EqDex': {
                'Match': (
                    'u64',
                    'u128',
                    'i64',
                    'u64',
                    'AccountId',
                    'AccountId',
                    'u128',
                    'u128',
                    'u128',
                    'scale_info::83',
                ),
                'OrderCreated': (
                    'AccountId',
                    'u64',
                    'u64',
                    'u128',
                    'i64',
                    'scale_info::83',
                    'u64',
                    'u64',
                ),
                'OrderDeleted': ('AccountId', 'u64', 'u64', 'scale_info::84'),
            },
            'EqLending': {
                'Deposit': {
                    'asset': 'u64',
                    'value': 'u128',
                    'who': 'AccountId',
                },
                'Payout': {
                    'asset': 'u64',
                    'payout': 'u128',
                    'who': 'AccountId',
                },
                'Withdraw': {
                    'asset': 'u64',
                    'value': 'u128',
                    'who': 'AccountId',
                },
            },
            'EqLockdrop': {
                'Lock': ('AccountId', 'u128'),
                'Unlock': ('AccountId', 'u128'),
            },
            'EqMarginCall': {
                'MaintenanceMarginCall': (
                    'AccountId',
                    (None, ('scale_info::68', 'AccountId')),
                    'u64',
                ),
                'MarginCallExecuted': (
                    'AccountId',
                    (None, ('scale_info::68', 'AccountId')),
                ),
            },
            'EqMarketMaker': {
                'AddedToWhitelist': 'AccountId',
                'RemovedFromWhitelist': 'AccountId',
            },
            'EqMultisigSudo': {
                'Initialized': None,
                'KeyAdded': 'AccountId',
                'KeyRemoved': 'AccountId',
                'MultisigSudid': ('[u8; 32]', 'scale_info::37'),
                'NewProposal': ('AccountId', '[u8; 32]'),
                'ProposalApproved': ('AccountId', '[u8; 32]'),
                'ProposalCancelled': '[u8; 32]',
                'SudoFailed': '[u8; 32]',
                'ThresholdModified': 'u32',
            },
            'EqSessionManager': {
                'ValidatorAdded': 'AccountId',
                'ValidatorRemoved': 'AccountId',
            },
            'Financial': {
                'AssetMetricsRecalculated': 'u64',
                'MetricsRecalculated': None,
                'PortfolioMetricsRecalculated': 'AccountId',
            },
            'Migration': {
                'Migrated': None,
                'MigrationProcessed': 'u16',
                'MigrationSetted': 'u16',
            },
            'Multisig': {
                'MultisigApproval': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                    'timepoint': 'scale_info::88',
                },
                'MultisigCancelled': {
                    'call_hash': '[u8; 32]',
                    'cancelling': 'AccountId',
                    'multisig': 'AccountId',
                    'timepoint': 'scale_info::88',
                },
                'MultisigExecuted': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                    'result': 'scale_info::37',
                    'timepoint': 'scale_info::88',
                },
                'NewMultisig': {
                    'approving': 'AccountId',
                    'call_hash': '[u8; 32]',
                    'multisig': 'AccountId',
                },
            },
            'Oracle': {'NewPrice': ('u64', 'i64', 'i64', 'AccountId')},
            'ParachainSystem': {
                'DownwardMessagesProcessed': {
                    'dmq_head': 'scale_info::16',
                    'weight_used': 'scale_info::14',
                },
                'DownwardMessagesReceived': {'count': 'u32'},
                'UpgradeAuthorized': {'code_hash': 'scale_info::16'},
                'UpwardMessageSent': {'message_hash': (None, '[u8; 32]')},
                'ValidationFunctionApplied': {'relay_chain_block_num': 'u32'},
                'ValidationFunctionDiscarded': None,
                'ValidationFunctionStored': None,
            },
            'PolkadotXcm': {
                'AssetsClaimed': (
                    'scale_info::16',
                    'scale_info::50',
                    'scale_info::127',
                ),
                'AssetsTrapped': (
                    'scale_info::16',
                    'scale_info::50',
                    'scale_info::127',
                ),
                'Attempted': {
                    'Complete': 'scale_info::14',
                    'Error': 'scale_info::98',
                    'Incomplete': ('scale_info::14', 'scale_info::98'),
                },
                'FeesPaid': ('scale_info::50', ['scale_info::104']),
                'InvalidQuerier': (
                    'scale_info::50',
                    'u64',
                    'scale_info::50',
                    (None, 'scale_info::50'),
                ),
                'InvalidQuerierVersion': ('scale_info::50', 'u64'),
                'InvalidResponder': (
                    'scale_info::50',
                    'u64',
                    (None, 'scale_info::50'),
                ),
                'InvalidResponderVersion': ('scale_info::50', 'u64'),
                'Notified': ('u64', 'u8', 'u8'),
                'NotifyDecodeFailed': ('u64', 'u8', 'u8'),
                'NotifyDispatchError': ('u64', 'u8', 'u8'),
                'NotifyOverweight': (
                    'u64',
                    'u8',
                    'u8',
                    'scale_info::14',
                    'scale_info::14',
                ),
                'NotifyTargetMigrationFail': ('scale_info::141', 'u64'),
                'NotifyTargetSendFail': (
                    'scale_info::50',
                    'u64',
                    'scale_info::98',
                ),
                'ResponseReady': ('u64', 'scale_info::110'),
                'ResponseTaken': 'u64',
                'Sent': (
                    'scale_info::50',
                    'scale_info::50',
                    ['scale_info::101'],
                ),
                'SupportedVersionChanged': ('scale_info::50', 'u32'),
                'UnexpectedResponse': ('scale_info::50', 'u64'),
                'VersionChangeNotified': (
                    'scale_info::50',
                    'u32',
                    ['scale_info::104'],
                ),
                'VersionNotifyRequested': (
                    'scale_info::50',
                    ['scale_info::104'],
                ),
                'VersionNotifyStarted': ('scale_info::50', ['scale_info::104']),
                'VersionNotifyUnrequested': (
                    'scale_info::50',
                    ['scale_info::104'],
                ),
            },
            'Preimage': {
                'Cleared': {'hash': 'scale_info::16'},
                'Noted': {'hash': 'scale_info::16'},
                'Requested': {'hash': 'scale_info::16'},
            },
            'Proxy': {
                'Announced': {
                    'call_hash': 'scale_info::16',
                    'proxy': 'AccountId',
                    'real': 'AccountId',
                },
                'ProxyAdded': {
                    'delay': 'u32',
                    'delegatee': 'AccountId',
                    'delegator': 'AccountId',
                    'proxy_type': 'scale_info::90',
                },
                'ProxyExecuted': {'result': 'scale_info::37'},
                'ProxyRemoved': {
                    'delay': 'u32',
                    'delegatee': 'AccountId',
                    'delegator': 'AccountId',
                    'proxy_type': 'scale_info::90',
                },
                'PureCreated': {
                    'disambiguation_index': 'u16',
                    'proxy_type': 'scale_info::90',
                    'pure': 'AccountId',
                    'who': 'AccountId',
                },
            },
            'QSwap': {
                'QSwap': ('AccountId', 'u128', 'u128', 'u128', 'u128', 'u128'),
            },
            'Scheduler': {
                'CallUnavailable': {
                    'id': (None, '[u8; 32]'),
                    'task': ('u32', 'u32'),
                },
                'Canceled': {'index': 'u32', 'when': 'u32'},
                'Dispatched': {
                    'id': (None, '[u8; 32]'),
                    'result': 'scale_info::37',
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
            'Subaccounts': {
                'RegisterBailsman': ('AccountId', 'AccountId'),
                'SubaccountCreated': (
                    'AccountId',
                    'AccountId',
                    'scale_info::68',
                ),
            },
            'System': {
                'CodeUpdated': None,
                'ExtrinsicFailed': {
                    'dispatch_error': 'scale_info::29',
                    'dispatch_info': 'scale_info::26',
                },
                'ExtrinsicSuccess': {'dispatch_info': 'scale_info::26'},
                'KilledAccount': {'account': 'AccountId'},
                'NewAccount': {'account': 'AccountId'},
                'Remarked': {'hash': 'scale_info::16', 'sender': 'AccountId'},
            },
            'TechnicalCommittee': {
                'Approved': {'proposal_hash': 'scale_info::16'},
                'Closed': {
                    'no': 'u32',
                    'proposal_hash': 'scale_info::16',
                    'yes': 'u32',
                },
                'Disapproved': {'proposal_hash': 'scale_info::16'},
                'Executed': {
                    'proposal_hash': 'scale_info::16',
                    'result': 'scale_info::37',
                },
                'MemberExecuted': {
                    'proposal_hash': 'scale_info::16',
                    'result': 'scale_info::37',
                },
                'Proposed': {
                    'account': 'AccountId',
                    'proposal_hash': 'scale_info::16',
                    'proposal_index': 'u32',
                    'threshold': 'u32',
                },
                'Voted': {
                    'account': 'AccountId',
                    'no': 'u32',
                    'proposal_hash': 'scale_info::16',
                    'voted': 'bool',
                    'yes': 'u32',
                },
            },
            'TransactionPayment': {
                'TransactionFeePaid': {
                    'actual_fee': 'u128',
                    'tip': 'u128',
                    'who': 'AccountId',
                },
            },
            'Treasury': {
                'Buyout': {
                    'asset': 'u64',
                    'buyout_amount': 'u128',
                    'exchange_amount': 'u128',
                    'who': 'AccountId',
                },
            },
            'Vesting': {
                'NewAccountsPerBlock': 'u32',
                'VestingCompleted': 'AccountId',
                'VestingUpdated': ('AccountId', 'u128'),
            },
            None: None,
            'TechnicalCommitteeMembership': (
                'MemberAdded',
                'MemberRemoved',
                'MembersSwapped',
                'MembersReset',
                'KeyChanged',
                'Dummy',
            ),
            'Utility': {
                'BatchCompleted': None,
                'BatchCompletedWithErrors': None,
                'BatchInterrupted': {
                    'error': 'scale_info::29',
                    'index': 'u32',
                },
                'DispatchedAs': {'result': 'scale_info::37'},
                'ItemCompleted': None,
                'ItemFailed': {'error': 'scale_info::29'},
            },
            'Vesting2': {
                'NewAccountsPerBlock': 'u32',
                'VestingCompleted': 'AccountId',
                'VestingUpdated': ('AccountId', 'u128'),
            },
            'Vesting3': {
                'NewAccountsPerBlock': 'u32',
                'VestingCompleted': 'AccountId',
                'VestingUpdated': ('AccountId', 'u128'),
            },
            'Vesting4': {
                'NewAccountsPerBlock': 'u32',
                'VestingCompleted': 'AccountId',
                'VestingUpdated': ('AccountId', 'u128'),
            },
            'Whitelists': {
                'AddedToWhitelist': 'AccountId',
                'RemovedFromWhitelist': 'AccountId',
            },
            'XcmpQueue': {
                'BadFormat': {'message_hash': (None, '[u8; 32]')},
                'BadVersion': {'message_hash': (None, '[u8; 32]')},
                'Fail': {
                    'error': 'scale_info::98',
                    'message_hash': (None, '[u8; 32]'),
                    'weight': 'scale_info::14',
                },
                'OverweightEnqueued': {
                    'index': 'u64',
                    'required': 'scale_info::14',
                    'sender': 'u32',
                    'sent_at': 'u32',
                },
                'OverweightServiced': {
                    'index': 'u64',
                    'used': 'scale_info::14',
                },
                'Success': {'message_hash': (None, '[u8; 32]'), 'weight': 'scale_info::14'},
                'XcmpMessageSent': {'message_hash': (None, '[u8; 32]')},
            },
        },
        'phase': {
            'ApplyExtrinsic': 'u32',
            'Finalization': None,
            'Initialization': None,
        },
        'topics': ['scale_info::16'],
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
'scale_info::16'
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
250
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
{'max': {'mandatory': 5242880, 'normal': 3932160, 'operational': 5242880}}
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
    'base_block': {'proof_size': 0, 'ref_time': 392184000},
    'max_block': {'proof_size': 5242880, 'ref_time': 500000000000},
    'per_class': {
        'mandatory': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 113638000},
            'max_extrinsic': None,
            'max_total': None,
            'reserved': None,
        },
        'normal': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 113638000},
            'max_extrinsic': {'proof_size': 3407872, 'ref_time': 324886362000},
            'max_total': {'proof_size': 3932160, 'ref_time': 375000000000},
            'reserved': {'proof_size': 0, 'ref_time': 0},
        },
        'operational': {
            'base_extrinsic': {'proof_size': 0, 'ref_time': 113638000},
            'max_extrinsic': {'proof_size': 4718592, 'ref_time': 449886362000},
            'max_total': {'proof_size': 5242880, 'ref_time': 500000000000},
            'reserved': {'proof_size': 1310720, 'ref_time': 125000000000},
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
{'read': 20499000, 'write': 83471000}
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
68
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
        ('0x37e397fc7c91f5e4', 2),
        ('0x40fe3ad401f8959a', 6),
        ('0xbc9d89904f5b923f', 1),
        ('0xd2bc9897eed08f15', 3),
        ('0xf78b278be53f454c', 2),
        ('0xdd718d5cc53262d4', 1),
        ('0x37c8bb1350a9a2a8', 4),
        ('0xab3c0572291feb8b', 1),
        ('0x5f79bfa4cb491750', 1),
        ('0xea93e3f16f3d6962', 2),
        ('0xeea427cf0ef4f816', 1),
        ('0x3b801a14ec2e4c67', 1),
    ],
    'authoring_version': 10,
    'impl_name': 'Equilibrium-parachain',
    'impl_version': 1,
    'spec_name': 'Equilibrium-parachain',
    'spec_version': 41,
    'state_version': 0,
    'transaction_version': 1,
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